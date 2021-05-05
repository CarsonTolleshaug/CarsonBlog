---
title: "CLImber"
date: 2021-01-18T12:00:00-07:00
type: portfolio
image: "images/projects/climber.png"
category: ["C# Web App"]
github_url: https://github.com/CarsonTolleshaug/CLImber
---

[![Build](https://github.com/CarsonTolleshaug/CLImber/actions/workflows/build.yml/badge.svg)](https://github.com/CarsonTolleshaug/CLImber/actions/workflows/build.yml)

`CLImber` is a ASP.NET web application designed to be run as a configurable server, which will convert incoming REST calls into commands on a command-line interface available on the server.

A CLImber configuration looks like this:

```yaml
shell: bash
endpoints:
  - name: List Files
    route: /ls/(.*)
    method: GET
    command: ls -la $1
    responses:
    - condition:
        exitCode: 0
      responseCode: 400
      responseBody: {
        "message": "unable to process request"
      }
    - responseCode: 200
      responseBody: {
        "outputText": "{{stdout}}"
      }
```

The above config will create a server which will listen for GET requests on `/ls/{name}` and will execute the bash command `ls -la {name}`. If the command produces an exit code of `0`, the server will respond with a 400 (Bad Request) status code and the following JSON body:

```json
{
  "message": "unable to process request"
}
```

Otherwise (if the exit code is non-zero), the service will return a 200 (OK) status code and a JSON body containing an `outputText` property with the value containing whatever was written to stdout during the execution of the `ls -la {name}` command.

---

*This project is in MVP. Future feature work is possible, but not guarenteed.*