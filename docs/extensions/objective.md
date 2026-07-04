# 🎯 目标任务（Objective）
> 💡 **肆说**：可以暂时跳过，知道有就行。等你想给AI设定"任务目标"再来看。

## 这是什么？

Objective 扩展让你为 AI 指定一个聊天中要达成的目标，目标会被分解为逐步任务。任务可以分支，自动或手动创建子任务，形成复杂任务树。任务完成状态会按间隔检查。

与静态提示词不同，它添加了顺序的、有节奏的指令，让 AI 自主争取达成目标，无需用户干预。

## 前提条件
- 最新版 SillyTavern
- 从"下载扩展和素材"菜单安装 "Objective" 扩展

## 配置
1. 在顶部文本框输入目标，点击 `Auto-Generate Tasks`
2. AI 会自动生成任务列表
3. `Position in Chat` - 任务在聊天提示词中的深度（0=AI最关注）
4. `Task Check Frequency` - 每N条消息检查一次任务完成情况

> ⚠️ Task Check Frequency 设为 1 会使 API 调用量翻倍！

## 自定义提示词
可编辑生成任务、检查完成和注入提示词用的提示词，可保存/加载。

## 使用
- 当前任务始终是第一个未完成任务
- **Branch Task** - 将当前任务设为子目标，可继续生成子任务
- 手动勾选完成 / 点红色x删除 / 点+添加任务
- **Hide Tasks** - 隐藏任务列表，让 AI 的意图保持神秘

📖 原文链接：[Objective](https://docs.sillytavern.app/extensions/objective/)
