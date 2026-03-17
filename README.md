# Rust
Rust learning

## 关于是否需要 VPN / Do I Need a VPN?

**不需要 VPN**，使用国内镜像源即可正常安装和使用 Rust。

### 安装 Rust（使用国内镜像）

设置以下环境变量后再执行安装命令，rustup 将从国内镜像下载：

```bash
# 中国科学技术大学（USTC）镜像
export RUSTUP_DIST_SERVER=https://mirrors.ustc.edu.cn/rust-static
export RUSTUP_UPDATE_ROOT=https://mirrors.ustc.edu.cn/rust-static/rustup

# 然后执行官方安装命令
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

Windows 用户可在命令提示符中先执行：
```cmd
set RUSTUP_DIST_SERVER=https://mirrors.ustc.edu.cn/rust-static
set RUSTUP_UPDATE_ROOT=https://mirrors.ustc.edu.cn/rust-static/rustup
```

### 配置 crates.io 镜像（加速 cargo 下载）

编辑 `~/.cargo/config.toml`（若不存在则新建），添加以下内容：

```toml
[source.crates-io]
replace-with = 'ustc'

[source.ustc]
registry = "sparse+https://mirrors.ustc.edu.cn/crates.io-index/"
```

或使用清华大学镜像：

```toml
[source.crates-io]
replace-with = 'tuna'

[source.tuna]
registry = "sparse+https://mirrors.tuna.tsinghua.edu.cn/crates.io-index/"
```

配置完成后，`cargo build` / `cargo add` 等命令将从国内镜像拉取依赖，无需 VPN。
