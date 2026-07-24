# vllm-fixed

A small, public compatibility patch for Runpod's Serverless vLLM worker.

This repository is based on Runpod's public
[`runpod-workers/worker-vllm`](https://github.com/runpod-workers/worker-vllm)
release `v2.22.5`. The only material runtime change is pinning vLLM 0.25.0
instead of the upstream release's 0.20.2.

It intentionally contains no model weights, tokens, endpoint IDs, local paths,
prompts, or user-specific configuration.

## What changed

```dockerfile
ARG VLLM_VERSION="0.25.0"
uv pip install --system "vllm[flashinfer]==${VLLM_VERSION}"
```

DeepGEMM is not installed by this patch because it is optional and disabled by
default in the worker.

## Build

Runpod can build this image directly from this public repository using its
GitHub integration. Configure model selection, credentials, and endpoint
settings in Runpod rather than committing them here.

## Upstream

The local `upstream` Git remote tracks the official Runpod worker and is
configured fetch-only. See the upstream documentation in `docs/` for the
worker API and configuration reference.
