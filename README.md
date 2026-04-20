# Motion Control Protocol

FlatBuffers-based protocol for motion controller communication with a 7-joint robot arm.

## Prerequisites

Install the [FlatBuffers compiler (`flatc`)](https://github.com/google/flatbuffers/releases):

```bash
# macOS
brew install flatbuffers

# Ubuntu/Debian
apt install flatbuffers-compiler

# Windows (winget)
winget install Google.FlatBuffers

# Or download a binary from the releases page above
```

## Generate Code

Run `flatc` for your target language against the schema files you need:

```bash
# Rust
flatc --rust -o out/ schemas/control_datagram.fbs schemas/control_stream.fbs

# C++
flatc --cpp -o out/ schemas/control_datagram.fbs schemas/control_stream.fbs

# Python
flatc --python -o out/ schemas/control_datagram.fbs schemas/control_stream.fbs

# TypeScript
flatc --ts -o out/ schemas/control_datagram.fbs schemas/control_stream.fbs
```

See `flatc --help` for all supported languages.
