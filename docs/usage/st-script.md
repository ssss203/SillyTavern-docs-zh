# STscript 脚本语言参考
> 💡 **肆说**：写卡前期不用管，等你想做自动化、小游戏、复杂互动再看。STscript是SillyTavern的"编程语言"。

## 什么是 STscript？

STscript 是一种简单但强大的脚本语言（Scripting Language），可以在不需要正式编程的情况下扩展 SillyTavern 的功能，让你能够：

- 创建小游戏或速通挑战
- 构建AI驱动的聊天洞察工具
- 释放你的创造力并与他人分享

STscript 基于斜杠命令（Slash Commands）引擎构建，利用命令批处理（Command Batching）、数据管道（Data Piping）、宏（Macros）和变量（Variables）等机制。这些概念将在下面的文档中逐一介绍。

### 安全提醒

能力越大，责任越大。执行脚本前请务必仔细检查代码内容。

## 你好，世界！

要运行你的第一个脚本，打开任意 SillyTavern 聊天，在聊天输入栏中输入：

```stscript
/pass Hello, World! | /echo
```

你应该会在屏幕顶部的弹窗通知（Toast）中看到这条消息。现在让我们逐部分拆解：

一个脚本就是一批命令，每个命令以斜杠开头，可以有命名参数（Named Arguments）和未命名参数（Unnamed Arguments），以命令分隔符（Command Separator）`|` 结尾。

命令按顺序执行，一个接一个，并在彼此之间传递数据。

1. `/pass` 命令接收常量值 "Hello, World!" 作为未命名参数，并将其写入管道（Pipe）。
2. `/echo` 命令通过管道接收前一个命令传来的值，并将其显示为弹窗通知。

**提示：** 要查看所有可用命令的列表，在聊天中输入 `/help slash`。

因为常量的未命名参数和管道是可以互换的，我们可以把脚本简化为：

```stscript
/echo Hello, World!
```

## 用户输入

现在让我们给脚本增加一点交互性。我们将从用户那里接受输入值，然后在通知中显示出来。

```stscript
/input Enter your name |
/echo Hello, my name is {{pipe}}
```

1. `/input` 命令用于显示一个输入框，提示文本由未命名参数指定，然后将输出写入管道。
2. 因为 `/echo` 已经有一个未命名参数设置了输出模板，我们使用 `{{pipe}}` 宏来指定管道值的渲染位置。

### 其他输入/输出命令

- `/popup (text)` — 显示一个阻塞弹窗（Blocking Popup），支持简易 HTML 格式，例如：`/popup <font color=red>I'm red!</font>`。
- `/setinput (text)` — 用提供的文本替换用户输入栏的内容。
- `/speak voice="name" (text)` — 使用选定的 TTS（文本转语音，Text-To-Speech）引擎和语音映射中的角色名称来朗读文本，例如 `/speak name="Donald Duck" Quack!`。
- `/buttons labels=["a","b"] (text)` — 显示一个带有指定文本和按钮标签的阻塞弹窗。`labels` 必须是 JSON 序列化的字符串数组或包含此类数组的变量名。返回点击的按钮标签到管道中，如果取消则返回空字符串。文本支持简易 HTML 格式。
- `/beep` — 播放消息通知音。

#### `/popup` 和 `/input` 的参数

`/popup` 和 `/input` 支持以下额外的命名参数：

- `large=on/off` - 增大弹窗的垂直尺寸。默认：`off`。
- `wide=on/off` - 增大弹窗的水平尺寸。默认：`off`。
- `okButton=string` - 自定义"Ok"按钮上的文字。默认：`Ok`。
- `rows=number` - （仅限 `/input`）增大输入控件的大小。默认：1。
- `placeholder=string` - 设置输入字段的占位符文本。
- `tooltip=string` - 设置鼠标悬停时显示的提示文本。
- `icon=string` - 设置弹窗的 Font Awesome 图标类名。

示例：

```stscript
/popup large=on wide=on okButton="Accept" Please accept our terms and conditions....
```

#### `/echo` 的参数

`/echo` 支持以下 `severity` 参数的值来设置显示消息的样式：

- `warning`
- `error`
- `info`（默认）
- `success`

示例：

```stscript
/echo severity=error Something really bad happened.
```

## 变量

变量用于在脚本中存储和操作数据，可以通过命令或宏来使用。变量可以是以下类型之一：

- 本地变量（Local Variables）— 保存到当前聊天的元数据中，对该聊天唯一。
- 全局变量（Global Variables）— 保存到 settings.json 中，在应用中全局存在。

1. `/getvar name` 或 `{{getvar::name}}` — 获取本地变量的值。
2. `/setvar key=name value` 或 `{{setvar::name::value}}` — 设置本地变量的值。
3. `/addvar key=name increment` 或 `{{addvar::name::increment}}` — 给本地变量的值加上增量。
4. `/incvar name` 或 `{{incvar::name}}` — 将本地变量的值加 1。
5. `/decvar name` 或 `{{decvar::name}}` — 将本地变量的值减 1。
6. `/getglobalvar name` 或 `{{getglobalvar::name}}` — 获取全局变量的值。
7. `/setglobalvar key=name` 或 `{{setglobalvar::name::value}}` — 设置全局变量的值。
8. `/addglobalvar key=name` 或 `{{addglobalvar::name:increment}}` — 给全局变量的值加上增量。
9. `/incglobalvar name` 或 `{{incglobalvar::name}}` — 将全局变量的值加 1。
10. `/decglobalvar name` 或 `{{decglobalvar::name}}` — 将全局变量的值减 1。
11. `/flushvar name` — 删除本地变量的值。
12. `/flushglobalvar name` — 删除全局变量的值。

- 之前未定义的变量的默认值是空字符串，或者如果首次在 `/addvar`、`/incvar`、`/decvar` 命令中使用则为零。
- `/addvar` 命令中的增量执行加法或减法（如果增量和变量值都可以转换为数字），否则执行字符串拼接（String Concatenation）。
- 如果命令参数接受变量名，且本地和全局变量存在同名的情况，则*本地变量*优先。
- 所有用于变量操作的*斜杠命令*都会将结果值写入管道供下一个命令使用。
- 对于*宏*，只有"get"、"inc"和"dec"类型的宏会返回值，"add"和"set"会被替换为空字符串。

现在，让我们看以下示例：

```stscript
/input What do you want to generate? |
/setvar key=SDinput |
/echo Requesting an image of {{getvar::SDinput}} |
/getvar SDinput |
/imagine
```

1. 用户输入的值保存在名为 `SDinput` 的本地变量中。
2. 使用 `getvar` 宏在 `/echo` 命令中显示变量的值。
3. 使用 `getvar` 命令检索变量的值并通过管道传递。
4. 值被传递给 `/imagine` 命令（由图片生成插件提供）作为其输入提示。

由于变量在脚本执行之间是保存的且不会被清除，你可以在其他脚本中引用该变量，通过宏也可以解析到相同的值。要确保值被丢弃，请在脚本中添加 `/flushvar` 命令。

### 数组和对象

变量值可以包含 JSON 序列化的数组（Arrays）或键值对对象（Objects）。

示例：

- 数组：`["apple","banana","orange"]`
- 对象：`{"fruits":["apple","banana","orange"]}`

可以对这些命令应用以下修改来处理这些变量：

- `/len` 命令获取数组中的项目数量。
- `index=number/string` 命名参数可以添加到 `/getvar` 或 `/setvar` 及其全局对应命令中，通过零基索引（数组）或字符串键（对象）获取或设置子值。
  - 如果对不存在的变量使用数字索引，变量将被创建为空数组 `[]`。
  - 如果对不存在的变量使用字符串索引，变量将被创建为空对象 `{}`。
- `/addvar` 和 `/addglobalvar` 命令支持向数组类型的变量推入新值。

## 流程控制 - 条件语句

你可以使用 `/if` 命令创建条件表达式，根据定义的规则来分支执行。

```stscript
/if left=valueA right=valueB rule=comparison else={: /echo (command on false) :} {: /echo (command on true) :}
```

注意，以下语法也受支持：

```stscript
/if left=valueA right=valueB rule=comparison else="(command on false)" "(command on true)"
```

不过 `{: 闭包 :}` 可以帮助你写出更整洁的脚本。

让我们看以下示例：

```stscript
/input What's your favorite drink? |
/if left={{pipe}} right="black tea" rule=eq else={: /echo You shall not pass | /abort :} {: /echo Welcome to the club, {{user}} :}
```

这个脚本将用户输入与要求的值进行比较，根据输入值显示不同的消息。

### `/if` 的参数

1. `left` 是第一个操作数。我们称之为 A。
2. `right` 是第二个操作数。我们称之为 B。
3. `rule` 是要应用于操作数的运算。
4. `else` 是可选的子命令字符串，在布尔比较结果为假时执行。
5. 未命名参数是在布尔比较结果为真时执行的子命令。

操作数值按以下顺序评估：

1. 数字字面量（Numeric Literals）
2. 本地变量名
3. 全局变量名
4. 字符串字面量（String Literals）

命名参数的字符串值可以用引号转义以允许多词字符串。引号随后会被去除。

### 布尔运算

支持的布尔比较规则如下。应用于操作数的运算产生真或假值。

1. `eq`（等于）=> A = B
2. `neq`（不等于）=> A != B
3. `lt`（小于）=> A < B
4. `gt`（大于）=> A > B
5. `lte`（小于等于）=> A <= B
6. `gte`（大于等于）=> A >= B
7. `not`（一元取反）=> !A
8. `in`（包含子串）=> A 包含 B，不区分大小写
9. `nin`（不包含子串）=> A 不包含 B，不区分大小写

### 子命令

子命令是包含要执行的斜杠命令列表的字符串。

1. 要在子命令中使用命令批处理，命令分隔符应该被转义（见下文）。
2. 由于宏值是在进入条件时执行的，而不是在子命令执行时，所以宏可以额外转义以延迟其评估到子命令执行时间。
3. 子命令执行的结果通过管道传递给 `/if` 后面的命令。
4. `/abort` 命令在遇到时中断脚本执行。

`/if` 命令可以用作三元运算符（Ternary Operator）。以下示例将在变量 `a` 等于 5 时向下一个命令传递 "true" 字符串，否则传递 "false" 字符串。

```stscript
/if left=a right=5 rule=eq else={: /pass false:} {: /pass true :} |
/echo
```

## 转义序列

### 宏

宏的转义和以前一样工作。不过，有了闭包，你需要转义宏的次数会大大减少。要么转义两个左花括号，要么同时转义左和右花括号对。

```stscript
/echo \{\{char}} |
/echo \{\{char\}\}
```

### 管道符

在闭包中（用作命令分隔符时），管道不需要转义。在任何你想使用字面管道字符而不是命令分隔符的地方，都需要转义它。

```stscript
/echo title="a\|b" c\|d |
/echo title=a\|b c\|d |
```

使用 `STRICT_ESCAPING` 解析器标志（Parser Flag），你不需要转义引号值中的管道。

```stscript
/parser-flag STRICT_ESCAPING |
/echo title="a|b" c\|d |
/echo title=a\|b c\|d |
```

### 引号

要在引号值内使用字面引号字符，必须转义该字符。

```stscript
/echo title="a \"b\" c" d "e" f
```

### 空格

要在命名参数的值中使用空格，你必须用引号包围值，或者转义空格字符。

```stscript
/echo title="a b" c d |
/echo title=a\ b c d
```

### 闭包定界符

如果你想使用标记闭包开头或结尾的字符组合，必须用单个反斜杠转义该序列。

```stscript
/echo \{: |
/echo \:}
```

## 管道断路器

```stscript
||
```

要阻止前一个命令的输出被自动注入为下一个命令的未命名参数，在两个命令之间放置双管道。

```stscript
/echo we don't want to pass this on ||
/world
```

## 闭包

```stscript
{: ... :}
```

闭包（Closures，也叫块语句、Lambda、匿名函数，随便你怎么叫）是用 `{:` 和 `:}` 包裹的一系列命令，只有在代码执行到该部分时才会被评估。

### 子命令

闭包使得使用子命令变得更容易，不再需要转义管道和宏。

```stscript
// 不用闭包的 if |
/if left=1 rule=eq right=1
 else="
 /echo not equal \|
 /return 0
 "
 /echo equal \|
 /return \{\{pipe}}
```

```stscript
// 用闭包的 if |
/if left=1 rule=eq right=1
 else={:
 /echo not equal |
 /return 0
 :}
 {:
 /echo equal |
 /return {{pipe}}
 :}
```

### 作用域

闭包有自己的作用域（Scope）并支持作用域变量（Scoped Variables）。作用域变量用 `/let` 声明，用 `/var` 设置和获取值。获取作用域变量的另一种方式是 `{{var::}}` 宏。

```stscript
/let x |
/let y 2 |
/var x 1 |
/var y |
/echo x is {{var::x}} and y is {{pipe}}.
```

在闭包内部，你可以访问在同一闭包或其祖先闭包中声明的所有变量。你不能访问在闭包后代中声明的变量。

如果变量与在闭包祖先中声明的变量同名，则在该闭包及其后代中无法访问祖先变量。

```stscript
/let x this is root x |
/let y this is root y |
/return {:
 /echo called from level-1: x is "{{var::x}}" and y is "{{var::y}}" |
 /delay 500 |
 /let x this is level-1 x |
 /echo called from level-1: x is "{{var::x}}" and y is "{{var::y}}" |
 /delay 500 |
 /return {:
 /echo called from level-2: x is "{{var::x}}" and y is "{{var::y}}" |
 /let x this is level-2 x |
 /echo called from level-2: x is "{{var::x}}" and y is "{{var::y}}" |
 /delay 500
 :}()
:}() |
/echo called from root: x is "{{var::x}}" and y is "{{var::y}}"
```

### 命名闭包

```stscript
/let x {: ... :} | /:x
```

闭包可以赋值给变量（仅限作用域变量）以便稍后调用或用作子命令。

```stscript
/let myClosure {:
 /echo this is my closure
:} |
/:myClosure
```

```stscript
/let myClosure {:
 /echo this is my closure |
 /delay 500
:} |
/times 3 {{var::myClosure}}
```

`/:` 也可以用来执行快速回复（Quick Replies），它只是 `/run` 的简写。

```stscript
/:QrSetName.QrButtonLabel |
/run QrSetName.QrButtonLabel
```

### 闭包参数

命名闭包可以接受命名参数，就像斜杠命令一样。参数可以有默认值。

```stscript
/let myClosure {: a=1 b=
 /echo a is {{var::a}} and b is {{var::b}}
:} |
/:myClosure b=10
```

### 闭包和管道参数

来自父闭包的管道值不会自动注入到子闭包的第一个命令中。

你仍然可以通过 `{{pipe}}` 显式引用父级的管道值，但如果你让闭包内第一个命令的未命名参数留空，值将*不会*被自动注入。

```stscript
/* 这以前会尝试将模型更改为 "foo"
 因为 /echo 外部的值 "foo" 被注入到了循环内部的
 /model 命令中。
 现在它只会简单地回显当前模型而不会
 尝试更改它。
*|
/echo foo |
/times 2 {:
	/model |
	/echo |
:} |
```

```stscript
/* 你仍然可以通过显式使用 {{pipe}} 宏
 来重新创建旧行为。
*|
/echo foo |
/times 2 {:
	/model {{pipe}} |
	/echo |
:} |
```

### 立即执行的闭包

```stscript
{: ... :}()
```

闭包可以立即执行，这意味着它们会被其返回值替换。这在没有显式闭包支持的地方很有用，也可以缩短一些本来需要大量中间变量的命令。

```stscript
// 不用闭包的简单字符串长度比较 |
/len foo |
/var lenOfFoo {{pipe}} |
/len bar |
/var lenOfBar {{pipe}} |
/if left={{var::lenOfFoo}} rule=eq right={{var:lenOfBar}} /echo yay!
```

```stscript
// 用立即执行闭包的相同比较 |
/if left={:/len foo:}() rule=eq right={:/len bar:}() /echo yay!
```

除了运行保存在作用域变量中的命名闭包外，`/run` 命令也可以用于立即执行闭包。

```stscript
/run {:
	/add 1 2 3 4 |
:} |
/echo |
```

## 注释

```stscript
// ... | /# ...
```

注释（Comment）是脚本代码中的人类可读解释或标注。注释不会断开管道。

```stscript
// this is a comment |
/echo foo |
/# this is also a comment
```

### 块注释

块注释（Block Comments）可以用来一次性注释掉多个命令。它们不会在管道上终止。

```stscript
/echo foo |
/*
/echo bar |
/echo foobar |
*|
/echo foo again |
```

## 流程控制

### 循环：`/while` 和 `/times`

如果你需要循环运行某个命令直到满足某个条件，使用 `/while` 命令。

```stscript
/while left=valueA right=valueB rule=operation guard=on "commands"
```

在循环的每一步，它比较变量 A 的值与变量 B 的值，如果条件为真，则执行引号中包含的任何有效斜杠命令，否则退出循环。此命令不会向输出管道写入任何内容。

#### `/while` 的参数

**可用的布尔比较集合、变量处理、字面值和子命令与 `/if` 命令相同。**

可选的 `guard` 命名参数（默认为 `on`）用于防止无限循环，将迭代次数限制为 100。要禁用并允许无限循环，设置 `guard=off`。

此示例将 1 加到变量 `i` 的值上直到它达到 10，然后输出结果值（本例中为 10）。

```stscript
/setvar key=i 0 |
/while left=i right=10 rule=lt "/addvar key=i 1" |
/echo {{getvar::i}} |
/flushvar i
```

#### `/times` 的参数

将子命令运行指定次数。

`/times (repeats) "(command)"` — 引号中的任何有效斜杠命令重复指定次数，例如 `/setvar key=i 1 | /times 5 "/addvar key=i 1"` 将 1 加到变量 "i" 的值上 5 次。

- `{{timesIndex}}` 被替换为迭代编号（从零开始），例如 `/times 4 {:/echo {{timesIndex}}:}` 回显数字 0 到 3。
- 循环默认限制为 100 次迭代，传入 `guard=off` 可禁用。

### 跳出循环和闭包

```stscript
/break |
```

`/break` 命令可用于提前跳出循环（`/while` 或 `/times`）或闭包。`/break` 的未命名参数可用于传递与当前管道不同的值。

`/break` 目前在以下命令中实现：

- `/while` - 提前退出循环
- `/times` - 提前退出循环
- `/run`（带有闭包或通过变量的闭包）- 提前退出闭包
- `/:`（带有闭包）- 提前退出闭包

```stscript
/times 10 {:
	/echo {{timesIndex}}
	/delay 500 |
	/if left={{timesIndex}} rule=gt right=3 {:
		/break
	:} |
:} |
```

```stscript
/let x {: iterations=2
	/if left={{var::iterations}} rule=gt right=10 {:
		/break too many iterations! |
	:} |
	/times {{var::iterations}} {:
		/delay 500 |
		/echo {{timesIndex}} |
	:} |
:} |
/:x iterations=30 |
/echo the final result is: {{pipe}}
```

```stscript
/run {:
	/break 1 |
	/pass 2 |
:} |
/echo pipe will be one: {{pipe}} |
```

```stscript
/let x {:
	/break 1 |
	/pass 2 |
:} |
/:x |
/echo pipe will be one: {{pipe}} |
```

## 数学运算

- 以下所有运算都接受一系列数字或变量名，并将结果输出到管道。
- 无效运算（如除以零）以及产生 NaN（非数字）值或无穷大的运算返回零。
- 乘法、加法、最小值和最大值接受无限数量的空格分隔参数。
- 减法、除法、指数和取模接受两个空格分隔的参数。
- 正弦、余弦、自然对数、平方根、绝对值和四舍五入接受一个参数。

**运算列表：**

1. `/add (a b c d)` – 执行一组值的加法，例如 `/add 10 i 30 j`
2. `/mul (a b c d)` – 执行一组值的乘法，例如 `/mul 10 i 30 j`
3. `/max (a b c d)` – 返回一组值中的最大值，例如 `/max 1 0 4 k`
4. `/min (a b c d)` – 返回一组值中的最小值，例如 `/min 5 4 i 2`
5. `/sub (a b)` – 执行两个值的减法，例如 `/sub i 5`
6. `/div (a b)` – 执行两个值的除法，例如 `/div 10 i`
7. `/mod (a b)` – 执行两个值的取模运算（Modulo），例如 `/mod i 2`
8. `/pow (a b)` – 执行两个值的幂运算（Exponentiation），例如 `/pow i 2`
9. `/sin (a)` – 执行一个值的正弦运算，例如 `/sin i`
10. `/cos (a)` – 执行一个值的余弦运算，例如 `/cos i`
11. `/log (a)` – 执行一个值的自然对数运算，例如 `/log i`
12. `/abs (a)` – 执行一个值的绝对值运算，例如 `/abs -10`
13. `/sqrt (a)` – 执行一个值的平方根运算，例如 `/sqrt 9`
14. `/round (a)` – 执行一个值的四舍五入到最近整数运算，例如 `/round 3.14`
15. `/rand (round=round|ceil|floor from=number=0 to=number=1)` – 返回 from 和 to 之间的随机数，例如 `/rand` 或 `/rand 10` 或 `/rand from=5 to=10`。范围包含端点。返回值将包含小数部分。使用 `round` 命名参数获取整数值，例如 `/rand round=ceil` 向上取整，`round=floor` 向下取整，`round=round` 四舍五入。

### 示例 1：获取半径为 50 的圆的面积

```stscript
/setglobalvar key=PI 3.1415 |
/setvar key=r 50 |
/mul r r PI |
/setvar key=area |
/echo Area is approximately {{getvar::area}} |
/flushvar r |
/flushvar area
```

## LLM 交互

### 生成回复

- `/gen (trigger)` – 从 LLM 生成回复。如果提供触发器，它会作为用户消息添加到提示中。
- `/trigger` – 生成下一个 AI 回复而不发送用户消息（等同于按"继续"按钮）。
- `/continue` – 继续上一个 AI 回复。
- `/regenerate` – 重新生成最后一个 AI 回复。
- `/impersonate` – 让 AI 代表用户生成一条消息。
- `/swipe (direction)` – 在备选回复之间切换。方向：0 = 下一个，-1 = 上一个。示例：`/swipe 0`。
- `/model (name)` – 切换当前活动的 AI 模型。示例：`/model gpt-4`。
- `/sysgen (text)` – 以系统消息的形式生成回复。

### 消息访问

- `/getlastmessage` – 获取聊天中的最后一条消息。
- `/getlastmessageid` – 获取聊天中最后一条消息的索引。
- `/del (index)` – 按索引删除消息。索引 0 = 最旧。`-1` = 最新的用户消息，`-2` = 最新的 AI 消息。示例：`/del 0`。
- `/delrange start end` – 删除从 start 到 end（含）范围的消息。示例：`/delrange 0 5`。
- `/delprev` – 删除上一条消息。
- `/delswipe` – 删除当前滑动（Swipe）。
- `/movechat` – 将当前聊天移动到另一个角色。

## 文本操作

- `/len (text)` – 返回文本的字符长度。
- `/trimtokens` – 从文本中修剪令牌（Tokens）。
- `/trimlines` – 从文本中修剪行。
- `/replace old new (text)` – 在文本中替换字符串。
- `/replacerex pattern replacement (text)` – 使用正则表达式在文本中替换。
- `/substring start end (text)` – 获取文本的子串。
- `/lower (text)` – 将文本转为小写。
- `/upper (text)` – 将文本转为大写。
- `/split separator (text)` – 按分隔符拆分文本。
- `/join separator (array)` – 用分隔符连接数组。

## Quick Replies 配置

Quick Replies（快速回复）是可自定义的按钮，点击时可以运行斜杠命令或 STscript。

- `/run (name)` – 执行一个 Quick Reply，例如 `/run MyQR.QRButton`。
- `/qrCreate (name) (text)` – 创建一个新的 Quick Reply。
- `/qrDelete (name)` – 删除一个 Quick Reply。
- `/qrSet (name) (text)` – 修改现有的 Quick Reply。
- `/qrList` – 列出所有 Quick Replies。

## 解析器标志

解析器标志（Parser Flags）影响 STscript 的解析方式。

- `/parser-flag (flag)` – 设置解析器标志。示例：`/parser-flag STRICT_ESCAPING`

### STRICT_ESCAPING

启用后：
- 引号值中的管道不需要转义。
- 符号前的反斜杠可以转义以提供字面反斜杠后跟功能符号。

### REPLACE_GETVAR

有助于避免当变量值包含可能被解释为宏的文本时发生双重替换。

## 延迟

- `/delay (ms)` – 暂停脚本执行指定的毫秒数。
- `/delay-async (ms)` – 异步暂停脚本执行，不阻塞其他操作。

---

📖 原文链接：[STscript Language Reference](https://docs.sillytavern.app/usage/st-script/)
