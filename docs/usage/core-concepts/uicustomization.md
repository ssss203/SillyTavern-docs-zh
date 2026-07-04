# UI 自定义（UI Customization）
> 💡 **肆说**：这里控制SillyTavern长什么样，纯视觉设置，不影响AI效果。想换主题、调字体大小的来这里。

## UI 主题

### 主题管理

主题文件允许你保存、分享和复用你的 UI 自定义设置。你可以维护多个主题用于不同的心情或目的，并在它们之间即时切换。

- 导入/导出主题文件
- 删除现有主题
- 保存对当前主题的更改
- 另存为新主题

本节中的所有设置都保存到当前主题中。如果你切换主题，设置会被新主题的设置替换。

### 显示设置

这些显示选项影响角色和消息在聊天界面中的呈现方式。

#### 头像样式

在圆形、方形、矩形或圆角方形之间选择。此设置同时应用于用户和 AI 头像。

#### 聊天样式

| 样式 | 说明 | 斜杠命令 |
|---|---|---|
| **扁平（Flat）** | 干净连续的"聊天记录"风格，一个用于 AI 互动的扁平画布。 | `/flat`<br>`/default` |
| **气泡（Bubbles）** | "即时通讯"风格，每条消息有独立的气泡，圆角和微妙的 3D 效果。 | `/bubble`<br>`/bubbles` |
| **文档（Document）** | 紧凑的文档式外观，以文本为中心的布局。隐藏过去消息的头像、时间戳和消息控制按钮。 | `/single`<br>`/story` |

### 通知

设置通知弹窗（Toast Messages）在屏幕上出现的位置。

- 左上
- 居中上（默认）
- 右上
- 左下
- 居中下
- 右下

### 媒体样式

聊天消息中媒体附件（图片、音频、视频）的默认显示样式。向聊天消息追加媒体的扩展可能会覆盖此设置。也可以通过消息上下文菜单中的"切换媒体显示样式"操作手动更改每条消息的设置。

- **列表（List）**：一次性以网格布局显示所有媒体附件。
- **画廊（Gallery）**：以轮播画廊方式显示媒体附件。

此设置还影响内联媒体附件如何发送到支持的聊天补全（Chat Completion）源：列表模式一次发送所有附件，画廊模式发送选中的附件。

### 主题颜色

自定义每个 UI 元素的颜色方案来创建你完美的主题。可以使用颜色选择器选择颜色，适用时包含透明度选项。

- 主要文本
- 斜体文本
- 下划线文本
- 引用文本
- 文本阴影
- 聊天背景
- UI 背景
- UI 边框
- 用户消息
- AI 消息

### 布局与视觉设置

通过这些滑块微调界面的视觉呈现。

- **聊天宽度**：调整聊天窗口宽度（屏幕的 25-100%）
- **字体缩放**：自定义文字大小（0.5-1.5 倍）
- **模糊强度**：控制 UI 面板模糊（0-30）
- **阴影宽度**：调整文字阴影强度（0-5）

### 主题开关

这些开关控制各种 UI 功能和行为。有些选项可以改善低端设备的性能，而其他选项则为聊天界面添加有用的信息或功能。

- **减少动画（Reduced Motion）**：禁用动画和过渡效果
- **无模糊效果（No Blur Effect）**：移除背景模糊以提高性能
- **无文字阴影（No Text Shadows）**：禁用文字阴影效果
- **视觉小说模式（Visual Novel mode）**：带背景精灵图的紧凑聊天
- **展开消息操作（Expand Message Actions）**：始终显示完整的消息上下文菜单
- **禅滑块（Zen Sliders）**：简化的参数控件
- **疯狂实验室模式（Mad Lab Mode）**：不受限制的参数范围
- **消息计时器（Message Timer）**：显示 AI 响应生成时间
- **聊天时间戳（Chat Timestamps）**：显示消息时间戳
- **模型图标（Model Icons）**：为消息显示 AI 模型图标
- **消息 ID（Message IDs）**：显示顺序消息编号
- **隐藏聊天头像（Hide Chat Avatars）**：从聊天中移除头像
- **消息令牌计数（Message Token Count）**：显示每条消息的令牌数
- **紧凑输入区（Compact Input Area）**：单行输入（仅限移动端）
- **所有消息的滑动编号（Swipe # for All Messages）**：在所有消息上显示滑动编号
- **角色热切换（Characters Hotswap）**：收藏角色的快速选择按钮
- **头像悬停放大（Avatar Hover Magnification）**：悬停头像时的缩放效果
- **标签作为文件夹（Tags as Folders）**：使用标签作为文件夹组织角色
> 💡 **肆说**：推荐开这个！开了之后标签会变成文件夹，管理角色卡方便多了。
- **点击编辑（Click to Edit）**：点击消息快速打开消息编辑器

### 自定义 CSS

允许你应用自定义 CSS 样式进一步自定义聊天界面的外观。

使用 **展开** 来展开编辑器窗口以获得更好的可见性和编辑体验。

如果你切换主题，你的自定义 CSS 将被新主题的自定义 CSS 替换。如果你想切换主题时保留自定义 CSS，请确保将其保存到主题中。

如果你使用大量自定义 CSS，或想在多个主题中使用相同的自定义 CSS，非官方的 [CSS Snippets 扩展](https://github.com/LenAnderson/SillyTavern-CssSnippets) 可以帮助你管理和组织自定义 CSS。

## 消息声音

要在收到机器人新消息时播放自定义声音，替换 SillyTavern 文件夹中的以下 MP3 文件：

`public/sounds/message.mp3`

以 80% 音量播放。

如果启用了"仅后台声音（Background Sound Only）"选项，则仅在 SillyTavern 窗口**未聚焦**时播放声音。

## 公式渲染

要启用数学公式渲染，使用 [LaTeX 扩展](https://github.com/SillyTavern/Extension-LaTeX)。要获取该扩展，你需要通过 SillyTavern 中的"下载扩展与资产"菜单安装它。

在带有 `latex` 或 `asciimath` 语言标识符的代码块中输入公式，分别用于 LaTeX 和 AsciiMath。该扩展使用 [KaTeX](https://katex.org/) 进行渲染。

````
```latex
\int_{-\infty}^{\infty} e^{-x^2} dx = \sqrt{\pi}
```

```asciimath
int_{-oo}^{oo} e^{-x^2} dx = sqrt{pi}
```
````

##### 弃用通知

旧式的 `$` 和 `$$` 包装语法不再受支持。请使用以下正则表达式脚本来兼容旧语法：

- [$$ - LaTeX](https://github.com/SillyTavern/Extension-LaTeX/raw/refs/heads/main/assets/$$_-_latex.json)
- [$ - AsciiMath](https://github.com/SillyTavern/Extension-LaTeX/raw/refs/heads/main/assets/$_-_asciimath.json)

---

📖 原文链接：[UI Customization](https://docs.sillytavern.app/usage/core-concepts/uicustomization/)
