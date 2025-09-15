# Variable Evaluation Hooks for Java SDK

This repository contains the variable evaluation hooks for the Java SDK.

## Usage

To use the hooks, you need to use the DevCycle Java SDK 2.9.1 or higher.

Then, you can use the hooks in your code, copy the DynatraceOneAgentHook.java file to your project and add it to your project.

## Add the hook to your DevCycle client

```java
    // Create DevCycle client with default options
    devCycleClient = new DevCycleLocalClient(devCycleServerSdkKey);

    // Add Dynatrace OneAgent SDK hook for all variable types
    DynatraceOneAgentHook hook = new DynatraceOneAgentHook();
    devCycleClient.addHook(hook);

```

## OpenTelemetry Configuration

The hook is using OpenTelemetry to trace the feature flag evaluation which are automatically picked up by Dynatrace OneAgent if its already configured.

If you have OpenTelemetry configured in your project, you can use the hook to trace the feature flag evaluation and they will go to your configured observability provider.

# OpenTelemetrySpanHook

Copy the OpenTelemetrySpanHook.java file into your project and include it in your build.

## Integrating the hook with your DevCycle client

```java
    // Create DevCycle client with default options
    devCycleClient = new DevCycleLocalClient(devCycleServerSdkKey);

    // Add OpenTelemetrySpanHook for all variable types
    OpenTelemetrySpanHook hook = new OpenTelemetrySpanHook();
    devCycleClient.addHook(hook);

```
