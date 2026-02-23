# Motion Control Protocol

FlatBuffers-based protocol for motion controller communication.

## Repository Structure

```
schemas/               FlatBuffers schema definitions
```

## Prerequisites

- [FlatBuffers compiler (`flatc`)](https://github.com/google/flatbuffers) – used to generate language-specific code from the `.fbs` schemas.

## Generate Code

```bash
# Rust
flatc --rust -o out/ schemas/motion_control.fbs

# C++
flatc --cpp -o out/ schemas/motion_control.fbs

# Python
flatc --python -o out/ schemas/motion_control.fbs

# TypeScript
flatc --ts -o out/ schemas/motion_control.fbs
```

See `flatc --help` for all supported languages.

## Schema Overview

The protocol defines a `Command` message with a union body that can be one of:

| Command       | Description                    |
|---------------|--------------------------------|
| `MoveCommand` | Move to a target position      |
| `HomeCommand` | Home one or all axes           |
| `StopCommand` | Stop all motion                |

A `Status` table is provided for controller state reporting.
