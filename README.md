# Cadence

Client-side performance mod for [Vintage Story](https://www.vintagestory.at).

Cadence reduces frame time and GC pressure by skipping work that produces no observable result. Same philosophy as [Stratum](https://github.com/trevorftp/Stratum) (server-side), applied to the client.

## Status

Early development. Not yet released.

## Scope

- Client-side only. Works with vanilla servers and Stratum servers.
- Zero gameplay changes. Optimizations are invisible to the player.
- Configurable. Each optimization has a toggle.

## Requirements

- Vintage Story 1.22.3+
- .NET 10 runtime (ships with VS 1.22)

## License

MIT
