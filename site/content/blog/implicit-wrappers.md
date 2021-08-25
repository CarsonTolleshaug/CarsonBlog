---
title: "Making Your Wrappers Better with Implicit Operators"
date: 2021-08-24T11:00:00-07:00
tags: ["C#", "Object-Oriented Design"]
image: images/blog/post-implicit-wrappers.jpg
feature_image: images/blog/details-implicit-wrappers.jpg
tldr: Implicit operators are cool, and you should use them in your wrapper classes.
---

First off, if you don't know what a "wrapper" class is, you're doing it wrong. But, just to make 
sure we're on the same page, I'll define it as follows:

> A "wrapper" is a class who's sole purpose is to encapsulate external functionality while providing
> an interface for dependent classes to consume. This allows the dependent classes to be more test-able,
> and simultaneously decouples internal code from external library implementation.

Clear as mud? Great. Let's get to the good part.

### Wrapper Instantiation

It's common to see wrapper classes in C# instantiated like this:

```c#
ExternalConcreteClass externalClass = new ExternalConcreteClass();
IMyWrappedInterface myVar = new MyWrappedClass(externalClass);

string result = DoStuff(myVar);
```

Here we create an instance of `MyWrappedClass` which implements the `IMyWrappedInterface` interface, but 
in order to do so we first had to create and then pass in an instance of the external concrete class which 
comes from outside our code.

Granted, instantiation is usually done in either chained constructors, or in a dependency injection 
framework, but I've made everything inline so it's more clear.

The implementation for `MyWrappedClass` would look something like this:

```c#
public class MyWrappedClass : IMyWrappedInterface
{
    private readonly ExternalConcreteClass _instance;

    public MyWrappedClass(ExternalConcreteClass instance)
    {
        _instance = instance;
    }

    public string MyWrappedMethod() => _instance.MyMethod();
}
```

### What if I told you, there's a better way?

For us C# devs, we can improve this code by using 
[implicit operators](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/user-defined-conversion-operators).
Take a look at the following change to `MyWrappedClass`:

```c#
public class MyWrappedClass : IMyWrappedInterface
{
    private readonly ExternalConcreteClass _instance;

    public MyWrappedClass(ExternalConcreteClass instance)
    {
        _instance = instance;
    }

    public string MyWrappedMethod() => _instance.MyMethod();

    public static implicit operator MyWrappedClass(ExternalConcreteClass e) => new MyWrappedClass(e);
}
```

Now we can implicitly convert any instance of `ExternalConcreteClass` to `MyWrappedClass`.

### So What?

Well, check this out. Our original code can be simplified:

```c#
ExternalConcreteClass externalClass = new ExternalConcreteClass();

string result = DoStuff(externalClass);
```

**It's like it's not even wrapped at all!** ( ͡° ͜ʖ ͡°)

Under the hood, this will implicitly cast our instance of `ExternalConcreteClass` to an instance of `MyWrappedClass` before passing it to the `DoStuff()` method. This conversion happens by calling the implicit operator declaration we gave in our class:

```c#
public static implicit operator MyWrappedClass(ExternalConcreteClass e) => new MyWrappedClass(e);
```

### Useful Example

If you work with ASP.NET, it can be extremely useful to wrap HTTP related concerns. Here's a standard controller endpoint that uses a service layer to do the actual "work" for the request:

```c#
[HttpGet]
public IActionResult Get(string input)
{
    MyModel result = _service.GetMyModel(input);

    return Ok(result);
}
```

Let's say you want your service layer to add or modify the cookies of the response. Normally you'd wrap the `Request` object like this:

```c#
[HttpGet]
public IActionResult Get(string input)
{
    IResponseWrapper responseWrapper = new ResponseWrapper(this.HttpContext.Response)

    MyModel result = _service.GetMyModel(input, responseWrapper);

    return Ok(result);
}
```

Now let's add an implicit conversion to our wrapper:

```c#
public static implicit operator ResponseWrapper(System.Web.HttpRequest request) => new ResponseWrapper(request);
```

We don't need to make any changes to our service layer at all and the controller code now becomes:

```c#
[HttpGet]
public IActionResult Get(string input)
{
    MyModel result = _service.GetMyModel(input, this.HttpContext.Response);

    return Ok(result);
}
```

By using implicit conversion in our wrapper class, we make the code cleaner and more readable without sacrificing testability or functionality of our dependent classes. The service layer can continue to depend on an interface that can easily be mocked or faked, but the controller doesn't need to worry about creating objects.

Hopefully, you can see why I think this is so cool. Have Fun!