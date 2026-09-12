# OpenWRT-CI（兆能 M2 + 京东云亚瑟）

基于 [VIKINGYFY/OpenWRT-CI](https://github.com/VIKINGYFY/OpenWRT-CI) 的精简云编译仓库，只编两台机器：

- 兆能 M2（`zn_m2`）
- 京东云亚瑟（`jdcloud_re-ss-01`）

源码使用 `VIKINGYFY/immortalwrt` 的 `main` 分支，带 Wi-Fi。

## 默认信息

- 地址：`192.168.10.1`
- 密码：无
- Wi-Fi：`OWRT` / `12345678`

## 插件策略

保留常用科学上网（HomeProxy）和基础网络功能，去掉下载、网盘、Samba、游戏加速、多主题等冗余插件。

额外加入：

- **UA3F**：改写 User-Agent，并编入所需 iptables / nftables 内核模块
- **SMART SRun**（`luci-app-smart-srun`）：深澜校园网 Web 认证，LuCI 路径为「服务 → SMART SRun」

## 使用方法

1. 把本仓库推到你自己的 GitHub（需要先登录 `gh` 或在网页上创建仓库）
2. 打开 Actions，运行 **QCA-ALL**
3. 编译完成后在 Releases 里下载：
   - `*zn_m2*`：兆能 M2
   - `*jdcloud_re-ss-01*`：京东云亚瑟

手动编译时可在 `PACKAGE` 输入框追加配置行，例如：

```text
CONFIG_PACKAGE_luci-app-passwall=y
```

勾选 `TEST` 则只生成 `.config`，不真正编译。

## 目录

- `.github/workflows`：云编译流程
- `Config`：设备和插件配置
- `Scripts`：拉包、修补、默认设置
