# 激活事件

**激活事件**是`package.json`中`activationEvents`字段声明的一个JSON对象, 参考[插件清单](/references/extension-manifest). 当**激活事件**触发时, 插件就会被激活. 下面是可用的**激活事件**列表:

- [激活事件](#激活事件)
  - [onLanguage](#onlanguage)
  - [onCommand](#oncommand)
  - [onDebug](#ondebug)
    - [onDebugInitialConfigurations](#ondebuginitialconfigurations)
    - [onDebugResolve](#ondebugresolve)
  - [workspaceContains](#workspacecontains)
  - [onFileSystem](#onfilesystem)
  - [onView](#onview)
  - [onUri](#onuri)
  - [onWebviewPanel](#onwebviewpanel)
  - [onCustomEditor](#oncustomeditor)
  - [onAuthenticationRequest](#onauthenticationrequest)
  - [onStartupFinished](#onstartupfinished)
  - [*](#start-up)

`package.json`的配置项都可以在[插件清单](/references/extension-manifest)中找到.

## onLanguage
---

打开特定语言文件时激活事件和相关插件

```json
...
"activationEvents": [
  "onLanguage:python"
]
...
```

`onLanguage`事件需要指定特定的[语言标识符](https://code.visualstudio.com/docs/languages/identifiers)

也可以添加多种语言:

```json
"activationEvents": [
  "onLanguage:json",
  "onLanguage:markdown",
  "onLanguage:typescript"
]
```

## onCommand
---

调用命令时激活

```json
...
"activationEvents": [
  "onCommand:extension.sayHello"
]
...
```

## onDebug
---

调试会话(debug session)启动前激活

```json
...
"activationEvents": [
  "onDebug"
]
...
```

### onDebugInitialConfigurations

### onDebugResolve

这是两个粒度更细的`onDebug`激活事件:

- `DebugConfigurationProvider`中的`provideDebugConfigurations`在`onDebugInitialConfigurations`之后触发
- `onDebugResolve:type`在`DebugConfigurationProvider`的`resolveDebugConfiguration`方法之前触发.

**友情提示**: 如果调试插件比较轻量, 使用`onDebug`. 相反, 根据`DebugConfigurationProvider`实现的对应方法（`provideDebugConfigurations`或`resolveDebugConfiguration`），使用`onDebugInitialConfigurations`或`onDebugResolve`. 参阅[使用调试器插件](/extension-guides/debugger-extension#using-a-debugconfigurationprovider).

## workspaceContains
---

文件夹打开后，且文件夹中至少包含一个符合glob模式的文件时触发.

```json
"activationEvents": [
  "workspaceContains:**/.editorconfig"
]
```

## onFileSystem
---

以协议（scheme）打开文件或文件夹时触发. 通常是`file`-协议，也可以用自定义的文件供应器函数替换掉，比如`ftp`、`ssh`.

```json
...
"activationEvents": [
  "onFileSystem:sftp"
]
...
```

## onView
---

指定id的视图展开时触发:

```json
...
"activationEvents": [
  "onView:nodeDependencies"
]
...
```

## onUri
---

插件的系统级URI打开时触发. 这个URI协议需要带上`vscode`或者 `vscode-insiders`协议. URI主机名必须是插件的唯一标识，剩余的URI是可选的. 

```json
...
"activationEvents": [
  "onUri"
]
...
```

如果`vscode.git`插件定义了`onUri`激活事件，那么下列任意URI打开时就会触发:

- `vscode://vscode.git/init`
- `vscode://vscode.git/clone?url=https%3A%2F%2Fgithub.com%2FMicrosoft%2Fvscode-vsce.git`
- `vscode-insiders://vscode.git/init`(for VS Code Insiders)

## onWebviewPanel
---

当相应`viewType`的`webview`恢复时触发. 

下面是一个例子:

```json
"activationEvents": [
  ...,
  "onWebviewPanel:catCoding"
]
```

VS Code 恢复 (restore) `viewType` 为 `catCoding` 的 webview 时会激活插件. 调用 `window.createWebviewPanel` 可以设置 `viewType`, 你可能会需要其它的激活事件(比如: `onCommand`)初始化你的插件，然后再创建`webview`视图. 

## onCustomEditor
---

当相应 `viewType` 的 [自定义编辑器](../extension-guides/custom-editors.md) 被创建时触发. 


下面是一个例子:
```json
"activationEvents": [
    "onCustomEditor:catCustoms.pawDraw"
]
```

VS Code 恢复 (restore) `viewType` 为 `catCustoms.pawDraw` 的自定义编辑器时会激活插件. 
首先通过 [`自定义编辑器` 的发布内容配置](../extension-guides/custom-editors.md#发布内容配置) 设置 `viewType` ，然后为 `registerCustomEditorProvider` 提供一个 供应器函数. 

!> **注意**: 从VS Code 1.74.0开始，包含自定义编辑器的插件，不再需要单独配置 `onCustomEditor` 事件来激活. 

## onAuthenticationRequest
---

当插件通过 `authentication.getSession()` API和相应的 `providerId` 请求认证会话时会激活插件. 

下面是一个例子：

```json
"activationEvents": [
    "onAuthenticationRequest:github"
]
```

当 VS Code 需要获取类型为 `github` 的 `AuthenticationSession` 将激活插件. 

!> **注意**: 从VS Code 1.74.0开始，包含认证程序的插件，不再需要单独配置 `onAuthenticationRequest` 事件来激活. 

## onStartupFinished
---

VS Code启动一段时间后才会激活插件. 它类似于 `*` 类激活事件，但它不会减慢VS Code启动. 目前，该事件在所有 `*` 类插件激活完成后触发. 

```json
...
"activationEvents": [
    "onStartupFinished"
]
...
```

## Start up
---

当VS Code启动时触发. 为了保证良好的用户体验，只在你的插件没有其他任何激活事件的前提下，添加这个激活事件. 

```json
...
"activationEvents": [
  "*"
]
...
```

!> **注意**: 一个插件如果侦听了多个激活事件, 那么最好用`"*"`替换掉.

!> **注意**: 插件**必须**从它的主模块中输出一个`activate()`函数，当任意的激活事件触发时，VS Code会**仅仅调用一次这个函数**. 此外，插件也**应该** 导出一个`deactivate()`函数，当VS Code关闭时执行清理的任务. 如果清理进程是异步的，插件的`deactivate()`**必须**返回一个Promise. 如果这个清理任务是同步的，那么`deactivate()`可以返回`undefined`. 
