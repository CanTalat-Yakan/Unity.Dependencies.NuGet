# Unity Essentials

This module is part of the Unity Essentials ecosystem and follows the same lightweight, editor-first approach.
Unity Essentials is a lightweight, modular set of editor utilities and helpers that streamline Unity development. It focuses on clean, dependency-free tools that work well together.

All utilities are under the `UnityEssentials` namespace.

```csharp
using UnityEssentials;
```

## Installation

Install the Unity Essentials entry package via Unity's Package Manager, then install modules from the Tools menu.

- Add the entry package (via Git URL)
  - Window → Package Manager
  - "+" → "Add package from git URL…"
  - Paste: `https://github.com/CanTalat-Yakan/UnityEssentials.git`

- Install or update Unity Essentials packages
  - Tools → Install & Update UnityEssentials
  - Install all or select individual modules; run again anytime to update

---

# NuGet

> Quick overview: In‑Editor NuGet package management powered by NuGetForUnity. Search, install, update, and restore NuGet packages directly from Unity; supports custom feeds and credentials.

This dependency module brings the NuGetForUnity plugin into your project so you can manage NuGet packages without leaving the Editor. Use the NuGet window to search public or private feeds, install/update/remove packages, and perform restores when opening a project. It’s ideal for pulling in .NET libraries that work with your Unity target frameworks.

![screenshot](Documentation/Screenshot.png)

## Features
- Manage NuGet packages without external tooling (search, install, update, remove, restore)
- Works with nuget.org out of the box; add custom/private feeds via configuration
- Supports authenticated feeds (username/password or token) via NuGetForUnity settings
- Restores packages when opening a project or on demand (configurable)
- Ships NuGetForUnity’s Plugin API assembly for advanced/editor automation scenarios

## Requirements
- Unity Editor 6000.0+ (Editor‑only)
- Internet access to reach NuGet feeds
- Packages must be compatible with your Editor/.NET target (e.g., .NET Standard 2.x)
- For private feeds: credentials or access tokens as required by your host

## Usage

- Open the NuGet window
- Use the NuGetForUnity menu item (commonly under Window → NuGet or a top‑level NuGet menu)
- If you don’t see it, restart Unity after importing this module
- Find and install packages
- Search for a package (e.g., Newtonsoft.Json)
- Choose a version and click Install; the plugin downloads the package and adds the assemblies to your project
- Update/Remove
- Switch to the Installed tab to update or remove packages
- Configure automatic restore on load if desired
- Feeds and authentication
- Open NuGet settings in the plugin window
- Add additional feeds (URL) and set credentials if you use private feeds

### Feeds and authentication
- Public feed (nuget.org) works without credentials
- Private feeds: add the feed URL in Settings and provide credentials or an access token as required by your server (e.g., GitHub Packages, Azure Artifacts)
- Some hosts require a scoped source URL or specific auth scheme; follow your provider’s documentation

## Notes and Limitations
- Unity supports a subset of .NET; some NuGet packages may target frameworks not compatible with your Editor/runtime
- Packages that bundle native plugins or platform‑specific assets may require manual setup for Unity
- Depending on your project structure, you may need to reference installed assemblies from your .asmdef files
- Consider committing the Packages/ or NuGet/ cache according to your team policy; large binary caches can bloat repos
- Ensure restore is run on CI before building if your pipeline relies on NuGet packages

## Files in This Package
- Editor/NugetForUnity.dll – NuGetForUnity plugin
- Editor/NuGetForUnity.PluginAPI.dll – NuGetForUnity Plugin API (for advanced integrations)
- Editor/NuGetForUnity.PluginAPI.xml – API XML docs
- Resources/defaultIcon.png – Default icon used by the plugin
- package.json – Package manifest metadata

## Tags
unity, nuget, nugetforunity, dependencies, packages, restore, feeds, authentication, editor-tool