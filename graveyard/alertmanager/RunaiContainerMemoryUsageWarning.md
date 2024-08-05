---
title: RunaiContainerMemoryUsageWarning
summary: This article describes the RunaiContainerMemoryUsageWarning alert.
authors:
    - Jason Novich
    - Viktor Koukouliev
date: 2024-Jan-10
---

## Meaning

A Run:ai container is using more than 80% of its Memory limit.

## Impact

The container might go out of memory (OOM) and crash.

## Severity

Warning

## Diagnosis

Use the command `kubectl top` on the relevant pod. 

If this tool is unavailable, you can calculate the memory usage by running `container_memory_usage_bytes{namespace=~"runai|runai-backend"}`.

## Mitigation

Add memory resources to the container. 
If the issue is not resolved, contact Run:ai support.
