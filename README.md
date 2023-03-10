# CardTradeExtension

[![Codacy Badge](https://app.codacy.com/project/badge/Grade/45b50288f8b14ebda915ed89e0382648)](https://www.codacy.com/gh/chr233/CardTradeExtension/dashboard)
![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/chr233/CardTradeExtension/autobuild.yml?logo=github)
[![License](https://img.shields.io/github/license/chr233/CardTradeExtension?logo=apache)](https://github.com/chr233/CardTradeExtension/blob/master/license)

[![GitHub Release](https://img.shields.io/github/v/release/chr233/CardTradeExtension?logo=github)](https://github.com/chr233/CardTradeExtension/releases)
[![GitHub Release](https://img.shields.io/github/v/release/chr233/CardTradeExtension?include_prereleases&label=pre-release&logo=github)](https://github.com/chr233/CardTradeExtension/releases)
![GitHub last commit](https://img.shields.io/github/last-commit/chr233/CardTradeExtension?logo=github)

![GitHub Repo stars](https://img.shields.io/github/stars/chr233/CardTradeExtension?logo=github)
[![GitHub Download](https://img.shields.io/github/downloads/chr233/CardTradeExtension/total?logo=github)](https://img.shields.io/github/v/release/chr233/CardTradeExtension)

[![Bilibili](https://img.shields.io/badge/bilibili-Chr__-00A2D8.svg?logo=bilibili)](https://space.bilibili.com/5805394)
[![Steam](https://img.shields.io/badge/steam-Chr__-1B2838.svg?logo=steam)](https://steamcommunity.com/id/Chr_)

[![Steam](https://img.shields.io/badge/steam-donate-1B2838.svg?logo=steam)](https://steamcommunity.com/tradeoffer/new/?partner=221260487&token=xgqMgL-i)
[![爱发电](https://img.shields.io/badge/爱发电-chr__-ea4aaa.svg?logo=github-sponsors)](https://afdian.net/@chr233)

CardTradeExtension 介绍 & 使用指南: [https://keylol.com/t876377-1-1](https://keylol.com/t876377-1-1)

## EULA

> 请不要使用本插件来进行不受欢迎的行为, 包括但不限于: 刷好评, 发布广告 等.
>
> 详见 [插件配置说明](#插件配置说明)

## 安装方式

### 初次安装 / 手动更新

1. 从 [GitHub Releases](https://github.com/chr233/CardTradeExtension/releases) 下载插件的最新版本
2. 解压后将 `CardTradeExtension.dll` 丢进 `ArchiSteamFarm` 目录下的 `plugins` 文件夹
3. 重新启动 `ArchiSteamFarm` , 使用命令 `CTE` 来检查插件是否正常工作

### 使用命令升级插件

> 可以使用插件自带的命令自带更新插件
> ASF 版本升级有可能出现不兼容情况, 如果发现插件无法加载请尝试更新 ASF

- `CTEVERSION` / `CTEV` 检查插件更新
- `CTEUPDATE` / `CTEU` 自动更新插件到最新版本 (需要手动重启 ASF)

### 更新日志

| CardTradeExtension 版本                                                      | 适配 ASF 版本 | 更新说明   |
| ---------------------------------------------------------------------------- | :-----------: | ---------- |
| [1.0.0.0](https://github.com/chr233/CardTradeExtension/releases/tag/1.0.0.0) |   5.4.2.13    | 第一个版本 |

<details>
  <summary>历史版本</summary>

| CardTradeExtension 版本 | 依赖 ASF 版本 | 5.3.1.2 | 5.3.2.4 | 5.4.0.3 | 5.4.1.11 |
| ----------------------- | :-----------: | :-----: | :-----: | :-----: | :------: |
| -                       |       -       |   ❌    |   ❌    |   ✔️    |    ✔️    |

</details>

## 插件配置说明

> 本插件的配置不是必须的, 保持默认配置即可使用大部分功能

ASF.json

```json
{
  //ASF 配置
  "CurrentCulture": "...",
  "IPCPassword": "...",
  "...": "...",
  //CardTradeExtension 配置
  "CardTradeExtension": {
    "EULA": true,
    "Statistic": true,
    "DisabledCmds": ["foo", "bar"],
    "MaxItemPerTrade": 255
  }
}
```

| 配置项            | 类型   | 默认值 | 说明                                                                                      |
| ----------------- | ------ | ------ | ----------------------------------------------------------------------------------------- |
| `EULA`            | bool   | `true` | 是否同意 [EULA](#EULA)\*                                                                  |
| `Statistic`       | bool   | `true` | 是否允许发送统计数据, 仅用于统计插件用户数量, 不会发送任何其他信息                        |
| `DisabledCmds`    | list   | `null` | 在此列表中的命令将会被禁用\*\* , **不区分大小写**, 仅对 `CardTradeExtension` 中的命令生效 |
| `MaxItemPerTrade` | ushort | `255`  | 单个交易最多物品数量, ASF 的默认值是 255, 如果报价中的物品超过此数量会自动拆分成多个报价  |

> \* 同意 [EULA](#EULA) 后, CardTradeExtension 将会开放全部命令
>
> \* 禁用 [EULA](#EULA) 后, CardTradeExtension 将无法使用大部分命令
>
> \*\* `DisabledCmds` 配置说明: 该项配置**不区分大小写**, 仅对 `CardTradeExtension` 中的命令有效
> 例如配置为 `["foo","BAR"]` , 则代表 `FOO` 和 `BAR` 命令将会被禁用
> 如果无需禁用任何命令, 请将此项配置为 `null` 或者 `[]`
> 当某条命令被禁用时, 仍然可以使用 `CTE.xxx` 的形式调用被禁用的命令, 例如 `CTE.FULLSETLIST`

## 插件指令说明

### 插件更新

| 命令                 | 缩写   | 权限            | 说明                                                      |
| -------------------- | ------ | --------------- | --------------------------------------------------------- |
| `CardTradeExtension` | `CTE`  | `FamilySharing` | 查看 CardTradeExtension 的版本                            |
| `CTEVERSION`         | `CTEV` | `Operator`      | 检查 CardTradeExtension 是否为最新版本                    |
| `CTEUPDATE`          | `CTEU` | `Owner`         | 自动更新 CardTradeExtension 到最新版本 (需要手动重启 ASF) |

### 主要功能

| 命令                                           | 缩写   | 权限       | 说明                                                         |
| ---------------------------------------------- | ------ | ---------- | ------------------------------------------------------------ |
| `FULLSETLIST [Bots] [Config]`                  | `FSL`  | `Operator` | 显示卡牌套数信息, 可用参数 \[-page 页码\] \[-line 显示行数\] |
| `FULLSET [Bots] <appIds>`                      | `FS`   | `Operator` | 显示指定 App 的卡牌套数信息                                  |
| `SENDCARDSET [Bots] AppId SetCount TradeLink`  | `SCS`  | `Master`   | 向指定交易链接发送指定`SetCount`套指定`AppId`的卡牌          |
| `2SENDCARDSET [Bots] AppId SetCount TradeLink` | `2SCS` | `Master`   | 同 `SENDCARDSET`, 发送交易后自动确认交易 (需要配置 2FA)      |

---

[![Repobeats analytics image](https://repobeats.axiom.co/api/embed/c7bad85b243c7305a5de1fa591469f64125c4048.svg "Repobeats analytics image")](https://github.com/chr233/CardTradeExtension/pulse)

---

[![Stargazers over time](https://starchart.cc/chr233/CardTradeExtension.svg)](https://github.com/chr233/CardTradeExtension/stargazers)

---
