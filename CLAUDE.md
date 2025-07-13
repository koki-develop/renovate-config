# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository contains Renovate configuration presets for managing dependency updates. It provides reusable Renovate configurations for different tools and environments.

## Repository Structure

- `default.json` - Main preset that extends config:recommended and includes all tool-specific presets
- `base.json` - Base configuration with pin strategy and release age minimums
- `aqua.json` - Extends aqua-renovate-config for aqua package manager
- `biome.json5` - Custom manager for Biome schema updates in biome.json files
- `docker.json` - Docker-related configuration preset
- `go.json` - Go-specific dependency management preset

## Common Commands

Format all files:

```bash
npm run format
```

Format JSON files only:

```bash
npx prettier --write "*.json"
```

Validate Renovate configuration:

```bash
npx renovate-config-validator
```

## Architecture

The preset system follows a hierarchical structure:

- `default.json` serves as the entry point, extending Renovate's recommended config
- Tool-specific presets (`aqua.json`, `biome.json5`, `docker.json`, `go.json`) handle custom dependency detection
- `base.json` provides common settings like version pinning and minimum release ages
- Each preset can be used independently via `local>koki-develop/renovate-config:preset-name`

The custom managers use regex patterns to detect dependencies in configuration files that Renovate doesn't natively support.
