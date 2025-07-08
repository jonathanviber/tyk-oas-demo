# Tyk OAS Demo

> **⚠️ CONTRIBUTIONS WELCOME!** This implementation has some [known issues](#known-issues) and missing features. Pull requests are welcome to improve, fix, or enhance this demo!

A production-ready Tyk OSS API Gateway implementation using OpenAPI Specification (OAS) for GitOps-style endpoint management.

## Overview

This demo showcases a typical production Tyk setup with:
- **Performance optimizations** for high-scale deployments
- **Logging** via Redis for collection by Tyk Pump
- **Metrics collection** using OpenTelemetry with Prometheus endpoints
- **GitOps approach** with OAS specifications stored in the repository

## Quick Start

```bash
docker compose up
```

## Endpoints

### Upstream APIs (Direct Access)
- **HTTPBin**: http://localhost/
- **Echo Server**: http://localhost:81

### Tyk Gateway
- **API Endpoints**: http://localhost:8080/api/get | http://localhost:8080/api/uuid

### Admin & Monitoring
- **Health Check**: http://localhost:5555/health
- **Metrics**: http://localhost:5555/metrics

## Architecture

- **Gateway**: Tyk OSS Gateway with production-ready configuration
- **Storage**: Redis for caching, rate-limiting and log aggregation
- **Monitoring**: OTEL metrics exported to Prometheus format
- **Logging**: Structured logs sent to Redis (Tyk Pump not included)
- **Configuration**: OAS-based API definitions for GitOps workflows

## Known Issues

- **Metrics endpoint**: http://localhost:5555/metrics is not working correctly