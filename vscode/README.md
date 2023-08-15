# VS Code 设置

## 前言

本套 VS Code 配置是以 `VSCodeVim`  插件为核心，建立的一套全键盘流方案。使用效果跟 NeoVim 存在 90% 以上的类似。

## 现有插件

按照依赖程度优先级

| 插件名称              | 描述                                                         | 补充说明        |
| --------------------- | ------------------------------------------------------------ | --------------- |
| One Dark Pro          | 主题插件                                                     | 颜值党排第一    |
| vscode-icons          | 为文件添加炫酷图标                                           | 颜值党排第一    |
| VSCodeVim             | Vim 模拟                                                     | 全键盘流核心    |
| Remote Development    | 远程开发扩展包（包含四个扩展：Remote - SSH、Remote - Tunnels、Dev Containers、WSL） | 远程开发必备    |
| Project Manager       | 管理多个项目                                                 |                 |
| GitLens               | Git 源代码管理工具                                           | 增强原有git能力 |
| Commit Message Editor | Git提交信息规范                                              | 代码提交规范    |
| Git Graph             | Git 提交图                                                   |                 |
| Bookmarks             | 书签功能                                                     |                 |
| REST Client           | REST 客户端                                                  |                 |
| Docker                | 提供Docker支持                                               |                 |
| Live Share            | 代码实时协作工具                                             |                 |

| 插件名称                       | 描述                                                         | 补充说明 |
| ------------------------------ | ------------------------------------------------------------ | -------- |
| HTML CSS Support               | HTML CSS 智能提示                                            |          |
| JavaScript (ES6) code snippets | ES6语法下的JavaScript代码片段支持                            |          |
| Vetur                          | Vue 2的语言支持                                              |          |
| Vue Language Features (Volar)  | Vue 3的语言支持                                              |          |
| Prettier                       | 代码格式化                                                   |          |
| ESLint                         | ESLint规范                                                   |          |
| Python                         | 智能感知(Pylance)、检测、调试(多线程、远程)、Jupyter笔记本、代码格式化、重构、单元测试等 |          |

| 插件名称       | 描述                                                         | 补充说明     |
| -------------- | ------------------------------------------------------------ | ------------ |
| Python（套件） | 智能感知(Pylance)、检测、调试(多线程、远程)、Jupyter笔记本、代码格式化、重构、单元测试等 | 写Python必备 |

## 外观

- 主题：One Dark Pro
- 图标：vscode-icons
- 字体：Fira Code, Source Code Pro, 'Courier New', monospace

## 设置

- 开启字体连字
- 开启linkedEditing（取代auto rename tag插件）
- 关闭缩略图（搭配Vim使用）
- 开启文件自动保存
- 开启光标平滑移动效果
- 指定默认tab对应空格数，需自定义其余自行配置
- 开启相对行号（搭配Vim使用）
- 将大纲添加到AuxiliaryBar（搭配Vim使用）
- 开启删除确认提示
- 开启拖放确认提示



## 全键盘流

VSCodeVim 插件由于是一款模拟器，所以它的配置文件是放在settings.json文件中，而不是vimrc文件中，个人也并不推荐将配置放在vimrc文件中，因为这会导致多端同步变的复杂，尽管这款插件可以支持从vimrc文件中读取配置。

实现全键盘流，理念是**基本设置 + 按键重新映射 + 模拟插件**，涉及改动 `settings.json` 和 `keybings.json` 。

### 基础设置

```json
"vim.useCtrlKeys": true, // 启用 Vim ctrl 键覆盖常见的 VS Code 操作，如复制、粘贴、查找等。
"vim.useSystemClipboard": true, // 使用系统剪贴板
"vim.leader": "<space>", // 指定 leader 键
"vim.foldfix": true, // 避免收缩内容自动展开
"vim.incsearch": true, // 输入搜索时显示下一个匹配项
"vim.hlsearch": true, // 高亮显示与当前搜索匹配的所有文本
"vim.highlightedyank.enable": true, // 开启复制高亮提示
"vim.highlightedyank.color": "rgba(252, 93, 124, 0.7)", // 搭配复制高亮提示，指定其颜色
"vim.sneak": true,       // 开启 sneak 模拟功能
"vim.easymotion": false, // 关闭 easymotion 模拟功能
"vim.surround": false, // 关闭 surround 模拟功能
"vim.handleKeys": { // 委托配置的键由 VS Code 而不是 VSCodeVim 扩展处理。
    "<C-f>": true,
    "<C-b>": true,
    "<C-u>": true,
    "<C-d>": true,
    "<C-o>": true,
    "<C-r>": true,
    "<C-c>": true,
    "<C-v>": true,
    "<C-w>": true,
    "<C-z>": true,
},
```



### 按键重新映射

此方案是配置 Vim 全键盘流后的按键映射方案，更多关于 Vim 配置请查阅 [VSCodeVim](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim)

基本上所有用leader键的地方都是配置在settings.json 中vim配置部分，其他大部分通过keybingds.json来模拟。没有改动的按键映射就沿用VS Code默认的。

#### Vim 不同模式

| command                                                      | keybinding  | origin                                   | model  | 配置来源         |
| ------------------------------------------------------------ | ----------- | ---------------------------------------- | ------ | ---------------- |
| 垂直分屏                                                     | \<leader>sv | \<C-w>v                                  | normal | settings.json    |
| 水平分屏                                                     | \<leader>sh | \<C-w>s                                  | normal | settings.json    |
| 关闭当前窗口                                                 | \<leader>sc | \<C-w>c                                  | normal | settings.json    |
| 关标跳到左边窗口                                             | \<C-h>      | \<C-w>h                                  | normal | keybindings.json |
| 关标跳到下边窗口                                             | \<C-j>      | \<C-w>j                                  | normal | keybindings.json |
| 关标跳到上边窗口                                             | \<C-k>      | \<C-w>k                                  | normal | keybindings.json |
| 关标跳到右边窗口                                             | \<C-l>      | \<C-w>l                                  | normal | keybindings.json |
| ~~跳到最顶部窗口~~                                           | ~~\<C-t>~~  | ~~\<C-w>t~~                              | normal | 暂未配置         |
| 减小宽度                                                     | \<leader>h  | \<C-w><                                  | normal | settings.json    |
| 增加宽度                                                     | \<leader>l  | \<C-w>>                                  | normal | settings.json    |
| 减小高度                                                     | \<leader>j  | \<C-w>-                                  | normal | settings.json    |
| 增加高度                                                     | \<leader>k  | \<C-w>+                                  | normal | settings.json    |
| 取消搜索高亮                                                 | \<leader>nh | :nohl\<CR>                               | normal | settings.json    |
| 格式化代码                                                   | \<leader>f  | editor.action.formatDocument             | normal | settings.json    |
| 打开侧边栏                                                   | \<leader>e  | workbench.action.toggleSidebarVisibility | normal | settings.json    |
| 打开大纲（辅助工具栏只设置了一个大纲，因此打开辅助工具栏就变相实现了这个行为） | \<leader>o  | workbench.action.toggleAuxiliaryBar      | normal | settings.json    |
| 搜索文件                                                     | \<leader>ff | workbench.action.quickOpen               | normal | settings.json    |
| 全局搜索内容 以search editor 打开                            | \<leader>fg | search.action.openEditor                 | normal | settings.json    |
| 全局搜索内容 默认窗口打开                                    | \<leader>fG | workbench.view.search                    | normal | settings.json    |
| 打开版本控制（使用的很少，实际被lazygit取代）                | \<leader>g  | workbench.view.scm                       | normal | settings.json    |
| 打开错误信息列表                                             | \<leader>q  | workbench.actions.view.problems          | normal | settings.json    |
| 增加缩进                                                     | >           | editor.action.indentLines                | visual | settings.json    |
| 减小缩进                                                     | <           | editor.action.outdentLines               | visual | settings.json    |
| 选中片段格式化                                               | \<leader>f  | editor.action.formatSelection            | visual | settings.json    |
| 查看hover提示                                                | gh          | editor.action.showDefinitionPreviewHover | normal | settings.json    |
| 跳转到definition                                             | gD          | editor.action.revealDefinition           | normal | settings.json    |
| 跳转到declaration                                            | gd          | editor.action.revealDeclaration          | normal | settings.json    |
| 跳转到implemention                                           | gi          | editor.action.goToImplementation         | normal | settings.json    |
| 查看references                                               | gr          | editor.action.goToReferences             | normal | settings.json    |
| 以列表视图查看所有references                                 | gR          | references-view.findReferences           | normal | settings.json    |
| 跳转到type_definition                                        | \<leader>D  | editor.action.goToTypeDefinition         | normal | settings.json    |
| rename symbol                                                | \<leader>rn | editor.action.rename                     | normal | settings.json    |
| quickFix (code action)                                       | \<leader>ca | editor.action.quickFix                   | normal | settings.json    |
| 打开错误信息列表                                             | \<leader>q  | workbench.actions.view.problems          | normal | settings.json    |
| 跳到下一次错误                                               | ]d          | editor.action.marker.next                | normal | settings.json    |
| 跳到上一次错误                                               | [d          | editor.action.marker.prev                | normal | settings.json    |



#### 更复杂的组合键

>It is highly recommended to remap keys using vim commands like `"vim.normalModeKeyBindings"` ([see here](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim#key-remapping)). But sometimes the usual remapping commands are not enough as they do not support every key combinations possible (for example `Alt+key` or `Ctrl+Shift+key`). In this case it is possible to create new keybindings inside [keybindings.json](https://code.visualstudio.com/docs/getstarted/keybindings#_keyboard-shortcuts-reference). To do so: open up keybindings.json in VSCode using `CTRL+SHIFT+P` and select `Open keyboard shortcuts (JSON)`.

```json
[
	{ // activitybar visibility
		"key": "alt+a",
		"command": "workbench.action.toggleActivityBarVisibility"
	},
	{ // quit panel (except terminal)
		"key": "alt+q",
		"command": "workbench.action.closePanel"
	},
	{ // make cursor back to editor => solve the jump problem between terminal and editor
		"key": "ctrl+k",
		"command": "workbench.action.focusActiveEditorGroup",
		"when": "panelFocus && activePanel"
	},

	// -----vim settings start------
    { // window move down
		"key": "ctrl+j",
		"command": "vim.remap",
		"when": "vim.mode == 'Normal' && !suggestWidgetVisible && !inQuickOpen && !panelFocus",
		"args": {
			"after": [
				"<c-w>",
				"j"
			]
		}
	},
	{ // window move up
		"key": "ctrl+k",
		"command": "vim.remap",
		"when": "vim.mode == 'Normal' && !suggestWidgetVisible && !inQuickOpen && !panelFocus",
		"args": {
			"after": [
				"<c-w>",
				"k"
			]
		}
	},
	{ // window move left
		"key": "ctrl+h",
		"command": "vim.remap",
		"when": "vim.mode == 'Normal' && !suggestWidgetVisible && !inQuickOpen && !panelFocus",
		"args": {
			"after": [
				"<c-w>",
				"h"
			]
		}
	},
	{ // window move right
		"key": "ctrl+l",
		"command": "vim.remap",
		"when": "vim.mode == 'Normal' && !suggestWidgetVisible && !inQuickOpen && !panelFocus",
		"args": {
			"after": [
				"<c-w>",
				"l"
			]
		}
	},
	// -----vim settings end------

	// -----file explorer start------
	{ // move down
		"key": "j",
		"command": "list.focusDown",
		"when": "explorerViewletVisible && filesExplorerFocus && !explorerResourceIsRoot && !explorerResourceReadonly && !inputFocus"
	},
	{ // move up
		"key": "k",
		"command": "list.focusUp",
		"when": "explorerViewletVisible && filesExplorerFocus && !explorerResourceIsRoot && !explorerResourceReadonly && !inputFocus"
	},
	{ // toggle folder expand
		"key": "tab",
		"command": "list.toggleExpand",
		"when": "explorerViewletVisible && filesExplorerFocus && !inputFocus"
	},
	{ // toggle folder expand
		"key": "o",
		"command": "list.toggleExpand",
		"when": "explorerViewletVisible && filesExplorerFocus && !inputFocus"
	},
	{ // select file to open
		"key": "l",
		"command": "list.select",
		"when": "explorerViewletVisible && filesExplorerFocus && !inputFocus"
	},
	{ // collapse folder
		"key": "h",
		"command": "list.collapse",
		"when": "explorerViewletVisible && filesExplorerFocus && !inputFocus"
	},
    { // new file
		"key": "a",
		"command": "explorer.newFile",
		"when": "explorerViewletVisible && filesExplorerFocus && !inputFocus"
	},
	{ // new folder
		"key": "shift+a",
		"command": "explorer.newFolder",
		"when": "explorerViewletVisible && filesExplorerFocus && !inputFocus"
	},
	{ // delete file or folder
		"key": "d",
		"command": "deleteFile",
		"when": "explorerViewletVisible && filesExplorerFocus && !explorerResourceIsRoot && !explorerResourceReadonly && !inputFocus"
	},
	{ // rename file
		"key": "r",
		"command": "renameFile",
		"when": "explorerViewletVisible && filesExplorerFocus && !explorerResourceIsRoot && !explorerResourceReadonly && !inputFocus"
	},
	// copy file
	{
		"command": "filesExplorer.copy",
		"key": "c",
		"when": "explorerViewletVisible && filesExplorerFocus && !inputFocus"
	},
	// paste file
	{
		"command": "filesExplorer.paste",
		"key": "p",
		"when": "explorerViewletVisible && filesExplorerFocus && !inputFocus"
	},
	// cut file
	{
		"command": "filesExplorer.cut",
		"key": "x",
		"when": "explorerViewletVisible && filesExplorerFocus && !inputFocus"
	},
	{ // disable old style rename shortcut
		"key": "enter",
		"command": "-renameFile",
		"when": "explorerViewletVisible && filesExplorerFocus && !explorerResourceIsRoot && !explorerResourceReadonly && !inputFocus"
	},
	// -----file explorer end------

	// -----terminal start------
	{ // toggle terminal
		"key": "ctrl+\\",
		"command": "workbench.action.terminal.toggleTerminal",
		"when": "terminal.active"
	},
	{ // maxmize terminal
		"key": "ctrl+m",
		"command": "workbench.action.toggleMaximizedPanel",
		"when": "terminalFocus"
	},
	// -----terminal end------

	// -----suggest item start------
	{ // move down at auto completion prompt
		"key": "ctrl+j",
		"command": "selectNextSuggestion",
		"when": "editorTextFocus && suggestWidgetMultipleSuggestions && suggestWidgetVisible"
	},
	{ // move up at auto completion prompt
		"key": "ctrl+k",
		"command": "selectPrevSuggestion",
		"when": "editorTextFocus && suggestWidgetMultipleSuggestions && suggestWidgetVisible"
	},
	{ // move down at quick open
		"key": "ctrl+j",
		"command": "workbench.action.quickOpenNavigateNext",
		"when": "inQuickOpen"
	},
	{ // move up at quick open
		"key": "ctrl+k",
		"command": "workbench.action.quickOpenNavigatePrevious",
		"when": "inQuickOpen"
	},
	{ // move down at problem open
		"key": "ctrl+shift+j",
		"command": "list.focusDown",
		"when": "panelFocus && activePanel == 'workbench.panel.markers' "
	},
	{ // move up at problem open
		"key": "ctrl+shift+k",
		"command": "list.focusUp",
		"when": "panelFocus && activePanel == 'workbench.panel.markers' "
	},
	{ // move down at code action
  		"key": "ctrl+j",
  		"command": "selectNextCodeAction",
  		"when": "codeActionMenuVisible"
	},
	{ // move up at code action
  		"key": "ctrl+k",
  		"command": "selectPrevCodeAction",
  		"when": "codeActionMenuVisible"
	},
	// -----suggest item end------

	{ // enter search bar
		"key": "enter",
		"command": "search.focus.nextInputBox",
		"when": "inSearchEditor && inputBoxFocus || inputBoxFocus && searchViewletVisible"
	}
]
```



### 模拟插件

默认都是关闭

开启

- vim-commentary
- vim-sneak

关闭

- vim-airline
- vim-easymotion
- vim-surround



## 自动切换输入法

在使用 VSCode Vim 编写代码时，经常会在 normal 和 insert 两种模式中切换，但是如果刚刚在 insert 模式下输入完中文，这时按 esc 切换到 normal 模式，无法直接输入指令，因为此时输入法还处于中文状态，需要先按 shift 切换到英文才可以。为了切换到 `normal` 模式时输入法能自动切换为英文状态，可以通过 im-select 来实现。

1. 安装 [im-select](https://github.com/daipeihust/im-select)
2. 将下面部分添加到 `VS Code` 的 `settings.json`

```json
// 开启自动切换输入法
"vim.autoSwitchInputMethod.enable": true,
// 设置默认输入法，值获取方法：切换到系统的英文输入法，在命令行输入 im-select 就可以获取当前输入法的值了
"vim.autoSwitchInputMethod.defaultIM": "xxx", // xxx 表示默认输入法或者输入法编号
// im-select 安装路径，在命令行输入 which im-select 获取
"vim.autoSwitchInputMethod.obtainIMCmd": "xxx", // xxx表示安装路径
"vim.autoSwitchInputMethod.switchIMCmd": "xxx {im}"
```



