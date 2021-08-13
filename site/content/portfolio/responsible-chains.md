---
title: "Responsible Chains"
date: 2021-06-23T12:00:00-07:00
type: portfolio
image: "images/projects/responsible-chains.png"
category: ["C# Library"]
github_url: https://github.com/CarsonTolleshaug/ResponsibleChains
---

[![Build and Release](https://github.com/CarsonTolleshaug/ResponsibleChains/actions/workflows/build.yml/badge.svg)](https://github.com/CarsonTolleshaug/ResponsibleChains/actions/workflows/build.yml)
[![NuGet](https://img.shields.io/nuget/v/ResponsibleChains.svg)](https://nuget.org/packages/ResponsibleChains) 
[![NuGet](https://img.shields.io/nuget/dt/ResponsibleChains.svg)](https://nuget.org/packages/ResponsibleChains)

`ResponsibleChains` is a library for easily implementing a chain of responsibility pattern.

After installing the NuGet package, a chain of responsibility can be added to the dependency injection in startup.

Example:

```c#
public void ConfigureServices(IServiceCollection services)
{
    services.AddResponsibleChain<IMyChain>()
        .WithLink<MyFirstLink>()
        .WithLink<MySecondLink>()
        .WithLink<DefaultLink>();

    ...
}
```

See https://github.com/CarsonTolleshaug/ResponsibleChains for more info.

---

*This project is feature complete. Use github issues to suggest new features or report a bug.*