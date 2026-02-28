# ClashRuleSet

用于分享和维护 Clash/Clash Meta 可用的 `.list` 规则集。

## 仓库定位

- 本仓库只提供规则列表（`*.list`）。
- 不提供机场订阅、节点信息或任何私密配置。
- 你可以将本仓库规则接入自己的 Clash 配置（本地、NAS 或云端模板均可）。

## 目录结构

- `Clash/`：基础通用规则（如 LAN、广告、直连/代理基础分类等）。
- `Clash/Ruleset/`：细分业务规则（如 AI、媒体、游戏、平台服务等）。

## 在 Clash Meta 中使用

以下为示例（可按需修改策略组名、缓存路径和更新周期）：

```yaml
rule-providers:
  rule_provider_ai_domain:
    type: http
    format: text
    behavior: classical
    url: "https://raw.githubusercontent.com/Mistakey/ClashRuleSet/main/Clash/Ruleset/AiDomain.list"
    path: ./ruleset/ai_domain.list
    interval: 86400

rules:
  - RULE-SET,rule_provider_ai_domain,🌈 OpenAI
  - MATCH,🐟 漏网之鱼
```

## 常用规则地址示例

- `https://raw.githubusercontent.com/Mistakey/ClashRuleSet/main/Clash/LocalAreaNetwork.list`
- `https://raw.githubusercontent.com/Mistakey/ClashRuleSet/main/Clash/BanAD.list`
- `https://raw.githubusercontent.com/Mistakey/ClashRuleSet/main/Clash/Ruleset/AiDomain.list`
- `https://raw.githubusercontent.com/Mistakey/ClashRuleSet/main/Clash/Ruleset/Netflix.list`

## 说明

- `behavior: classical` 搭配 `.list` 文本规则使用。
- 建议为 `rule-providers` 显式设置 `format: text`，避免内核按 YAML payload 解析导致报错。
