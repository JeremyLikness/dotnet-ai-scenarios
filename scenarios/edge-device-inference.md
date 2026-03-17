---
title: Edge and Device Inference
job: I need to run AI models on edge devices or locally with low latency
category: Edge and Device AI
technologies:
  - ONNX Runtime
status: GA
repo: https://github.com/microsoft/onnxruntime/tree/main/csharp/sample/
---

# Edge and Device Inference

> Offline inference, on-device classification, low-latency embeddings, NPU acceleration

## Why ONNX Runtime

ONNX Runtime is a high-performance inference engine optimized for CPU, GPU, and NPU hardware. It runs ONNX-format models locally with no network dependency, making it ideal for scenarios where latency, privacy, or connectivity constraints rule out cloud calls. MEAI can wrap ONNX Runtime as a provider, so your application code stays provider-agnostic.

## Architecture

```
Your app → ONNX Runtime (local model) → Inference result
         (CPU / GPU / NPU — no network required)
```

## Example

A manufacturing quality-inspection app running on factory-floor tablets classifies product images in real time using an ONNX model. No cloud connectivity is needed, and inference completes in under 50ms per image.

## Code

```csharp
using Microsoft.ML.OnnxRuntime;

var session = new InferenceSession("model.onnx");
var inputs = new List<NamedOnnxValue>
{
    NamedOnnxValue.CreateFromTensor("input", inputTensor)
};
var results = session.Run(inputs);
```
