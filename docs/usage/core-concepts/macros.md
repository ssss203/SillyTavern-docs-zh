# 宏（Macros）
> 💡 **肆说**：宏是SillyTavern的"魔法变量"，写角色卡和世界信息时会大量用到。至少记住 {{user}}、{{char}} 这两个。

宏是 SillyTavern 中一种强大的模板机制，可以在提示词、角色卡、世界信息等地方使用特殊占位符来自动替换为相应的值。

## 查找可用宏

在聊天中输入 `/? macros` 可以查看完整的可用宏列表及其详细说明。

## 宏自动补全

SillyTavern 提供了宏的自动补全功能。在输入 `{{` 后会自动弹出可用宏的列表，方便你快速选择。

## 基本语法
> 💡 **肆说**：用双花括号包围就行，最常用的就是 {{user}}（你的名字）和 {{char}}（角色名字）。写角色卡时用这些代替硬编码名字。

宏使用双花括号包围：`{{macro_name}}`

示例：
- `{{user}}` — 当前用户/人格的名字
- `{{char}}` — 当前角色名
- `{{time}}` — 当前本地时间

## 参数

### 空格分隔符

某些宏使用空格来分隔参数：

```
{{setvar::name::value}}
```

### 双冒号分隔符

大多数宏使用双冒号 `::` 来分隔参数：

```
{{getvar::variable_name}}
{{addvar::variable_name::10}}
```

### 单冒号分隔符（旧式）

一些旧式宏使用单冒号 `:` 来分隔参数，这种写法已不推荐使用：

```
{{getvar:variable_name}}
```

### 宏定义中的空白

宏定义中参数之间的空白会被忽略，所以以下写法等价：

```
{{setvar::name::value}}
{{setvar :: name :: value}}
```

## 嵌套宏
> 💡 **肆说**：宏可以套宏！比如 {{getvar::{{user}}_score}} 能根据玩家名字获取不同变量，做复杂互动很有用。

宏可以嵌套使用，即一个宏的值中可以包含另一个宏：

```
{{getvar::{{user}}_score}}
```

## 作用域宏

作用域宏只在当前闭包（Closure）作用域内有效：

```
{{var::variable_name}}
```

### 作用域语法

使用 `var::` 前缀来访问作用域变量：

```
/let myVar hello |
/echo {{var::myVar}}
```

### 示例

```
/let name {{user}} |
/echo Hello, {{var::name}}!
```

## 内容裁剪

宏的输出可以通过 `|` 管道符和裁剪命令来处理：

- `{{trim::text}}` — 去除文本两端的换行
- `{{trimlines::text}}` — 去除每行两端的空白

## 条件宏
> 💡 **肆说**：条件宏可以让角色卡"智能"——根据不同情况显示不同内容。进阶写卡必学。

### 简单条件

```
{{if condition}}text{{/if}}
```

当条件为真时显示文本。

### 在条件中使用变量简写

```
{{if {{.score > 50}}}}High score!{{/if}}
```

### 反转条件

```
{{if! condition}}text{{/if}}
```

当条件为假时显示文本。

### If/Else 分支

```
{{if condition}}true text{{else}}false text{{/if}}
```

## 宏标志

### 语法

宏标志是添加在宏名称前的特殊标记，用于修改宏的行为。

### 已实现的标志

| 标志 | 说明 |
|---|---|
| `|s|` | 保留空白（Preserve Whitespace）— 不裁剪宏输出中的空白 |
| `|c|` | 抑制错误（Suppress Errors）— 如果宏求值失败，不显示错误 |

### 计划中的标志（尚未实现）

- 更多标志正在规划中

### 类标志前缀运算符

以下前缀运算符不是宏标志，而是变量简写的指示器：

| 前缀 | 名称 | 说明 | 示例 |
|---|---|---|---|
| `.` | 本地变量 | 本地变量操作的简写 | `{{.myvar}}` |
| `$` | 全局变量 | 全局变量操作的简写 | `{{$myvar}}` |

这些前缀运算符必须放在变量名**紧前面**，在可能出现的宏标志之后。它们不被视为宏标志，而是指示正在插入变量简写而非按名称调用的宏。前缀运算符不是变量名本身的一部分，而是改变变量访问方式的修饰符。

### 保留空白标志

```
{{|s| macro_name}}
```

防止宏输出中的空白被裁剪。

### 注释

```
{{# this is a comment}}
```

注释宏不会被替换为任何内容。

## 转义宏

要输出字面的 `{{` 而不被解释为宏，使用反斜杠转义：

```
\{\{char}}
```

或者转义整对花括号：

```
\{\{char\}\}
```

## 变量简写

变量简写（Variable Shorthands）提供了一种简洁的方式来操作变量。

### 变量简写前缀

| 前缀 | 名称 | 说明 | 示例 |
|---|---|---|---|
| `.` | 本地变量 | 本地变量操作的简写 | `{{.myvar}}` |
| `$` | 全局变量 | 全局变量操作的简写 | `{{$myvar}}` |

### 变量名

变量名遵循与宏标识符相同的规则：以字母开头，后跟字母、数字、下划线或连字符。最后一个字符不允许是下划线或连字符。

```
{{.my-var}} // 有效
{{.my_var}} // 有效
{{.myVar123}} // 有效
```

如果你的变量标识符不符合标准规则，你必须使用完整的变量宏语法（例如 `{{getvar::my§var----}}`），或者重命名/移动你的变量值。

### 值中的嵌套宏

变量值可以包含嵌套宏：

```
{{.greeting = Hello, {{user}}!}}
```

解析为一个变量，保存了 `Hello, User!`（如果 `{{user}}` 的名字是 "User"）。

### 空白处理

运算符周围的空白是允许的：

```
{{ .myvar = spaced value }}
{{ .counter ++ }}
```

### 变量简写运算符

以下运算符可以与变量简写一起使用。每个运算符遵循 `{{.varName operator value}}` 或 `{{$varName operator value}}` 的模式。

| 运算符 | 名称 | 示例 | 说明 |
|---|---|---|---|
| *(无)* | 获取 | `{{.myvar}}` | 返回变量值 |
| `=` | 设置 | `{{.myvar = value}}` | 将变量设为值，不返回任何内容 |
| `++` | 递增 | `{{.counter++}}` | 加 1，返回新值 |
| `--` | 递减 | `{{.counter--}}` | 减 1，返回新值 |
| `+=` | 加 | `{{.score += 10}}` | 加到变量上（数字或字符串拼接），不返回任何内容 |
| `-=` | 减 | `{{.health -= 5}}` | 从变量中减去（仅数字），不返回任何内容 |
| `\|\|` | 逻辑或 | `{{.name \|\| Guest}}` | 如果变量为假值则返回回退值 |
| `??` | 空值合并 | `{{.name ?? Guest}}` | 仅当变量未定义时返回回退值 |
| `\|\|=` | 逻辑或赋值 | `{{.name \|\|= Guest}}` | 如果变量为假值则设置，返回新值 |
| `??=` | 空值合并赋值 | `{{.name ??= Guest}}` | 仅当变量未定义时设置，返回新值 |
| `==` | 等于 | `{{.status == active}}` | 比较值，返回 `"true"` 或 `"false"` |
| `!=` | 不等于 | `{{.status != active}}` | 如果不等于则返回 `"true"` |
| `>` | 大于 | `{{.score > 50}}` | 如果变量大于值则返回 `"true"` |
| `>=` | 大于等于 | `{{.level >= 10}}` | 如果变量大于等于值则返回 `"true"` |
| `<` | 小于 | `{{.health < 20}}` | 如果变量小于值则返回 `"true"` |
| `<=` | 小于等于 | `{{.health <= 0}}` | 如果变量小于等于值则返回 `"true"` |

## 旧式语法
> 💡 **肆说**：老格式 <USER> <BOT> 还能用但别再用了，新内容都用 {{user}} {{char}}。

为了向后兼容，仍然支持尖括号标记：

| 旧式 | 等效宏 |
|---|---|
| `<USER>` | `{{user}}` |
| `<BOT>` | `{{char}}` |
| `<CHAR>` | `{{char}}` |
| `<GROUP>` | `{{group}}` |
| `<CHARIFNOTGROUP>` | `{{charIfNotGroup}}` |

这些会在处理时自动转换为对应的宏。

**注意：** 不推荐使用旧式语法。请在新内容中使用等效的 `{{macro}}` 语法。

## 按类别列出的常用宏

使用 `/? macros` 可以获取可用宏的完整列表和详细说明。

### 名称与参与者

| 宏 | 说明 |
|---|---|
| `{{user}}` | 当前用户/人格名 |
| `{{char}}` | 当前角色名 |
| `{{group}}` | 逗号分隔的群组成员名列表（含静音成员），或单人聊天中的角色名 |
| `{{groupNotMuted}}` | 逗号分隔的群组成员名列表（不含静音成员） |
| `{{charIfNotGroup}}` | 角色名（群组中为空） |
| `{{notChar}}` | 除当前说话者外所有参与者的逗号分隔列表 |

### 角色卡与人格字段

| 宏 | 说明 |
|---|---|
| `{{description}}` | 角色描述 |
| `{{personality}}` | 角色性格 |
| `{{scenario}}` | 角色场景 |
| `{{persona}}` | 用户人格描述 |
| `{{charPrompt}}` | 角色的主提示词覆盖 |
| `{{charInstruction}}` | 角色的历史后指令覆盖 |
| `{{charDepthPrompt}}` | 角色的深度注释（@ Depth Note） |
| `{{charCreatorNotes}}` | 角色卡中的创建者备注 |
| `{{charVersion}}` | 角色的版本号 |
| `{{mesExamples}}` | 角色的对话示例，格式化为指令模式 |
| `{{mesExamplesRaw}}` | 角色卡中未格式化的对话示例 |
| `{{charFirstMessage}}` | 角色的第一条消息（问候语）。接受可选索引用于替代问候语，例如 `{{charFirstMessage::1}}` |
| `{{original}}` | 角色提示词覆盖中用于替换的原始消息内容 |

### 聊天历史与消息

| 宏 | 说明 |
|---|---|
| `{{lastMessage}}` | 聊天中的最后一条消息 |
| `{{lastMessageId}}` | 聊天中最后一条消息的索引 |
| `{{lastUserMessage}}` | 聊天中最后的用户消息 |
| `{{lastCharMessage}}` | 聊天中最后的角色/机器人消息 |
| `{{firstIncludedMessageId}}` | 当前上下文中包含的第一条消息的索引 |
| `{{firstDisplayedMessageId}}` | 聊天中显示的第一条消息的索引 |
| `{{lastSwipeId}}` | 最后一条消息的最后一次滑动的 1 基索引 |
| `{{currentSwipeId}}` | 当前滑动的 1 基索引 |
| `{{allChatRange}}` | 提供整个聊天的范围（例如 `0-{{lastMessageId}}`） |
| `{{summary}}` | 来自"摘要"扩展的最新聊天摘要（可用时） |

### 时间与日期

| 宏 | 说明 |
|---|---|
| `{{time}}` | 当前本地时间 |
| `{{time::UTC±(offset)}}` | 带 UTC 偏移的时间 |
| `{{date}}` | 当前本地日期（短格式） |
| `{{weekday}}` | 当前星期几 |
| `{{isotime}}` | 当前时间（HH:mm 格式） |
| `{{isodate}}` | 当前日期（YYYY-MM-DD 格式） |
| `{{datetimeformat::format}}` | 自定义格式的日期/时间（例如 `YYYY-MM-DD HH:mm:ss`） |
| `{{idleDuration}}` | 自上次用户消息以来的人类可读持续时间 |
| `{{timeDiff::left::right}}` | 两个时间之间的人类可读差值 |

### 变量

| 宏 | 说明 |
|---|---|
| `{{getvar::name}}` | 获取本地变量值 |
| `{{setvar::name::value}}` | 设置本地变量 |
| `{{addvar::name::value}}` | 向本地变量增加值（数字或字符串拼接） |
| `{{incvar::name}}` | 本地变量加 1 并返回新值 |
| `{{decvar::name}}` | 本地变量减 1 并返回新值 |
| `{{hasvar::name}}` | 检查本地变量是否存在（返回 "true" 或 "false"） |
| `{{deletevar::name}}` | 删除本地变量 |
| `{{getglobalvar::name}}` | 获取全局变量值 |
| `{{setglobalvar::name::value}}` | 设置全局变量 |
| `{{addglobalvar::name::value}}` | 向全局变量增加值 |
| `{{incglobalvar::name}}` | 全局变量加 1 并返回新值 |
| `{{decglobalvar::name}}` | 全局变量减 1 并返回新值 |
| `{{hasglobalvar::name}}` | 检查全局变量是否存在 |
| `{{deleteglobalvar::name}}` | 删除全局变量 |

### 随机化

| 宏 | 说明 |
|---|---|
| `{{random::a::b::c}}` | 随机选择（每次重新随机） |
| `{{pick::a::b::c}}` | 稳定的随机选择（每个聊天和位置一致）。可以用 `/reroll-pick` 命令重新随机 |
| `{{roll::1d20}}` | 使用 droll 语法的骰子投掷 |

### 运行时状态

| 宏 | 说明 |
|---|---|
| `{{maxPrompt}}` | 最大提示词上下文大小（提示词令牌数 = 上下文令牌数 - 响应令牌数） |
| `{{maxContextTokens}}` | 当前生成设置的最大上下文令牌数 |
| `{{maxResponseTokens}}` | 当前生成设置的最大响应令牌数 |
| `{{model}}` | 当前选择的 API 模型名称 |
| `{{isMobile}}` | 如果在移动环境中运行则为 "true"，否则为 "false" |
| `{{lastGenerationType}}` | 最后排队的生成请求类型（如 "normal"、"impersonate"、"regenerate"、"quiet"、"swipe"、"continue"） |
| `{{hasExtension::name}}` | 检查扩展是否激活（返回 "true" 或 "false"）。按扩展名匹配，不区分大小写 |

### 提示词模板

| 宏 | 说明 |
|---|---|
| `{{systemPrompt}}` | 活动的系统提示词文本（可被角色覆盖） |
| `{{defaultSystemPrompt}}` | 默认系统提示词 |
| `{{authorsNote}}` | 作者备注的内容 |
| `{{charAuthorsNote}}` | 角色作者备注的内容 |
| `{{defaultAuthorsNote}}` | 默认作者备注的内容 |
| `{{instructStoryStringPrefix}}` | 指令故事字符串前缀 |
| `{{instructStoryStringSuffix}}` | 指令故事字符串后缀 |
| `{{instructUserPrefix}}` | 指令输入/用户前缀序列 |
| `{{instructUserSuffix}}` | 指令输入/用户后缀序列 |
| `{{instructAssistantPrefix}}` | 指令输出/助手前缀序列 |
| `{{instructAssistantSuffix}}` | 指令输出/助手后缀序列 |
| `{{instructSeparator}}` | 指令分隔序列 |
| `{{instructSystemPrefix}}` | 指令系统前缀序列 |
| `{{instructSystemSuffix}}` | 指令系统后缀序列 |
| `{{instructFirstAssistantPrefix}}` | 指令第一个助手/输出前缀序列 |
| `{{instructLastAssistantPrefix}}` | 指令最后一个助手/输出前缀序列 |
| `{{instructFirstUserPrefix}}` | 指令第一个用户/输入前缀序列 |
| `{{instructLastUserPrefix}}` | 指令最后一个用户/输入前缀序列 |
| `{{instructStop}}` | 指令停止序列 |
| `{{instructUserFiller}}` | 指令用户对齐填充 |
| `{{instructSystemInstructionPrefix}}` | 指令系统指令前缀序列 |
| `{{chatSeparator}}` | 文本补全提示词中示例聊天块之间的分隔符 |
| `{{chatStart}}` | 文本补全提示词中的聊天开始标记 |
| `{{reasoningPrefix}}` | 推理块之前使用的前缀字符串 |
| `{{reasoningSuffix}}` | 推理块之后使用的后缀字符串 |
| `{{reasoningSeparator}}` | 内容和响应之间的分隔符 |
| `{{charPrefix}}` | 角色的正面图片生成提示词前缀 |
| `{{charNegativePrefix}}` | 角色的负面图片生成提示词前缀 |

### 实用工具

| 宏 | 说明 |
|---|---|
| `{{newline}}` | 插入换行符 |
| `{{newline::count}}` | 插入多个换行符 |
| `{{space}}` | 插入空格字符 |
| `{{space::count}}` | 插入多个空格 |
| `{{noop}}` | 什么也不做，产生空字符串 |
| `{{trim}}` | 去除周围的换行 |
| `{{reverse::text}}` | 反转字符串 |
| `{{input}}` | 当前聊天输入字段内容 |
| `{{banned::word}}` | 为文本补全后端禁止一个词 |
| `{{outlet::key}}` | 返回给定出口键的世界信息出口提示词 |

---

📖 原文链接：[Macros](https://docs.sillytavern.app/usage/core-concepts/macros/)
