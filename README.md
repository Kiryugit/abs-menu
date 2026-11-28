<p align="center">
  <a href="https://kiryugit.github.io/abs-menu/">
    <img src="gh-pages/docs/preview-home.png" width="880" alt="antiBallsheet 中文主菜单">
  </a>
  <br>
  <sub>四套反应力玩法 · REFLEX 主菜单 · 单文件离线运行</sub>
</p>

<h1 align="center">antiBallsheet · 中文四合一</h1>

<p align="center">
  <a href="https://kiryugit.github.io/abs-menu/"><img alt="在线试玩" src="https://img.shields.io/badge/PLAY-%E5%9C%A8%E7%BA%BF%E8%AF%95%E7%8E%A9-22d3ee?style=flat-square"></a>
  <img alt="version" src="https://img.shields.io/badge/version-v0.9.4%20beta-f472b6?style=flat-square">
  <img alt="single file" src="https://img.shields.io/badge/build-single%20HTML-8b5cf6?style=flat-square">
  <img alt="language" src="https://img.shields.io/badge/lang-%E4%B8%AD%E8%8B%B1%E5%8F%8C%E8%AF%AD-38bdf8?style=flat-square">
</p>

> 浏览器里的反应力训练场：速通、生存、舒尔特、反应测试，四套玩法装进一个 HTML。无需安装、无需联网，双击即玩，手机也能用。

这是对 [dphdmn/antiBallsheet](https://github.com/dphdmn/antiBallsheet) 的非官方中文重构版：保留原作的速通规则与成绩系统，并把 [dphdmn/ballsheet](https://github.com/dphdmn/ballsheet) p5 原版的生存规则做成 **BALLSHEET BIGBALLS**；另加舒尔特方格、反应测试、双语、统计、主题、音效和小屏适配。

## 关于这个页面

本 HTML 网页由 AI 编写，目的很直接：把 **antiBallsheet**（速通）、**BALLSHEET BIGBALLS**（生存）、舒尔特方格和反应测试放进同一个打开即玩的页面，省去安装和切换成本；同时把每局成绩留在本机，方便回看趋势、历史记录和 PB。界面、交互和响应式布局也按更清爽、更适合桌面与手机的方向重做。

**在线试玩**：<https://kiryugit.github.io/abs-menu/>

## 为什么是单文件

- **一个 `index.html` 就是完整游戏**：Chart.js、random-js、光标、音效全部内嵌，不依赖 CDN、`node_modules` 或本地服务器。
- **离线可用**：拷到 U 盘、断网、`file://` 双击，行为一致。
- **易部署**：GitHub Pages、Cloudflare Pages、任意静态空间，传上去就能玩。

## 四套玩法

| 模式 | 玩法 | 主要记录 |
| --- | --- | --- |
| **antiBallsheet** | 固定球数，光标触球即得分；在最短时间内接完设定数量的球，没有复杂压力公式 | 总时长、平均 / 最快 / 最慢反应、逐球曲线 |
| **BALLSHEET BIGBALLS** | 100 HP 开局，压力按 `60 × ln(1 + t)` 持续扣血，接球回血；血量归零结束 | 存活时长、吃球数、每秒得分、最高秒得分 |
| **舒尔特方格** | 3×3 – 10×10，14 种规则：顺序、倒序、隐藏、记忆、字母、颜色、Gorbow 等；倒计时支持 0–60000 ms 自定义 | 用时、错误数、每格均时、分尺寸 / 分规则最好 |
| **反应测试** | 点击后才随机等待，默认 1–8 秒，可调 0.5–15 秒；屏幕变绿立即点击，支持 1–100 次，默认 5 次 | 平均、最快 / 最慢单次、有效次数、抢跑次数 |

## 界面

主菜单为四个入口：**01 BALLSHEET**（进入「选一个玩法」：antiBallsheet 速通 / BALLSHEET BIGBALLS 生存）、**02 舒尔特**、**03 反应测试**、**04 灵敏度转换**；右下角固定 **数据 / 设置 / 玩法 / 关于**。桌面为 7:5 满高双栏：左栏标题、菜单与按键提示，右栏为「最近一局」焦点卡、其余模式的三行队列与单行工具 dock；高度不足时自动回退为正常滚动，不会压住页脚。≥1500px 且高度足够时 shell 放宽到 1480，并增加跨模式「最近记录」卡。

hero 顶部为呼吸等化器与 **`REFLEX · LOCAL SESSION`**；下方两枚胶囊按 antiBallsheet → BALLSHEET BIGBALLS → 舒尔特 → 反应测试约每 4.2 秒轮播，显示当前参数与对应 PB，圆点和边框跟随模式色，悬停暂停。

右栏「最近一局」不再固定为单一模式，而是汇总四套存档中时间最新的一局：卡头、指标、PB 单位、差值说明与趋势标题都随模式切换；无记录时才回退 antiBallsheet 配置。焦点卡下方用三行常驻列出其余模式（模式名、最近成绩、PB），不再出现「任何时刻只看到一个模式」的空档；工具入口压成一条四列 dock，短横屏只显示四枚带 `title` 的图标。

| English | 设置 |
| --- | --- |
| <img src="gh-pages/docs/preview-english.png" width="420" alt="English menu"> | <img src="gh-pages/docs/preview-settings.png" width="420" alt="设置页"> |

- **选一个玩法**：两张规则卡分别指向 **BALLSHEET BIGBALLS**（生存，`helloimxtal.github.io/ballsheet/`）与 **antiBallsheet**（速通，`github.com/dphdmn/antiBallsheet`）；卡片顶部的模式标签与右侧来源胶囊都会在新标签打开原作页面，点卡片其余区域进入对应准备页。卡面用大号编号、模式色渐变线、球体与虚线环区分两套规则，短横屏自动切成双列紧凑布局。
- **顶栏 GitHub**：右上角 GitHub 按钮点击后展开下拉菜单，只链接三个原作仓库——`dphdmn/antiBallsheet`、`dphdmn/ballsheet`、`helloimxtal/BallSheetOGL`，不显示本仓库自己的地址。
- **中文 / English**：顶栏 `EN` / `ZH` 一键切换，菜单、设置、HUD、结算、统计、玩法与关于同步换语言。
- **设置集中在一个入口**：主设置只保留辅助 / 外观 / 音效三页；模式规则移到各模式准备页与局内齿轮，不再塞进全局设置。
- **数据留在本机**：四套玩法独立存档，趋势图、历史记录、JSON 导出与清除都在「数据」页。数据页默认是**跨四模式最近流**，按时间倒序、每页 12 局，可切模式筛选并「加载更早」直到全部记录；点任意一条会进入对应**模式详情**并高亮那一局。模式详情保留 PB、均值、走势图与完整历史表（不限 12 条，表内滚动）。主菜单「最近记录」仍单独汇总最近 4 条。
- **外观与音效**：主题色、场地、球色、光标尺寸可调；接球 / 悬停 / 点击三个音效槽位可导入本地音频。

## 操作

| 场景 | 按键 |
| --- | --- |
| 主菜单 | `↑` `↓` 选择，`Enter` 确认，`Esc` 返回 |
| 游戏中 | `R` / `空格` 开始或重开，`Esc` 暂停 |
| 全屏 | `F11` |
| 手机 | 直接点按；暂停与返回使用屏幕按钮 |

## 运行

```bash
git clone https://github.com/Kiryugit/abs-menu.git
cd abs-menu
```

直接双击 `index.html`；或起一个本地静态服务：

```bash
python -m http.server 8000
# http://localhost:8000/
```

## 构建

源码在 `antiBallsheet-menu/`，构建脚本会把引擎、菜单层、玩法、双语与资源拼回根目录的 `index.html`：

```powershell
cd antiBallsheet-menu
node --check src\i18n.js
node --check src\menu.js
node --check src\reaction.js
pwsh -NoProfile -File .\build.ps1
```

构建不需要安装依赖；`gh-pages/` 是可直接发布的同步副本。

## 目录

| 路径 | 说明 |
| --- | --- |
| `index.html` | 构建产物，完整游戏 |
| `antiBallsheet-main/` | 原版引擎、样式与版本脚本（构建输入） |
| `antiBallsheet-menu/` | 中文菜单、四套玩法、i18n 与构建脚本 |
| `gh-pages/` | GitHub Pages 发布副本与 README 预览图 |

更细的源码说明见 [`antiBallsheet-menu/README.md`](antiBallsheet-menu/README.md)；发布版说明与完整更新日志见 [`gh-pages/README.md`](gh-pages/README.md)。

## 部署

`index.html` 不经过构建也能直接运行。GitHub Pages 二选一：

- **根目录发布**：Settings → Pages → Deploy from a branch → `main` / `/(root)`。
- **发布 `gh-pages/`**：Settings → Pages → `main` / `/gh-pages`，该目录已包含完整 `index.html`。

## 来源与致谢

- 原作：[dphdmn/antiBallsheet](https://github.com/dphdmn/antiBallsheet)，基于 [dphdmn/ballsheet](https://github.com/dphdmn/ballsheet/) 的速通改版；速通说明采用其 README 的 “Simple Speedrun Approach” 口径。
- BALLSHEET BIGBALLS 的生存参数与计分取自 [dphdmn/ballsheet](https://github.com/dphdmn/ballsheet/) 的 p5 原版；在线版是 [helloimxtal.github.io/ballsheet](https://helloimxtal.github.io/ballsheet/)（页面标题 “BallSheet Big Balls”），[helloimxtal/BallSheetOGL](https://github.com/helloimxtal/BallSheetOGL) 是该玩法的 C++ OpenGL 重制，本页面只作参数与手感对照，不包含其代码。
- 舒尔特方格参考 [schulte-table.com](https://schulte-table.com/)；反应测试流程参考 [Human Benchmark](https://humanbenchmark.com/tests/reactiontime)。
- 中文菜单、四套玩法的整合、双语层、统计与响应式界面为本仓库新增内容。

原作仓库未附 LICENSE。本仓库是非官方二次创作，未单独声明开源许可；欢迎学习、Fork 与提交 Issue，商用或再分发前请先确认原作者授权。

## 版本

当前 `v0.9.4 (beta)`：hero 标识改为 `REFLEX`，模式与 PB 胶囊升级为四模式轮播；主菜单右栏改为**焦点 + 队列**——最新一局保留大卡与趋势，其余三模式压成三行常驻，数据 / 设置 / 玩法 / 关于收成右下单行 dock；数据页改为**最近流 + 模式详情**双层，最近流跨四模式倒序、可筛选、可加载到全部记录，点记录可跳转并高亮对应历史行，模式详情历史表不再截断；主菜单合并两条 BALLSHEET 规则入口并新增跨模式最近记录；灵敏度页支持目标 DPI 预选与四项指标反推；反应等待范围可调 0.5–15 秒；局内齿轮、旋转与暂停改为 132px 竖排。主菜单 BALLSHEET 副标签改为 **BALLSHEET by dphdmn**；右上角 GitHub 改为点击展开的下拉菜单，只列出三个原作仓库。本轮「选一个玩法」页重做：生存卡命名 **BALLSHEET BIGBALLS** 并链到 `https://helloimxtal.github.io/ballsheet/`，速通卡命名 **antiBallsheet** 并链到 `https://github.com/dphdmn/antiBallsheet`；两卡采用大号编号、模式色渐变线、球体与虚线环的新卡面，点卡片进入准备页，点左上标签打开原作页面；准备页、HUD、结算、数据筛选、右栏队列、帮助与关于同步改用新名称与原作规则口径。

完整版本记录见 [`gh-pages/README.md`](gh-pages/README.md#版本)。
