# 💬 Blip 消息动画
> 💡 **肆说**：让角色消息像视觉小说一样一个字一个字蹦出来+音效，纯装饰功能。

Blip 扩展用可变速度动画显示消息文字，并伴随音效。可使用音频文件或生成声音。

## 前提条件
- 最新版 SillyTavern
- 从"下载扩展和素材"菜单安装 "Blip" 扩展

## 全局设置
1. **Blip user message** - 勾选后对用户消息也播放动画，可设配置文件
2. **Blip only for certain text** - 只对引号内文字播放 / 忽略星号内文字
3. **Automatic scroll down** - 动画时自动滚动，关闭则自由滚动
4. **Audio volume** - 可静音只留动画，或调节全局音量

## 角色动画/语音配置
可保存每个角色的配置文件（包括用户和可选的默认配置）：
- **文字速度**：每字母的毫秒延迟，可设最小/最大速度倍率增加随机感
- **逗号/句号延迟**：特殊字符时暂停，增加生动感
- **音量倍率**：只影响该角色
- **音频速度**：每次 blip 声音间隔，独立于文字速度

### 声音来源
- **Generated sound**：用频率滑块自定义 blip 声音
- **文件**：从列表选音频文件，可从素材菜单获取官方 blip 资源，或放入 `\SillyTavern\data\<user-handle>\assets\blip`

📖 原文链接：[Blip](https://docs.sillytavern.app/extensions/blip/)
