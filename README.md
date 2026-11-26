# abs-menu · antiBallsheet 中文三合一

> 浏览器里练反应与注意力的三套玩法，**单个 HTML 文件**、全中文界面、手机可玩。
> Live demo：**https://kiryugit.github.io/abs-menu/**

一个把 [dphdmn/antiBallsheet](https://github.com/dphdmn/antiBallsheet) 重做成「中文主菜单 + 三套玩法」的二次创作版本：保留原作的速通手感，加上生存模式与舒尔特方格，并补齐小屏适配、触控与外观设置。

## 三套玩法

| 玩法 | 一句话 |
| --- | --- |
| **速通** | 原版 antiBallsheet：固定球数，越快吃完越好，记录每球反应。 |
| **BallSheet · 生存** | 血量随时间被压力扣减，吃球回血；有「球色随血量」与「边框随血量」两套配色。 |
| **舒尔特方格** | 425 px 方格，5 种尺寸 × 9 种规则，专注力训练。 |

舒尔特九种规则：`Light`、`Classic`、`Light Reverse`、`Classic Reverse`、`Memory`、`Reaction`、`Letters`、`Colors`、`Gorbow`；尺寸 3×3 / 4×4 / 5×5 / 7×7 / 10×10。点中即判（按下就计数，不等抬手），点错只记错误不罚时。

## 特点

- 单文件交付：音频、字体、图表全部以 data URI 内嵌，双击即玩，无需服务器。
- 全中文：菜单、模式、数据、外观、音效、玩法说明、关于。
- 手机适配：整套 600 px 场地等比缩放，支持触控按地即判、横屏排版、刘海安全区。
- 可换音效：接球 / 悬停 / 点击三个槽位，音频存本地。
- 本地统计：三套玩法独立存档，历史曲线、最快 / 平均 / 零错率，可导出 JSON。
- 外观自定义：场地底色、边框、球色、光标尺寸；舒尔特为白卡黑字深色主题。
- 开局节奏与 [schulte-table.com](https://schulte-table.com/) 对齐：`开始` → 3·2·1 倒计时 → 起表；Memory 为 3 秒记忆窗。

## 操作

- 主菜单 9 项：开始 / BallSheet / 舒尔特 / 模式 / 数据 / 外观 / 音效 / 玩法 / 关于。
- `R` 或 `空格`：重开（回到准备态）；`Esc`：暂停 / 返回。
- 手机：直接点按，触控按地即判。

## 部署

仓库根目录的 `index.html` 就是全部内容，把它放到任意静态托管即可（GitHub Pages / Cloudflare Pages / 自己的服务器）。本地预览：

```bash
python -m http.server 8000
# 浏览器打开 http://localhost:8000/
```

## 来源与致谢

- 原作：[dphdmn/antiBallsheet](https://github.com/dphdmn/antiBallsheet)（基于 [ballsheet](https://github.com/dphdmn/ballsheet) 的速通改版）。本仓库是在原作基础上的中文重构与玩法扩展，**非原创**，原作版权归原作者。
- 舒尔特方格的尺寸比例、配色与部分交互参考 [schulte-table.com](https://schulte-table.com/)。

## 版本

`v0.5.1` — 舒尔特新增九种规则与 425 px 方格、开局倒计时、按地即判、球色双模式。
