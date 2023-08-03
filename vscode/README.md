# VS Code 设置

## 外观

- 主题：One Dark Pro
- 图标：vscode-icons
- 字体：Fira Code, Source Code Pro, 'Courier New', monospace



## 基本

- 开启字体连字
- 开启linkedEditing（取代auto rename tag插件）
- 关闭缩略图（搭配Vim使用）
- 开启文件自动保存
- 关闭光标闪缩
- 指定默认tab对应空格数，需自定义其余自行配置
- 开启相对行号（搭配Vim使用）
- 将大纲添加到AuxiliaryBar（搭配Vim使用）
- 开启删除确认提示
- 开启拖放确认提示



## Vim 全键盘流

插件基本设置 + 按键重新映射

### VSCodeVim 部分基础设置

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

>It is highly recommended to remap keys using vim commands like `"vim.normalModeKeyBindings"` ([see here](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim#key-remapping)). But sometimes the usual remapping commands are not enough as they do not support every key combinations possible (for example `Alt+key` or `Ctrl+Shift+key`). In this case it is possible to create new keybindings inside [keybindings.json](https://code.visualstudio.com/docs/getstarted/keybindings#_keyboard-shortcuts-reference). To do so: open up keybindings.json in VSCode using `CTRL+SHIFT+P` and select `Open keyboard shortcuts (JSON)`.



基本上所有用leader键的地方都是配置在settings.json 中vim配置部分，其他通过keybingds.json来模拟。没有改动的按键映射就沿用VS Code默认的。

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



#### 更复杂的组合键

```json
// 将键绑定放在此文件中以覆盖默认值auto[]
[
	// todo 1.需要解决terminal 和 pane之间的跳转问题；2.需要添加一些git相关快捷键；3.需要配置gd gD gh gi相关lsp的键
	// -----vim settings start------
    { // window move down
		"key": "ctrl+j",
		"command": "vim.remap",
		"when": "vim.mode == 'Normal' && !suggestWidgetVisible && !inQuickOpen && !panelFocus",
		"args": {
			"after": [
				"<c-w>",
				"j"
			],
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
			],
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
			],
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
			],
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
		"when": "explorerViewletVisible && filesExplorerFocus && !explorerResourceReadonly && !inputFocus"
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
	// -----suggest item end------

	{ // enter search bar
		"key": "enter",
		"command": "search.focus.nextInputBox",
		"when": "inSearchEditor && inputBoxFocus || inputBoxFocus && searchViewletVisible"
	}
]
```

