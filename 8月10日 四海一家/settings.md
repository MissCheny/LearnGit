```json
{ // ===================工作台 workbench=========================
  "workbench.statusBar.visible": true,             // 工作台底部状态栏的可见性
  "workbench.activityBar.location": "bottom",      // 活动栏底部显示
  "workbench.startupEditor": "none", // 主题
  "workbench.iconTheme": "material-icon-theme",    // 图标主题
  "workbench.list.mouseWheelScrollSensitivity": 3, // 工作台列表滚动速度
  "workbench.editorAssociations": {
    "{git, gitlens, git-graph}:/**/*.{md, csv, svg}": "default",
    // 作用范围：Git 扩展（git/gitlens/git-graph）生成的特殊路径文件
    // 文件类型：所有 .md (Markdown)、.csv (表格)、.svg (矢量图) 文件

    // 专门处理 Git 变基操作时生成的 git-rebase-todo 文件
    // 使用 GitLens 扩展提供的可视化变基编辑器（比原始文本编辑更友好）
  },
  "workbench.editor.autoLockGroups": {
    "workbench.editor.chatSession": true     // 锁定chat窗口，避免误关闭
  },

  // ===========files==============================
  "files.autoSave": "afterDelay",            // 文件（默认1000ms）后自动保存

  // ===========editor================================
  "editor.minimap.enabled": false,           // 缩略图
  "editor.wordWrap": "off",                  // 代码过多时，显示效果（换行、折叠）
  "editor.formatOnSave": false,              // 保存时，自动格式化代码。自己调整的格式更适合我自己
  "editor.accessibilitySupport": "off",      // 试听障碍人士的编辑器辅助功能
  "editor.mouseWheelScrollSensitivity": 2,   // 编辑器滚动速度
  "editor.parameterHints.enabled": true,     // 参数提示：输入函数名后弹出，显示该函数的参数信息。
  "editor.mouseWheelZoom": true,             // 鼠标缩放：Ctrl+鼠标滚轮
  "editor.fontSize": 16,                     // 编辑器中代码的字体大小为16
  "editor.maxTokenizationLineLength": 40000, // 代码行长度超过40000字符时，将不再进行高亮和语法分析，以避免降低性能
  
  //=============emmet====更多快捷触发功能请自行搜索Emmet=======================
  "emmet.triggerExpansionOnTab": true,    // 输入`ul>li*5`后，按Tab键，生成包含5个<li>的无序列表
  
  // ==============terminal=终端======================
  // -------------基础配置---------------------------------------------------------------------------
  "terminal.integrated.defaultProfile.linux": "",             // Linux终端：""表示使用系统默认终端
  // "terminal.integrated.defaultProfile.windows": "Git Bash",   // 这个配置会拖慢VSCode的启动速度，Windows终端：（Ctrl+`自动打开）Git Bash

  // -------------目录设置-----------------------------------------------------------------------------
  "terminal.integrated.cwd": "${fileDirname}",  // 新终端会以当前所在目录为工作目录
  "terminal.integrated.splitCwd": "initial",    // "initial"：分屏终端继承原终端目录

  // --------------显示优化-----------------------------------------------------------------------------
  "terminal.integrated.mouseWheelScrollSensitivity": 3,   // 终端滚动速度
  "terminal.integrated.mouseWheelZoom": true,             // 终端鼠标缩放
  "terminal.integrated.rescaleOverlappingGlyphs": false,  // 终端字体抗锯齿，可避免字体显示异常

  // ==============jupyter====================================
  "jupyter.interactiveWindow.creationMode": "perFile",    // 同时打开的不同文件，不会因为变量名相同而污染另一个文件
  "jupyter.askForKernelRestart": false,                    // 重启内核时弹出确认框

  // ================explorer资源管理器=========================
  "explorer.confirmDelete": false,                        // 删除文件不会弹出确认框
  "explorer.confirmDragAndDrop": false,                   // 拖拽文件不会弹出确认框
  "explorer.confirmPasteNative": false,                   // 粘贴文件不会弹出确认框

  // ==============notebook====================================
  "notebook.cellToolbarLocation": {
    "default": "right",                                  // 默认工具栏位置：右侧
    "jupyter-notebook": "right"                          // 特别指定 Jupyter Notebook 的工具栏位置：右侧
  },
  "notebook.lineNumbers": "on",                          // 显示行号
  "notebook.codeActionsOnSave": {}, // 单元格的行高
  
  // ==============fittencode==================================
  "fittencode.languagePreference.displayPreference": "zh-cn",
  "fittencode.languagePreference.commentPreference": "zh-cn",
  "fittencode.action.askFile.showInResourceMenu": true,
  "fittencode.selection.showCodeLens": false,

  // ==============window======================================
  "window.customTitleBarVisibility": "auto",
  "window.title": "${folderName}",
  "window.zoomLevel": 1,

  // ===============material-icon-theme========================
  "material-icon-theme.files.associations": {},

  // ===============python======================================
  "python.terminal.executeInFileDir": true,

  // ====================markdown===============================
  "[markdown]": {
    "editor.defaultFormatter": "yzhang.markdown-all-in-one"
  },
  "markdown-preview-enhanced.previewTheme": "solarized-light.css",
  "markdown-preview-enhanced.codeBlockTheme": "solarized-light.css",
  "markdown-preview-enhanced.revealjsTheme": "beige.css",
  "markdown-preview-enhanced.enablePreviewZenMode": true,
  "markdown.extension.list.indentationSize": 2,
  "markdown.extension.preview.autoShowPreviewToSide": true,


  // =====================prettier==============================
  "prettier.tabWidth": 4, // 代码块缩进量
  "prettier.proseWrap": "never", // 防止段落自动换行
  "prettier.printWidth": 80, // 控制行长
  "prettier.useTabs": false, // 强制使用空格

  // ===================extensions:Office Viewer================
  "vscode-office.openOutline": true,
  "vscode-office.editorTheme": "Auto",

  // ===================未分类===================================
  "dataWrangler.debug": true,
  "settingsSync.ignoredSettings": [],
  "security.workspace.trust.untrustedFiles": "open",
  "github.copilot.enable": {
    "*": false,
    "plaintext": false,
    "markdown": false,
    "scminput": false
  },

  // ===============git==========================================
  "git.enableSmartCommit": false,
  "git.autofetch": true,
  "git.openRepositoryInParentFolders": "always",

  // ===============gitlens========================
  "gitlens.graph.layout": "editor",
  "gitlens.hovers.currentLine.over": "line",
  "gitlens.changes.locations": [
    "gutter",
    "overview",
    "line"
  ],
  "gitlens.heatmap.locations": [
    "overview",
    "gutter"
  ],
  "gitlens.currentLine.format": "${' via  'pullRequest}${message|50?} - ${id}",
  "markdown-preview-enhanced.enableExtendedTableSyntax": true,
  "gitlens.views.formats.commits.description": "${agoOrDate}",
  "gitlens.statusBar.format": "${agoOrDate}${' via  'pullRequest}",
  "gitlens.views.commitDetails.files.layout": "tree",

  // =========================vim==============================
  // before（按键序列）、after（映射后的按键）或commands（执行的命令）
  "vim.easymotion": true,
  "vim.incsearch": true,
  "vim.useSystemClipboard": true,
  "vim.useCtrlKeys": true,
  "vim.hlsearch": true,

  // -------------`INSERT`模式按键绑定---------------------------------
  "vim.insertModeKeyBindings": [
    {"before": ["j","j"], "after": ["<Esc>"]},   // `jj`退出插入模式
  ],

  // -------------`NORMAL`模式按键绑定，非递归--------------------------
  "vim.normalModeKeyBindingsNonRecursive": [
    {
      "before": ["<leader>","d"],      // 按下<leader>d
      "after": ["d","d"]               // 相当于按下`dd`键
    },
    {
      "before": ["<C-n>"],             // 按下Ctrl+n 
      "commands": [":nohl"]            // 执行 `:nohl`命令 ▸ 取消搜索后的关键词高亮显示
    },
    {
      "before": ["K"],                 // 按下 `K`
      "commands": ["lineBreakInsert"], // 执行 lineBreakInsert 命令 ▸ 插入空行，光标不跳转
      "silent": true,                  // 执行时，不显示命令执行结果
    },
    // ----------------------自定义-------------必须需切换到英文输入法------------
    {"before": ["<S-E>"], "after": ["g","T"]}, // Shift+E 左标签页切换
    {"before": ["<S-R>"], "after": ["g","t"]}, // Shift+R 右标签页切换

  ],
  "vim.leader": "<space>",
  "vim.handleKeys": {
    "<C-a>": false,
    "<C-f>": false,
  },
  "extensions.experimental.affinity": {
    "vscodevim.vim": 1
  },
  "terminal.integrated.fontSize": 16,
  "markdowntable.showMenu.csvToTable": true,
  "fittencode.action.generateUnitTest.showInEditorContextMenu": false,
  "fittencode.showSubmenu": true,
  "chat.commandCenter.enabled": false,
  "workbench.layoutControl.enabled": false,
  "diffEditor.hideUnchangedRegions.enabled": true,
  "workbench.secondarySideBar.defaultVisibility": "hidden",
  "telemetry.feedback.enabled": false,
  "github.copilot.nextEditSuggestions.enabled": false,
  "github.copilot.chat.edits.suggestRelatedFilesForTests": false,
  "github.copilot.chat.newWorkspaceCreation.enabled": false,
  "github.copilot.chat.agent.autoFix": false,
  "github.copilot.chat.agent.runTasks": false,
  "github.copilot.chat.codeGeneration.useInstructionFiles": false,
  "github.copilot.chat.useProjectTemplates": false,
  "github.copilot.editor.enableCodeActions": false,
  "github.copilot.nextEditSuggestions.fixes": false,
  "github.copilot.renameSuggestions.triggerAutomatically": false,
  "github.copilot.chat.copilotDebugCommand.enabled": false,
  "github.copilot.chat.reviewSelection.enabled": false,
  "github.copilot.chat.startDebugging.enabled": false,
  "github.copilot.chat.agent.currentEditorContext.enabled": false,
  "github.copilot.chat.edits.suggestRelatedFilesFromGitHistory": false,
  "github.copilot.chat.setupTests.enabled": false,
  "github.copilot.chat.summarizeAgentConversationHistory.enabled": false,
  "workbench.colorTheme": "Solarized Light",
}
```