<div align="center">
  <img src="logo.svg" width="128" height="128" alt="Optimum"/>
  <h1>Optimum</h1>
</div>

[![License](https://img.shields.io/badge/license-GPL--3.0%20%2B%20Commons%20Clause-blue)](LICENSE)
[![VS Version](https://img.shields.io/badge/Vintage%20Story-1.22.3-green)](https://www.vintagestory.at)
[![Donate](https://img.shields.io/badge/Ko--fi-Zaldaryon-ff5e5b?logo=ko-fi)](https://ko-fi.com/zaldaryon)

Optimum is a high-performance, client-side fork of [Vintage Story](https://www.vintagestory.at). It decompiles the official client, applies performance patches at compile time, and produces optimized DLLs and shaders. No Harmony. No runtime patching. Same gameplay, faster frames.

## Features

- Precise frame pacing (hybrid sleep/yield/spin, fixes micro-stutter)
- Background FPS limiter (20 FPS when alt-tabbed)
- Weather wind throttling (cache lookups for 4 frames)
- Ticking blocks GC reduction (reuse BlockPos in particle loop)
- Ambient sound position throttling (skip updates when stationary)
- Fly sound volume deduplication (skip updates below 1% change)
- Entity shadow distance culling (skip draws beyond 80 blocks)
- Entity repulsion distance gate (skip physics beyond 64 blocks)
- Dynamic light radius scaling (35-60 blocks based on view distance)
- Animated block LOD (3-tier distance scaling for forges, querns, etc.)
- SSAO bilateral blur tap reduction (11 to 7 taps, 8 fewer texture reads/pass)
- Water foam grid reduction (5x5 to 3x3, 16 fewer depth reads per fragment)
- Mat4f.Multiply inlining (13 hot methods, eliminates call overhead)
- Mouse wheel fix at low sensitivity (#9710)
- Prospecting dialog mouse fix (#8874)
- Health tooltip decimal fix (#8901)

## Install

Optimum ships as source. Download the source archive from the [Releases](https://github.com/Zaldaryon/Optimum/releases) page, extract it, and run the build script for your platform. The script downloads the official client on your machine, builds the optimized DLLs, and produces a ready-to-run folder. Requires the .NET 10 SDK.

| Platform | Command |
|---|---|
| Windows x64 | `powershell -ExecutionPolicy Bypass -File build-windows.ps1` |
| Linux x64 | `./build-linux.sh` |
| macOS | `./build-macos.sh` |

See the [wiki](https://github.com/Zaldaryon/Optimum/wiki) for detailed installation instructions, build-from-source guide, and feature documentation.

## Compatibility

Optimum connects to any server running Vintage Story 1.22.3. Servers need nothing installed. Worlds, accounts, and mods carry over unchanged.

## Build from Source

Requires .NET 10 SDK, bash, python3, git, curl, perl.

```bash
make build    # bootstrap + compile (first run downloads ~570MB)
make test     # 81 unit tests
make run      # build, deploy, launch
make package  # ready-to-run packages for all platforms (built locally)
```

See the [Building from Source](https://github.com/Zaldaryon/Optimum/wiki/Building-from-Source) wiki page for the full guide.

## Contributing

Pull requests welcome. See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## Donate

If Optimum improves your experience, consider supporting development:

[![Ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/zaldaryon)

## Legal

Vintage Story is developed and published by [Anego Studios](https://www.vintagestory.at). Optimum distributes no game files: it ships only its own source, the performance patches and Optimum source files. It contains no game assets, no prebuilt binaries, and none of the official client code. The build downloads the official client from Anego on your machine and applies the Optimum patches there, so the assets, runtime, and resulting DLLs all stay local to your install. A valid Vintage Story account is required to play.

## License

GPL-3.0 with the Commons Clause. Read the source, modify it, share it. Copyleft applies. You cannot sell Optimum or a product whose value derives from it. See [LICENSE](LICENSE) for the full terms.
