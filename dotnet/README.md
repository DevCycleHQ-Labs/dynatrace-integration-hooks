
# DevCycle Feature Flag Evaluation Hooks for .NET SDK

This repository provides evaluation hooks for the DevCycle .NET SDK that enable observability and tracing of feature flag evaluations.

## Usage

To implement these hooks, you must have the DevCycle Local .NET SDK version 4.8.1 or later installed.

Copy the DynatraceOneAgentHook.cs file into your project and include it in your build.

## Integrating the hook with your DevCycle client

```c#
    // Initialize DevCycle client with standard configuration
    DevCycleLocalClient client = new DevCycleLocalClientBuilder()
        .SetSDKKey("<DEVCYCLE_SERVER_SDK_KEY>")
        .SetLogger(LoggerFactory.Create(builder => builder.AddConsole()))
        .Build();

    // Initialize evaluation hook with an ActivitySource for tracing
    var hook = new DynatraceOneAgentHook(new ActivitySource("DevCycle.FlagEvaluations"));
    client.AddEvalHook(hook);
```

## OpenTelemetry Integration

This hook leverages OpenTelemetry to instrument feature flag evaluations, creating traces that Dynatrace OneAgent automatically collects when properly configured.

When OpenTelemetry is configured in your application, the hook will send feature flag evaluation traces to your designated observability platform.
