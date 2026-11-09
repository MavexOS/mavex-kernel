# mavex-kernel

The MavexOS kernel: a Rust crate set compiled to `wasm32-unknown-unknown`, plus the JS host that implements its imports.

- `vfs/`: in-memory filesystem (inodes, permissions, symlinks)
- `sys/`: processes, fds, pipes, ttys, signals, virtual netns, /proc
- `shell/`: the built-in `msh` fallback shell and its `Host` trait
- `kernel/`: the cdylib that wires them together and exports `k_*` / imports `mavex.*`
- `host/wasi.js`: the browser side (process scheduler, WASI + `mavex.*` imports)

Build: `cargo build --release --target wasm32-unknown-unknown -p mavex-kernel`
(output: `target/wasm32-unknown-unknown/release/mavex_kernel.wasm`).
Consumed by [MavexOS/mavexos](https://github.com/MavexOS/mavexos) via `tools/ext.sh` (pinned commit, or `MAVEX_KERNEL_DIR=...` for a local checkout).
