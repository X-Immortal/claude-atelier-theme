# Claude 娘 · 橘花书房视觉设计

## 配色与构图

- **浅色主题（`claude-maid-atelier`）**：采用奶油白、暖橘与焦糖棕。
- **深色主题（`claude-maid-atelier-dark`）**：采用深咖、暖灰与低饱和橘色。
- **场景构图**：背景左侧为坐姿阅读人物，右侧为持书半身人物，两处人物面部均避开中央会话与任务内容列，背景图本身不含窗口、按钮或界面文字。

## 样式分层与引擎关系

主题效果由主题包自身的 Safe CSS 与可选的定制引擎渲染规则共同构成：

1. **主题包层（本仓库 `light/` 与 `dark/`）**
   - 主题 ZIP 包含 `background.png`、`theme.json` 与 `theme.css`。
   - `theme.css` 通过 Dream Skin 公开的 `[data-ds-part]` 选择器控制根容器、侧栏、顶栏、首页、项目列表、消息气泡、输入框及弹窗的底色、边框、圆角与阴影，导入[上游 Codex Dream Skin](https://github.com/Fei-Away/Codex-Dream-Skin) 即可生效。

2. **定制引擎装饰层（[X-Immortal/Codex-Dream-Skin](https://github.com/X-Immortal/Codex-Dream-Skin)）**
   - [`atelier-theme` 分支](https://github.com/X-Immortal/Codex-Dream-Skin/tree/atelier-theme)在 `renderer-inject.js` 中为根元素写入 `data-dream-theme-id`（对应 `claude-maid-atelier` 与 `claude-maid-atelier-dark`），并在共享渲染层 `dream-skin.css` 中追加主题专属规则：
     - 为侧栏绘制书页质感底色、细金线框，以及顶部/底部的橘花与枝叶角饰。
     - 为当前选中的会话绘制书签式高亮状态。
     - 调整输入框边框贴合外框，并改善流式思考与批注展开时的可读性。
   - 装饰层均设置 `pointer-events: none`，不拦截鼠标点击，不增加动画、伪造文案或状态联动。
   - [`atelier-local` 分支](https://github.com/X-Immortal/Codex-Dream-Skin/tree/atelier-local)在此基础上合并了 [`skin-fixes`](https://github.com/X-Immortal/Codex-Dream-Skin/tree/skin-fixes) 中的 Codex 标题栏、底部渐变清除、启动唤醒、弹窗遮挡与附件对比度等兼容修复，并同步构建了 `runtime/`、`windows/assets/` 与 `macos/assets/` 资源。本仓库 [README](../README.md) 中的实机截图均截自该分支。
