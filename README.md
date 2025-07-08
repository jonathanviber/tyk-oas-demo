# Tyk OAS Demo

> **⚠️ CONTRIBUTIONS WELCOME!** This implementation has some [known issues](#known-issues) and missing features. Pull requests are welcome to improve, fix, or enhance this demo!

A production-ready Tyk OSS API Gateway implementation using OpenAPI Specification (OAS) for GitOps-style endpoint management.

## Overview

This demo showcases a typical production Tyk setup with:
- **Performance optimizations** for high-scale deployments
- **GitOps approach** with OAS specifications stored in the repository
- **Logging** via Redis for collection by Tyk Pump
- **Metrics collection** using OpenTelemetry with Prometheus endpoints
- **Circuit breaker** all endpoints should implement a circuit breaker
- **Caching** Most GET endpoints should cache in REDIS
- **Rate Limiting** Some endpoints should use rate limiting with REDIS as the storage.
- **HTTP/2** Requests form the client to TYK and requests from TYK to the upstream should be HTTP/2


## Quick Start

```bash
docker compose up
```

## Endpoints

### Upstream APIs (Direct Access)
- **HTTPBin**: http://localhost/
- **Echo Server**: http://localhost:81

### Tyk Gateway
- **WORKING API Endpoints**: http://localhost:8080/api/get | http://localhost:8080/api/uuid
- **NOT WORKING API Endpoints**: http://localhost:8080/api/echo

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
- **OAS Config not working**: I have a file called api-config.json which I believe should not be necessary but if I remove it, my APIs don't register
- **Echo Endpoints**: The downstream server http://echo is configured in echo-api.json but it is calling the proxy in api-config.json
- **Metrics endpoint**: http://localhost:5555/metrics is not working correctly
- **HTTP/2 not working**: Calling endpoints from Insomnia show that they are using HTTP/1.1

## Not Yet Added
- **Caching**
- **Rate limiting**
- **Circuit breaker**
- **Logging**
- **Performance Optimizations** 