# Serilog.Sinks.Loggly

[![Build status](https://ci.appveyor.com/api/projects/status/x2ob36tl8brpkkjf/branch/master?svg=true)](https://ci.appveyor.com/project/serilog/serilog-sinks-loggly/branch/master) [![NuGet Version](http://img.shields.io/nuget/v/Serilog.Sinks.Loggly.svg?style=flat)](https://www.nuget.org/packages/Serilog.Sinks.Loggly/) 


[Loggly](http://www.loggly.com) is a cloud based log management service. Create a new input and specify that you want to use a http input with JSON enabled. Use the [loggly-csharp-configuration](https://github.com/neutmute/loggly-csharp) XML configuration syntax to configure the sink.

**Package** - [Serilog.Sinks.Loggly](http://nuget.org/packages/serilog.sinks.loggly)
| **Platforms** - .NET 4.8 and .NET Standard 2.0

```csharp
var log = new LoggerConfiguration()
    .WriteTo.Loggly()
    .CreateLogger();
```

Properties will be sent along to Loggly. The level is sent as a category.

The sink can also be configured from `appsettings.json` for .NET Standard / .NET Core applications that do not support XML configuration:

```json
{
  "Serilog": {
    "WriteTo": [
      {
        "Name": "Loggly",
        "Args": {
          "customerToken": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
          "tags": "foo,bar"
        }
      }
    ],
    "Properties": { "Application": "SampleApp" }
  }
}
```

The `customerToken` argument is required, if you use this form of configuration. The `tags` argument is comma-delimited. The `Application` property will also be sent to Loggly and should be set appropriately.