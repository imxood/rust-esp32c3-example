# rust 嵌入式

硬件: esp32c3

## 环境搭建

参考: https://esp-rs.github.io/book/

1. 安装 rust

    请参考: https://rustup.rs/

2. 安装 nightly toolchain

    rustup toolchain install nightly
    rustup default nightly

3. 创建项目

    cargo new rust-esp32c3-example

    安装 linker:
        cargo install ldproxy

    在项目中添加文件 .cargo/config, 指定编译目标, 及其它参数:

        [build]
        target = "riscv32imc-esp-espidf"

        [target.riscv32imc-esp-espidf]
        linker = "ldproxy"

        [unstable]
        build-std = ["std", "panic_abort"]
        build-std-features = ["panic_immediate_abort"]
        patch-in-config = true


4. 编译
   
   cargo install ldproxy

