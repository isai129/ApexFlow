# ApexFlow

Shadowrocket 远程配置与 Tailscale DERP 直连规则集。

| 文件 | 用途 | 远程地址 |
|---|---|---|
| `ApexFlow.conf` | Shadowrocket 主配置（v8） | `https://raw.githubusercontent.com/isai129/ApexFlow/refs/heads/main/ApexFlow.conf` |
| `ApexFlow_backup` | 上一版配置（v7），回滚用 | — |
| `tailscale-derp-direct.list` | Tailscale DERP 服务器 IP 直连规则（`ApexFlow.conf` 通过 `RULE-SET` 引用） | `https://raw.githubusercontent.com/isai129/ApexFlow/refs/heads/main/tailscale-derp-direct.list` |

## 使用

在 Shadowrocket 里用上面的 `ApexFlow.conf` raw 地址添加远程配置；配置内 `update-url` 已指向本仓库，之后可直接「更新配置」拉取变更。

## 说明

- 本仓库**不含机场订阅链接与任何密钥**——订阅在 Shadowrocket 内单独管理。
- `tailscale-derp-direct.list` 由 hp-server 上的 `refresh-derp-rules.sh` 每周从当前 DERPMap 自动重生成（DERP 服务器 IP 会轮换，静态规则集会过期）。手工改这个文件会在下次自动刷新时被覆盖。
- 从私有仓库 `SR_Conf` 拆分而来（2026-11-02）：SR_Conf 保留 mihomo/主机配置模板，本仓库只放需要被 Shadowrocket 公网拉取的文件。
