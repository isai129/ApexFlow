# ApexFlow

[English](README.md) | 简体中文

手机（Shadowrocket + Loon）的代理配置仓，外加 Tailscale DERP 直连规则与国内可达的镜像。定位是公开仓——**不含机场订阅链接、任何密钥、私有主机信息**。

## 文件

| 文件 | 用途 | 拉取地址 |
|---|---|---|
| `ApexFlow.conf` | 手机 Shadowrocket 配置（当前版） | Pages（配置内 `update-url` 自指）— App 内「更新配置」 |
| `ApexFlow-Loon.conf` | 手机 Loon 配置（当前版，Tailscale 节点需 ≥3.5.4） | Pages — 导入一次，之后 App 内「更新」 |
| `ApexFlow_backup` | 上一版 Shadowrocket 配置（v7），紧急回滚用 | — |
| `{{TERM_b4cqz2lbz}}-derp-direct.list` / `.yaml` | Tailscale DERP 服务器 IP 直连规则，经 `RULE-SET` 引用 | jsDelivr |
| `vendor/` | 第三方资源镜像（Sub-Store 解析器、iRingo WeatherKit），保证国内网络可靠拉取 | Pages |

## 使用

- **Shadowrocket**：把 `ApexFlow.conf` 添加为远程配置；配置内 `update-url` 已指向本仓（GitHub Pages），App 内直接「更新配置」拉变更。
- **Loon**：从 Pages 导入 `ApexFlow-Loon.conf`。**配置与订阅分离**：机场订阅放在 App 级「订阅」页（添加一次、启用 Sub-Store 解析器），更新配置不影响订阅。
- 本仓通过 **GitHub Pages** 发布（`isai129.github.io/ApexFlow/...`）——jsDelivr 的 @main 分支缓存实测不可靠，raw.githubusercontent 在国内蜂窝网被墙。规则集 URL 仍走 jsDelivr（上游仓库稳定）。

## 说明

- `{{TERM_b4cqz2lbz}}-derp-direct.list` 由家里服务器的脚本每周从实时 DERPMap 自动重生成（DERP 服务器 IP 会轮换，静态列表会过期），手工改动会被覆盖。
- `vendor/` 文件是未改动的第三方发布物，唯一例外是 `iRingo.WeatherKit.lpx` 内的 script-path 已重写到本目录（上游更新时重新下载并重做该改写）。
- 2026-11-02 从私有仓 `SR_Conf` 拆分而来；SR_Conf 保留 mihomo/主机配置模板与镜像。
