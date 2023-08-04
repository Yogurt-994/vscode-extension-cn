# 插件指南

通过[Hello World](/get-started/your-first-extension)学习过基本的VS Code插件API之后，现在是时间搞搞真正的插件了。在[插件功能](/extension-capabilities/README)章节，在更宽泛的层面上介绍了插件**能做**些什么，本章则细化了各个功能点，并提供了**详细的代码**和VS Code API的解释。

在每个指南-示例组合中，你将会看到：
- 贯穿整个代码的注释
- 使用示例插件的gif或者图片
- 运行示例插件指引
- 使用过的VS Code API列表
- 使用过的配置点列表
- 真正的组合插件示例
- API概念解释

## 指南和例子
---

下面是一份指南和例子的表格，虽然每个指南都要有示例代码，但是一些示例目前暂时还没有与之匹配的指南。

每个例子都至少阐释了一个[VS Code API](/references/vscode-api)或者[发布内容配置](/references/contribution-points)的使用。

| 例子                                                                                                               | VS Code网页指南                                                    | API & 配置                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Webview Sample](https://github.com/Microsoft/vscode-extension-samples/tree/master/webview-sample)                 | [/extension-guides/webview](/extension-guides/webview)             | [window.createWebviewPanel](https://code.visualstudio.com/api/references/vscode-api#window.createWebviewPanel)<br>[window.registerWebviewPanelSerializer](https://code.visualstudio.com/api/references/vscode-api#window.registerWebviewPanelSerializer)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| [Status Bar Sample](https://github.com/Microsoft/vscode-extension-samples/tree/master/statusbar-sample)            | N/A                                                                | [window.createStatusBarItem](https://code.visualstudio.com/api/references/vscode-api#window.createStatusBarItem)<br>[StatusBarItem](https://code.visualstudio.com/api/references/vscode-api#StatusBarItem)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| [Tree View Sample](https://github.com/Microsoft/vscode-extension-samples/tree/master/tree-view-sample)             | [/extension-guides/tree-view](/extension-guides/tree-view)         | [window.createTreeView](https://code.visualstudio.com/api/references/vscode-api#window.createTreeView)<br>[window.registerTreeDataProvider](https://code.visualstudio.com/api/references/vscode-api#window.registerTreeDataProvider)<br>[TreeView](https://code.visualstudio.com/api/references/vscode-api#TreeView)<br>[TreeDataProvider](https://code.visualstudio.com/api/references/vscode-api#TreeDataProvider)<br>[contributes.views](/references/contribution-points?#contributesviews)<br>[contributes.viewsContainers](/references/contribution-points#contributesviewscontainers)                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| [Task Provider Sample](https://github.com/Microsoft/vscode-extension-samples/tree/master/task-provider-sample)     | [/extension-guides/task-provider](/extension-guides/task-provider) | [tasks.registerTaskProvider](https://code.visualstudio.com/api/references/vscode-api#tasks.registerTaskProvider)<br>[Task](https://code.visualstudio.com/api/references/vscode-api#Task)<br>[ShellExecution](https://code.visualstudio.com/api/references/vscode-api#ShellExecution)<br>[contributes.taskDefinitions](/references/contribution-points?id=contributestaskdefinitions)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| [Multi Root Sample](https://github.com/Microsoft/vscode-extension-samples/tree/master/basic-multi-root-sample)     | N/A                                                                | [workspace.getWorkspaceFolder](https://code.visualstudio.com/api/references/vscode-api#workspace.getWorkspaceFolder)<br>[workspace.onDidChangeWorkspaceFolders](https://code.visualstudio.com/api/references/vscode-api#workspace.onDidChangeWorkspaceFolders)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| [Completion Provider Sample](https://github.com/Microsoft/vscode-extension-samples/tree/master/completions-sample) | N/A                                                                | [languages.registerCompletionItemProvider](https://code.visualstudio.com/api/references/vscode-api#languages.registerCompletionItemProvider)<br>[CompletionItem](https://code.visualstudio.com/api/references/vscode-api#CompletionItem)<br>[SnippetString](https://code.visualstudio.com/api/references/vscode-api#SnippetString)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| [File System Provider Sample](https://github.com/Microsoft/vscode-extension-samples/tree/master/fsprovider-sample) | N/A                                                                | [workspace.registerFileSystemProvider](https://code.visualstudio.com/api/references/vscode-api#workspace.registerFileSystemProvider)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| [Editor Decorator Sample](https://github.com/Microsoft/vscode-extension-samples/tree/master/decorator-sample)      | N/A                                                                | [TextEditor.setDecorations](https://code.visualstudio.com/api/references/vscode-api#TextEditor.setDecorations)<br>[DecorationOptions](https://code.visualstudio.com/api/references/vscode-api#DecorationOptions)<br>[DecorationInstanceRenderOptions](https://code.visualstudio.com/api/references/vscode-api#DecorationInstanceRenderOptions)<br>[ThemableDecorationInstanceRenderOptions](https://code.visualstudio.com/api/references/vscode-api#ThemableDecorationInstanceRenderOptions)<br>[window.createTextEditorDecorationType](https://code.visualstudio.com/api/references/vscode-api#window.createTextEditorDecorationType)<br>[TextEditorDecorationType](https://code.visualstudio.com/api/references/vscode-api#TextEditorDecorationType)<br>[contributes.colors](/references/contribution-points#contributescolors)                                                                                                                                                                                                                  |
| [I18n Sample](https://github.com/Microsoft/vscode-extension-samples/tree/master/i18n-sample)                       | N/A                                                                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| [Terminal Sample](https://github.com/Microsoft/vscode-extension-samples/tree/master/terminal-sample)               | N/A                                                                | [window.createTerminal](https://code.visualstudio.com/api/references/vscode-api#window.createTerminal)<br>[window.onDidChangeActiveTerminal](https://code.visualstudio.com/api/references/vscode-api#window.onDidChangeActiveTerminal)<br>[window.onDidCloseTerminal](https://code.visualstudio.com/api/references/vscode-api#window.onDidCloseTerminal)<br>[window.onDidOpenTerminal](https://code.visualstudio.com/api/references/vscode-api#window.onDidOpenTerminal)<br>[window.Terminal](https://code.visualstudio.com/api/references/vscode-api#window.Terminal)<br>[window.terminals](https://code.visualstudio.com/api/references/vscode-api#window.terminals)                                                                                                                                                                                                                                                                                                                                                                             |
| [Vim Sample](https://github.com/Microsoft/vscode-extension-samples/tree/master/vim-sample)                         | N/A                                                                | [commands](https://code.visualstudio.com/api/references/vscode-api#commands)<br>[StatusBarItem](https://code.visualstudio.com/api/references/vscode-api#StatusBarItem)<br>[window.createStatusBarItem](https://code.visualstudio.com/api/references/vscode-api#window.createStatusBarItem)<br>[TextEditorCursorStyle](https://code.visualstudio.com/api/references/vscode-api#TextEditorCursorStyle)<br>[window.activeTextEditor](https://code.visualstudio.com/api/references/vscode-api#window.activeTextEditor)<br>[Position](https://code.visualstudio.com/api/references/vscode-api#Position)<br>[Range](https://code.visualstudio.com/api/references/vscode-api#Range)<br>[Selection](https://code.visualstudio.com/api/references/vscode-api#Selection)<br>[TextEditor](https://code.visualstudio.com/api/references/vscode-api#TextEditor)<br>[TextEditorRevealType](https://code.visualstudio.com/api/references/vscode-api#TextEditorRevealType)<br>[TextDocument](https://code.visualstudio.com/api/references/vscode-api#TextDocument) |

## 语言插件示例
---

下面的部分是[语言插件](/language-extensions/README)相关示例：

| 例子                                                                                                                             | VS Code网页指南                                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Snippet Sample](https://github.com/Microsoft/vscode-extension-samples/tree/master/snippet-sample)                               | [/language-extensions/snippet-guide](/language-extensions/snippet-guide)                                                                          | [contributes.snippets](https://code.visualstudio.com/api/references/contribution-points#contributes.snippets)   |
| [Language Configuration Sample](https://github.com/Microsoft/vscode-extension-samples/tree/master/language-configuration-sample) | [/language-extensions/language-configuration-guide](/language-extensions/language-configuration-guide)                                            | [contributes.languages](https://code.visualstudio.com/api/references/contribution-points#contributes.languages) |
| [LSP Sample](https://github.com/Microsoft/vscode-extension-samples/tree/master/lsp-sample)                                       | [/language-extensions/language-server-extension-guide](/language-extensions/language-server-extension-guide) |                                                                                                                 |
| [LSP Log Streaming Sample](https://github.com/Microsoft/vscode-extension-samples/tree/master/lsp-log-streaming-sample)           | N/A                                                                                                                                               |                                                                                                                 |
| [LSP Multi Root Server Sample](https://github.com/Microsoft/vscode-extension-samples/tree/master/lsp-multi-server-sample)        | https://github.com/Microsoft/vscode/wiki/Adopting-Multi-Root-Workspace-APIs#language-client--language-server                                      |                                                                                                                 |