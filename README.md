# Motion Control Protocol

FlatBuffers schemas for communication with a Ruvion motion controller.
Supports both single-arm (standalone) and humanoid (dual-arm) robots; each
Ruvion arm has 7 joints.

## Schemas

| File                     | Purpose                        | Transport                             |
| ------------------------ | ------------------------------ | ------------------------------------- |
| `control_datagram.fbs`   | High-frequency motion commands | Unreliable QUIC datagram (client → controller) |
| `control_stream.fbs`     | Control-plane commands + reply | Reliable QUIC stream (client ↔ controller)     |
| `telemetry_datagram.fbs` | High-frequency state feedback  | Unreliable QUIC datagram (controller → client) |
| `event.fbs`              | Discrete state-change events   | Reliable unidirectional QUIC stream (controller → client) |

Units, reference frames, and joint conventions are documented in the header of each `.fbs` file.

## Prerequisites

Install the [FlatBuffers compiler (`flatc`)](https://github.com/google/flatbuffers/releases):

```bash
# macOS
brew install flatbuffers

# Ubuntu/Debian
apt install flatbuffers-compiler

# Windows (winget)
winget install Google.FlatBuffers
```

## Generate Code

Run `flatc` for your target language against the schemas you need:

```bash
# Rust
flatc --rust -o out/ schemas/*.fbs

# C++
flatc --cpp -o out/ schemas/*.fbs

# Python
flatc --python -o out/ schemas/*.fbs

# TypeScript
flatc --ts -o out/ schemas/*.fbs
```

See `flatc --help` for all supported languages.
