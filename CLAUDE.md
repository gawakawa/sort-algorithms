# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a Lean 4 library project called SortAlgorithms. The project uses Lake (Lean's build system) and is configured with Nix for reproducible development environments.

## Development Environment

The project uses Nix flakes with direnv for environment management:
- `nix develop` - Enter development shell with elan and uv
- `.envrc` automatically loads the flake environment with direnv

Lean toolchain: `stable` (managed by elan)

## Common Commands

### Building and Running
- `lake build` - Build the entire project (library + executable)
- `lake exe sortalgorithms` - Run the executable defined in Main.lean
- `lake clean` - Clean build artifacts

### Testing and Verification
- `lake build` - Compiles and type-checks all Lean files (Lean proofs are verified during compilation)

### Dependencies
- `lake update` - Update dependencies from lakefile.toml

## Project Structure

The project follows standard Lean 4 library conventions:

- `Main.lean` - Entry point for the executable, imports the library
- `SortAlgorithms.lean` - Root module that imports all library modules
- `SortAlgorithms/` - Directory containing library implementation modules
  - `Basic.lean` - Basic definitions and utilities

### Module Organization

- New library modules should be added under `SortAlgorithms/` directory
- Each new module must be imported in `SortAlgorithms.lean` to be included in the library
- The executable name is `sortalgorithms` (lowercase)

## CI/CD

GitHub Actions runs `leanprover/lean-action@v1` which builds the project and verifies all proofs on every push and pull request.
