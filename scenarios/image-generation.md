---
title: Image Generation
job: I need to generate images from text descriptions
category: Content Generation
technologies:
  - MEAI
status: Experimental
repo: https://github.com/dotnet/ai-samples/tree/main/src/microsoft-extensions-ai/
---

# Image Generation

> Marketing assets, product mockups, content illustrations, diagrams

## Why MEAI (IImageGenerator)

MEAI's `IImageGenerator` interface provides provider-agnostic text-to-image and image editing. Same middleware patterns as chat (logging, caching, telemetry). Currently supports OpenAI (DALL-E) and Azure OpenAI, with more providers coming.

## Architecture

```
Text prompt → MEAI IImageGenerator → Generated image
```

## Example

A content management system that generates social media images from article summaries. Content editors enter a description, and the system produces branded visuals ready for publishing.

## Note

`IImageGenerator` is currently experimental (MEAI001). The API is usable but may evolve before GA.
