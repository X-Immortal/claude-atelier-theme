# Claude 娘 · 橘花书房视觉设计

## 配色与构图

- **浅色主题（`claude-maid-atelier`）**：采用奶油白、暖橘与焦糖棕。
- **深色主题（`claude-maid-atelier-dark`）**：采用深咖、暖灰与低饱和橘色。
- **场景构图**：背景左侧为坐姿阅读人物，右侧为持书半身人物，两处人物面部均避开中央会话与任务内容列，背景图本身不含窗口、按钮或界面文字。

## 样式结构

- **主题包内样式（`light/` 与 `dark/`）**：主题 ZIP 包含 `background.png`、`theme.json` 与 `theme.css`。`theme.css` 基于 [Codex Dream Skin](https://github.com/Fei-Away/Codex-Dream-Skin) 的 `[data-ds-part]` 选择器设置根容器、侧栏、顶栏、首页、项目列表、消息气泡、输入框与弹窗的底色、边框、圆角和阴影。
- **可选渲染层装饰**：个人渲染层 fork（[X-Immortal/Codex-Dream-Skin](https://github.com/X-Immortal/Codex-Dream-Skin)）的 [`atelier-theme`](https://github.com/X-Immortal/Codex-Dream-Skin/tree/atelier-theme) 分支在 `renderer-inject.js` 写入 `data-dream-theme-id` 标识，并在共享渲染层 `dream-skin.css` 中为本主题追加侧栏书页底色、细金线框、顶部与底部橘花及角饰、书签式会话选中态和输入框花边。装饰层设置 `pointer-events: none`，并在窗口宽度不超过 1000px 时收起场景图。[README](../README.md) 中的实机截图运行于合并了日常兼容补丁的 [`atelier-local`](https://github.com/X-Immortal/Codex-Dream-Skin/tree/atelier-local) 分支。
