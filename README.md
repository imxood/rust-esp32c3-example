# rust riscv esp32

Hardware: esp32 c3
System: Windows 10 pro

## environment

参考: https://esp-rs.github.io/book/

1. install rust

    请参考: https://rustup.rs/

2. use nightly toolchain

    rustup toolchain install nightly
    rustup default nightly

3. create project

    cargo new rust-esp32c3-example

4. create file .cargo/config:

```
[build]
target = "riscv32imc-esp-espidf"

[unstable]
build-std = ["std", "panic_abort"]
build-std-features = ["panic_immediate_abort"]

[env]
ESP_IDF_GLOBAL_INSTALL = { value = "1" }
```

5. add dependence

    cargo add esp-idf-sys --features "native binstart std"

6. main.rs

```rust
use esp_idf_sys;

fn main() {
    // Temporary. Will disappear once ESP-IDF 4.4 is released, but for now it is necessary to call this function once,
    // or else some patches to the runtime implemented by esp-idf-sys might not link properly.
    esp_idf_sys::link_patches();

    println!("Hello, world!");
}
```

7. build

   cargo build

8. flash

    cargo install espflash

    espflash /dev/ttyUSB0 target/riscv32imc-esp-espidf/debug/rust-esp32-std-mini