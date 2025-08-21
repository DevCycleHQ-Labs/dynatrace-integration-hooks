
# Variable Evaluation Hooks for .NET SDK

This repository contains the variable evaluation hooks for the .NET SDK.

## Usage

To use the hooks, you need to use the Local DevCycle .NET SDK 4.8.1 or higher.

Then, you can use the hooks in your code, copy the ActivityHook.cs file to your project and add it to your project.

## Add the hook to your DevCycle client

```c#
    // Create DevCycle client with default options
    DevCycleLocalClient client = new DevCycleLocalClientBuilder()
        .SetSDKKey("<DEVCYCLE_SERVER_SDK_KEY>")
        .SetLogger(LoggerFactory.Create(builder => builder.AddConsole()))
        .Build();

    // Add eval hook and pass an ActivitySource
    var hook = new ActivityHook(new ActivitySource("DevCycle.FlagEvaluations");
    client.AddEvalHook(hook);
```

## OpenTelemetry Configuration

The hook is using OpenTelemetry to trace the feature flag evaluation which are automatically picked up by Dynatrace OneAgent if its already configured.

If you have OpenTelemetry configured in your project, you can use the hook to trace the feature flag evaluation and they will go to your configured observability provider.
