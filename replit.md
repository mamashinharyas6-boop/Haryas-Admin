# Haryas Admin (Haryas Admin)

## Overview

Haryas Admin is a Roblox admin script that provides command execution capabilities through a loadstring-based loader. The project serves as the official continuation of the original Haryas Admin script, adding new commands, fixes, and plugin support.

The core functionality is a Lua-based admin command system that users execute in Roblox through script executors. The project also includes a Node.js web component using Express, likely for documentation or hosting purposes.

Key features:
- Loadstring-based script loader for Roblox
- Plugin system supporting two formats: `.na` (native) and `.iy` (Infinite Yield compatible)
- Command system with aliases, argument hints, and required argument validation

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Dual-Component Structure

**Lua Admin Script (Primary)**
- `Source.lua` - Main production script loaded via HTTP GET from GitHub raw
- `HA testing.lua` - Development/testing version of the script
- Plugin architecture with two loading directories:
  - `Haryas-Admin/Plugins` for `.na` format plugins
  - `Haryas-Admin/PluginsIY` for `.iy` format plugins (Infinite Yield compatibility)

**Node.js Web Server (Secondary)**
- Express 5.x web server (`index.js` entry point)
- Marked library for Markdown parsing (likely for documentation rendering)
- Minimal configuration with no database or authentication

### Plugin System Design

Plugins follow a structured object format:
- `Aliases` - Array of command triggers
- `ArgsHint` - Usage hint string
- `Info` - Command description
- `Function` - Command implementation callback
- `RequiresArguments` - Boolean flag for argument validation

This modular approach allows users to extend functionality without modifying core scripts.

### Deployment Model

The Lua scripts are hosted on GitHub and loaded dynamically via `HttpGet`, enabling:
- Instant updates without user action
- Separation of loader from execution environment
- Two-branch approach (main vs testing) for staged releases

## External Dependencies

### Node.js Dependencies
| Package | Version | Purpose |
|---------|---------|---------|
| express | ^5.2.1 | Web server framework |
| marked | ^17.0.1 | Markdown to HTML conversion |

### External Services
- **GitHub Raw** - Hosts Lua source files for HTTP-based loading
- **Roblox HttpService** - Client-side HTTP requests for script loading

### File System Requirements
Users must configure their script executor's workspace with:
- `Haryas-Admin/Plugins/` directory for native plugins
- `Haryas-Admin/PluginsIY/` directory for Infinite Yield plugins