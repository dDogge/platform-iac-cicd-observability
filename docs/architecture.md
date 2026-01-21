# Architecture

## Overview
This repo is the "local platform": it wires services together and provides observability.

## Components (target)
- Service containers (ingest API, analytics, registry)
- Metrics: Prometheus
- Dashboards: Grafana
- Logs (optional): Loki

## Goals
- One command to start everything locally
- Easy to see metrics/logs quickly
- CI validates configs and formatting