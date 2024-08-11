# VS Code 设置

## 一、前言

本套 VS Code 配置是以 `VSCodeVim`  插件为核心，建立的一套全键盘流方案。使用效果跟 NeoVim 存在 90% 以上的类似。

## 二、插件

### Vim-Like 依赖插件

| 插件名称  | 描述     | 补充说明     |
| --------- | -------- | ------------ |
| VSCodeVim | Vim 模拟 | 全键盘流核心 |
| Bookmarks | 书签     | 增加书签功能 |

### 其余插件

按需使用，不一一列举

## 三、外观

- 主题：One Dark Pro
- 图标：vscode-icons
- 字体：Fira Code, Source Code Pro, 'Courier New', monospace

## 四、设置

### VSCodeVim 配置

VSCodeVim 插件由于是一款模拟器，所以它的配置文件是放在 settings.json 文件中，而不是 vimrc 文件中，个人也并不推荐将配置放在 vimrc 文件中，因为这会导致多端同步变的复杂，尽管这款插件可以支持从 vimrc 文件中读取配置。

实现全键盘流，理念是模拟 Vim，涉及改动 `settings.json` 和 `keybings.json` 。了解更多查阅  [VSCodeVim](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim)

### 快捷键

此方案是配置 Vim 全键盘流后的按键映射方案。基本上所有用leader键的地方都是配置在 settings.json 中 vim 配置部分，其他大部分通过 keybingds.json 来模拟。没有改动的按键映射就沿用 VS Code 默认的，下面不记录。

| command                                                      | keybinding   | origin                                       | model         | 配置来源         |
| ------------------------------------------------------------ | ------------ | -------------------------------------------- | ------------- | ---------------- |
| 垂直分屏                                                     | `<leader>sv` | `<C-w>v`                                     | normal        | settings.json    |
| 水平分屏                                                     | `<leader>sh` | `<C-w>s`                                     | normal        | settings.json    |
| 关闭当前窗口                                                 | `<leader>sc` | `<C-w>c`                                     | normal        | settings.json    |
| 关标跳到左边窗口                                             | `<C-h>`      | `<C-w>h`                                     | normal        | keybindings.json |
| 关标跳到下边窗口                                             | `<C-j>`      | `<C-w>j`                                     | normal        | keybindings.json |
| 关标跳到上边窗口                                             | `<C-k>`      | `<C-w>k`                                     | normal        | keybindings.json |
| 关标跳到右边窗口                                             | `<C-l>`      | `<C-w>l`                                     | normal        | keybindings.json |
| ~~跳到最顶部窗口~~                                           | `<C-t>`      | `<C-w>t`                                     | normal        | 暂未配置         |
| 减小宽度                                                     | `<leader>h`  | `<C-w><`                                     | normal        | settings.json    |
| 增加宽度                                                     | `<leader>l`  | `<C-w>>`                                     | normal        | settings.json    |
| 减小高度                                                     | `<leader>j`  | `<C-w>-`                                     | normal        | settings.json    |
| 增加高度                                                     | `<leader>k`  | `<C-w>+`                                     | normal        | settings.json    |
| 窗口等分                                                     | `<leader>=`  | `<C-w>=`                                     | normal        | settings.json    |
| 取消搜索高亮                                                 | `<leader>nh` | `:nohl<CR>`                                  | normal        | settings.json    |
| 格式化代码                                                   | `<leader>lf` | editor.action.formatDocument                 | normal&visual | settings.json    |
| 打开侧边栏                                                   | `<leader>e`  | workbench.action.toggleSidebarVisibility     | normal        | settings.json    |
| 打开大纲（辅助工具栏只设置了一个大纲，因此打开辅助工具栏就变相实现了这个行为） | `<leader>o`  | workbench.action.toggleAuxiliaryBar          | normal        | settings.json    |
| 查找                                                         | `<leader>fi` | actions.find                                 | normal&visual | settings.json    |
| 替换                                                         | `<leader>ri` | editor.action.startFindReplaceAction         | normal&visual | settings.json    |
| 全局替换                                                     | `<leader>rg` | workbench.action.replaceInFiles              | normal&visual | settings.json    |
| 搜索文件                                                     | `<leader>ff` | workbench.action.quickOpen                   | normal        | settings.json    |
| 全局搜索内容 默认窗口打开                                    | `<leader>fg` | workbench.view.search                        | normal        | settings.json    |
| 全局搜索内容 以search editor 打开                            | `<leader>fG` | search.action.openEditor                     | normal        | settings.json    |
| goto symbol (current file)                                   | `<leader>fs` | workbench.action.gotoSymbol                  | normal        | settings.json    |
| goto symbol (all files)                                      | `<leader>Fs` | workbench.action.showAllSymbols              | normal        | settings.json    |
| 关闭当前editor                                               | `<leader>bc` | workbench.action.closeActiveEditor           | normal        | settings.json    |
| 关闭所有左侧editor                                           | `<leader>bh` | workbench.action.closeEditorsToTheLeft       | normal        | settings.json    |
| 关闭所有右侧editor                                           | `<leader>bl` | workbench.action.closeEditorsToTheRight      | normal        | settings.json    |
| 跳到下一个editor                                             | `<leader>bj` | workbench.action.nextEditor                  | normal        | settings.json    |
| 跳到上一个editor                                             | `<leader>bk` | workbench.action.previousEditor              | normal        | settings.json    |
| 移动editor到右边                                             | `<leader>bJ` | workbench.action.moveEditorRightInGroup      | normal        | settings.json    |
| 移动editor到左边                                             | `<leader>bK` | workbench.action.moveEditorLeftInGroup       | normal        | settings.json    |
| 打开错误信息列表                                             | `<leader>q`  | workbench.actions.view.problems              | normal        | settings.json    |
| 打开下一个editor                                             | `<leader>bj` | workbench.action.nextEditor                  | normal        | settings.json    |
| 打开上一个editor                                             | `<leader>bk` | workbench.action.previousEditor              | normal        | settings.json    |
| 查看hover提示                                                | `gh`         | editor.action.showDefinitionPreviewHover     | normal        | settings.json    |
| 跳转到definition                                             | `gd`         | editor.action.revealDefinition               | normal        | settings.json    |
| 跳转到declaration                                            | `gD`         | editor.action.revealDeclaration              | normal        | settings.json    |
| 跳转到implemention                                           | `gi`         | editor.action.goToImplementation             | normal        | settings.json    |
| 查看references                                               | `gr`         | editor.action.goToReferences                 | normal        | settings.json    |
| 以列表视图查看所有references                                 | `gR`         | references-view.findReferences               | normal        | settings.json    |
| 跳转到type_definition                                        | `gt`         | editor.action.goToTypeDefinition             | normal        | settings.json    |
| 查看type_hierarchy                                           | `gT`         | references-view.showTypeHierarchy            | normal        | settings.json    |
| 查看call_hierarchy                                           | `gC`         | references-view.showCallHierarchy            | normal        | settings.json    |
| rename symbol                                                | `<leader>rn` | editor.action.rename                         | normal        | settings.json    |
| quickFix (code action)                                       | `<leader>ca` | editor.action.quickFix                       | normal        | settings.json    |
| 打开错误信息列表                                             | `<leader>q`  | workbench.actions.view.problems              | normal        | settings.json    |
| 跳到下一次错误                                               | `]d`         | editor.action.marker.next                    | normal        | settings.json    |
| 跳到上一次错误                                               | `[d`         | editor.action.marker.prev                    | normal        | settings.json    |
| 打开版本控制（使用的很少，实际被lazygit取代）                | `<leader>gg` | workbench.view.scm                           | normal        | settings.json    |
| 书签开关                                                     | `mm`         | bookmarks.toggle                             | normal        | settings.json    |
| 带label书签开关                                              | `mi`         | bookmarks.toggleLabeled                      | normal        | settings.json    |
| 列出当前文件的书签                                           | `<leader>fm` | bookmarks.list                               | normal        | settings.json    |
| 列出所有文件的书签                                           | `<leader>fM` | bookmarks.listFromAllFiles                   | normal        | settings.json    |
| 跳到下一个书签                                               | `mn`         | bookmarks.jumpToNext                         | normal        | settings.json    |
| 跳到上一个书签                                               | `mp`         | bookmarks.jumpToPrevious                     | normal        | settings.json    |
| 删除当前文件的书签                                           | `mc`         | bookmarks.clear                              | normal        | settings.json    |
| 删除所有文件的书签                                           | `mx`         | bookmarks.clearFromAllFiles                  | normal        | settings.json    |
| 所有文件的书签                                               | `ma`         | bookmarks.listFromAllFiles                   | normal        | settings.json    |
| ReplaceWithRegisterOperator                                  | `<leader>r`  | `gr`                                         | normal        | settings.json    |
| ReplaceWithRegisterVisual                                    | `<leader>r`  | `gr`                                         | visual        | settings.json    |
| ReplaceWithRegisterLine                                      | `<leader>rr` | `grr`                                        | normal        | settings.json    |
| 增加缩进                                                     | `>`          | editor.action.indentLines                    | visual        | settings.json    |
| 减小缩进                                                     | `<`          | editor.action.outdentLines                   | visual        | settings.json    |
| make cursor back to editor                                   | `alt+m`      | workbench.action.focusActiveEditorGroup      |               | keybindings.json |
| hide panel                                                   | `alt+q`      | workbench.action.closePanel                  |               | keybindings.json |
| activitybar visibility                                       | `alt+a`      | workbench.action.toggleActivityBarVisibility |               | keybindings.json |
| enter search bar                                             | `enter`      | search.focus.nextInputBox                    |               | keybindings.json |
| move line down                                               | `alt+j`      | editor.action.moveLinesDownAction            |               | keybindings.json |
| move line up                                                 | `alt+k`      | editor.action.moveLinesUpAction              |               | keybindings.json |
| toggle terminal                                              | `ctrl+\`     | workbench.action.terminal.toggleTerminal     |               | keybindings.json |
| maxmize terminal                                             | `ctrl+m`     | workbench.action.toggleMaximizedPanel        |               | keybindings.json |
| up                                                           | `ctrl+j`     | list.focusDown                               |               | keybindings.json |
| down                                                         | `ctrl+k`     | list.focusUp                                 |               | keybindings.json |
| up                                                           | `ctrl+j`     | selectNextSuggestion                         |               | keybindings.json |
| down                                                         | `ctrl+k`     | selectPrevSuggestion                         |               | keybindings.json |
| up                                                           | `ctrl+j`     | workbench.action.quickOpenNavigateNext       |               | keybindings.json |
| down                                                         | `ctrl+k`     | workbench.action.quickOpenNavigatePrevious   |               | keybindings.json |
| up                                                           | `ctrl+j`     | selectNextCodeAction                         |               | keybindings.json |
| down                                                         | `ctrl+k`     | selectPrevCodeAction                         |               | keybindings.json |
| up                                                           | `ctrl+j`     | showNextParameterHint                        |               | keybindings.json |
| down                                                         | `ctrl+k`     | showPrevParameterHint                        |               | keybindings.json |

### 自动切换输入法

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



