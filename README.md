# escrunch

An ESM module-to-module bundler, written in Rust. Early development — no bundling logic is implemented yet.

## What it is

escrunch is intended to be a bundler that takes ECMAScript modules as input and produces transformed/bundled ESM output. The design relies on SWC for parsing, AST manipulation, and code generation.

## Current state

The workspace compiles, but the library (`crates/escrunch/src/lib.rs`) is currently empty. No bundling, transformation, or output logic exists yet. The project is at version 0.1.0 and is pre-alpha.

## Repository layout

```
Cargo.toml                  # Workspace root (single member: crates/escrunch)
crates/
  escrunch/
    Cargo.toml              # Package manifest
    src/
      lib.rs                # Library entry point (currently empty)
```

## Dependencies

All dependencies are declared at the workspace level in the root `Cargo.toml`.

**SWC crates** (all from the `swc-project/swc` ecosystem):

| Crate | Purpose |
|---|---|
| `swc_ecma_parser` | Parse JS/TS source into an AST |
| `swc_ecma_ast` | AST type definitions |
| `swc_ecma_visit` | AST visitor/fold traits |
| `swc_ecma_codegen` | Emit JS source from an AST |
| `swc_ecma_utils` | Common AST helpers |
| `swc_ecma_transforms_base` | Base transform infrastructure |
| `swc_ecma_transforms_optimization` | Optimization passes |
| `swc_ecma_compat_es2015` | ES2015 compatibility transforms |
| `swc_ecma_minifier` | Minification |
| `swc_bundler` | Module bundling |
| `swc_ecma_loader` | Module resolution |
| `swc_common` | Source maps, spans, error reporting |
| `swc_atoms` | Interned string atoms |

**Internal/private crates** (fetched from git):

- `portal-solutions-swibb` (`github.com/portal-co/swibb`, `^0.6.0-alpha.1`) — purpose unclear from this repository alone
- `rayoff` (`github.com/portal-co/rayoff`, `0.1.0`) — purpose unclear from this repository alone

Only `rayoff`, `swc_atoms`, `swc_common`, `swc_ecma_ast`, `swc_ecma_visit`, and `portal-solutions-swibb` are currently referenced in the crate's own `Cargo.toml`. The remaining SWC crates are declared in the workspace but not yet used by any member.

## License

MPL-2.0
