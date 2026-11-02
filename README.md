# Remotion Skills for ZCode

一个 [ZCode](https://z.ai) 插件：把 [Remotion](https://www.remotion.dev/)（用 React 写代码做视频的框架）的最佳实践技能库打包成 Agent Skill，供 ZCode 中的 AI 代理在编写 Remotion 代码时自动参考。

技能内容为中文版，源自 [buainoai/remotion-skills](https://github.com/buainoai/remotion-skills)，其原始出处为 [remotion-dev/skills](https://github.com/remotion-dev/skills)。

## 安装

在 ZCode 中：**Plugin Marketplace → Add → Add Plugin Marketplace**，添加本仓库：

```
https://github.com/APX103/remotion-zcode
```

然后在 **Personal → remotion-zcode → Remotion Skills → Install** 安装。

安装后，当你在对话中处理 Remotion 项目（写动画、嵌视频/音频、做字幕、3D、图表、转场等）时，从 composer 的技能选择器中选用 **remotion-best-practices**（或直接描述 Remotion 任务，由代理自动触发）。

## 技能覆盖范围（30+ 规则）

| 分类 | 内容 |
| --- | --- |
| 核心概念 | 动画、组合（Composition）、时序插值（线性/缓动/弹簧）、序列编排 |
| 媒体处理 | 图像、视频、音频、GIF、资源导入 |
| 高级功能 | Three.js 3D、字幕显示（TikTok 风格高亮）、SRT 导入、音频转录、Lottie、图表、Mapbox 地图 |
| 文本排版 | Google/本地字体、文本动画、文本测量、DOM 节点测量 |
| 视频工具 | Mediabunny 提取帧、取时长/尺寸、解码检查 |
| 配置优化 | Zod 参数化、动态元数据、TailwindCSS、透明视频、修剪、场景转场 |

核心原则：一切动画由 `useCurrentFrame()` 驱动；禁止 CSS 过渡/动画与 Tailwind 动画类名（它们无法正确渲染）；动画以秒为单位书写并乘以 `useVideoConfig()` 的 `fps`。

## 仓库结构

```
remotion-zcode/
├── .claude-plugin/marketplace.json   # 市场元数据（根目录另有一份副本）
├── marketplace.json
├── NOTICE                            # 上游来源与许可说明
└── remotion-skills/                  # 插件本体
    ├── .zcode-plugin/plugin.json     # 插件清单
    └── skills/remotion/
        ├── SKILL.md                  # 技能入口与索引
        └── rules/                    # 30+ 条最佳实践规则（含 .tsx 示例）
```

## 本地开发 / 测试

将本仓库克隆到本地后，在 ZCode 中把本地目录添加为 Marketplace（粘贴仓库根目录路径）即可安装测试。修改 `remotion-skills/` 下的文件后，在 **Settings → Plugins** 中更新该插件即可生效。

## 致谢与许可

- 技能内容来自 [buainoai/remotion-skills](https://github.com/buainoai/remotion-skills)（中文版），原始出处 [remotion-dev/skills](https://github.com/remotion-dev/skills)。
- 详见 [NOTICE](NOTICE)。Remotion 框架本身采用其自身的源码可得许可证，见 [remotion.pro](https://www.remotion.pro/)。
