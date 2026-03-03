## 二、Lazygit基本使用方法

- ### LazyGit 详细使用方法

  Lazygit 是一个简单高效的终端 UI 工具，用于简化 Git 命令操作。它可以帮助你可视化地管理 Git 仓库，包括分支、提交、暂存区等操作，而无需记忆复杂的 Git 命令。下面我将从安装、基本使用、键绑定、功能特点以及常见工作流程等方面进行详细说明。这些信息基于官方文档（GitHub README），以确保准确性。

  #### 1. 安装方法
  Lazygit 支持多种操作系统和安装方式。你可以根据自己的环境选择合适的方法。安装后，确保你的终端 PATH 中包含 lazygit 的可执行文件。

  - **二进制文件下载**：从 [GitHub Releases](https://github.com/jesseduffield/lazygit/releases) 下载适用于 Windows、macOS (10.12+) 或 Linux 的二进制文件。
  - **Homebrew (macOS/Linux)**：运行 `brew install lazygit`。
  - **MacPorts (macOS)**：运行 `sudo port install lazygit`。
  - **Arch Linux**：通过 pacman 或 AUR 安装（AUR 详情见 [Arch Wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository)）。
  - **Fedora / CentOS / Amazon Linux**：启用 Copr 仓库 `sudo dnf copr enable dejan/lazygit`，然后 `sudo dnf install lazygit`。
  - **Debian / Ubuntu**：对于较新版本，直接 `sudo apt install lazygit`；旧版本可使用 curl 脚本手动安装：
    ```
    LAZYGIT_VERSION=$(curl -s "https://api.github.com/repos/jesseduffield/lazygit/releases/latest" | grep -Po '"tag_name": "v\K[^"]*')
    curl -Lo lazygit.tar.gz "https://github.com/jesseduffield/lazygit/releases/latest/download/lazygit_${LAZYGIT_VERSION}_Linux_x86_64.tar.gz"
    tar xf lazygit.tar.gz lazygit
    sudo install lazygit /usr/local/bin
    rm -f lazygit.tar.gz lazygit
    ```
    验证：`lazygit --version`。
  - **Windows (Scoop)**：`scoop bucket add extras` 然后 `scoop install lazygit`。
  - **Windows (Chocolatey)**：`choco install lazygit`。
  - **Windows (Winget)**：`winget install -e --id=JesseDuffield.lazygit`。
  - **Go 安装**：如果有 Go 环境，运行 `go install github.com/jesseduffield/lazygit@latest`（确保 `~/go/bin` 在 PATH 中）。
  - **其他 Linux 发行版**：如 openSUSE、Gentoo、NixOS 等，有专用仓库或命令（详见官方文档）。
  - **手动构建**：克隆仓库 `git clone https://github.com/jesseduffield/lazygit.git`，进入目录运行 `go install` 或 `go run main.go`（需安装 Go）。

  安装完成后，在终端输入 `lazygit --help` 测试是否成功。

  #### 2. 基本使用
  - **启动**：在 Git 仓库目录下运行 `lazygit`（简称 `lg`，你可以添加别名到 shell 配置文件中，如 `echo "alias lg='lazygit'" >> ~/.zshrc` 并 `source ~/.zshrc`）。
  - **界面概述**：启动后，lazygit 会显示一个分屏界面：
    - **左侧面板**：文件列表（未暂存/暂存的文件）。
    - **中间面板**：提交历史（commits）、分支（branches）等。
    - **右侧面板**：选中的文件或提交的详细内容（如 diff）。
    - **底部**：状态栏，显示当前模式、帮助提示。
  - **导航**：使用 Vim 风格的键（hjkl）或箭头键移动光标。按 `?` 查看当前面板的键绑定帮助。
  - **退出**：按 `q` 退出当前面板，按 `Q` 完全退出 lazygit。
  - **配置**：默认配置文件在 `~/.config/lazygit/config.yml`，你可以自定义键绑定、主题等。运行 `lazygit --help` 查看所有选项。

  **提示**：如果想在退出时切换到 lazygit 中使用的仓库目录，可以在 shell 配置文件（如 `~/.zshrc`）中添加以下函数：
  ```
  lg() {
      export LAZYGIT_NEW_DIR_FILE=~/.lazygit/newdir
      lazygit "$@"
      if [ -f $LAZYGIT_NEW_DIR_FILE ]; then
          cd "$(cat $LAZYGIT_NEW_DIR_FILE)"
          rm -f $LAZYGIT_NEW_DIR_FILE > /dev/null
      fi
  }
  ```
  然后使用 `lg` 启动。按 `Shift + Q` 可以覆盖此行为直接退出而不切换目录。

  #### 3. 键绑定（Key Bindings）
  Lazygit 的键绑定类似于 Vim，高度可自定义。以下是常见默认键绑定，按面板或操作分类（按 `?` 在界面中查看实时帮助）。这些键在不同模式下可能略有变化。

  - **全局键（适用于所有面板）**：
    - `q`：退出当前面板或视图。
    - `Q`：完全退出 lazygit。
    - `?`：显示帮助（键绑定列表）。
    - `g`：刷新界面（重新加载数据）。
    - `F1` 或 `h`：切换到主视图（文件/分支/提交）。
    - `F2` 或 `c`：切换到提交视图。
    - `F3` 或 `b`：切换到分支视图。
    - `F4` 或 `s`：切换到暂存视图（staged files）。
    - `F5` 或 `u`：切换到未暂存视图（unstaged files）。
    - `F6` 或 `r`：切换到 reflog 视图（引用日志）。
    - `/`：搜索（在当前面板搜索）。

  - **文件面板（Files Panel，未暂存/暂存文件）**：
    - `Space`：暂存/取消暂存选中的文件（或 hunk）。
    - `c`：签入（commit）选中的文件或 hunk。
    - `e`：编辑选中的文件（打开编辑器）。
    - `d`：查看 diff（差异）。
    - `h` / `j` / `k` / `l`：向上/向下/左/右导航（或箭头键）。
    - `a`：暂存所有文件。
    - `Enter`：展开/折叠 hunk（代码块）。
    - `Ctrl + Space`：切换 hunk 选择模式。

  - **提交面板（Commits Panel）**：
    - `c`：签入（checkout）选中的提交。
    - `r`：重置（reset）到选中的提交（小心使用，会丢失更改）。
    - `s`：软重置（soft reset）。
    - `h`：硬重置（hard reset）。
    - `m`：修改选中的提交（reword commit message）。
    - `d`：查看 diff。
    - `p`：推送到远程（push）。
    - `f`：拉取（fetch）远程更改。

  - **分支面板（Branches Panel）**：
    - `c`：签出（checkout）选中的分支。
    - `n`：创建新分支。
    - `d`：删除选中的分支。
    - `r`：重命名分支。
    - `m`：合并（merge）选中的分支。
    - `b`：变基（rebase）到选中的分支。
    - `p`：推送到远程分支。
    - `u`：上游设置（set upstream）。

  - **其他操作**：
    - `o`：打开外部 diff 工具（需配置）。
    - `z`：撤销（undo）最近操作。
    - `:`：进入命令模式，输入 Git 命令（如 `:git push`）。
    - `Shift + P`：打开子模块面板。
    - `Shift + S`：打开 stash 面板（存储未提交更改）。
    - `Ctrl + R`：重新加载配置。

  **自定义键绑定**：在 `~/.config/lazygit/config.yml` 中编辑键映射，例如：
  ```
  keybindings:
    universal:
      return: toggle-files
  ```
  重启 lazygit 生效。更多自定义见官方文档。

  #### 4. 功能特点（Features）
  - **可视化 Git 操作**：直观显示文件状态、提交历史、分支图，支持 diff 高亮。
  - **Hunk 级别操作**：可以选择性暂存代码块（hunk），而非整个文件。
  - **集成 Git 命令**：支持 cherry-pick、rebase、merge、stash 等高级操作。
  - **子模块支持**：管理嵌套 Git 仓库。
  - **Reflog 和 Bisect**：查看引用日志，进行二分查找 bug。
  - **主题和外观**：支持自定义颜色方案（默认使用终端主题）。
  - **无依赖**：纯 Go 编写，轻量级，不需额外依赖。
  - **跨平台**：Windows、macOS、Linux 均支持。
  - **插件扩展**：有限，但可以通过配置集成外部工具如 diff 编辑器。

  #### 5. 常见工作流程（Tips and Workflows）
  - **日常提交**：
    1. 启动 `lazygit`。
    2. 在文件面板选择文件，按 `Space` 暂存。
    3. 按 `c` 打开 commit 编辑器，输入消息并保存。
    4. 切换到分支面板，按 `p` 推送。

  - **分支管理**：
    1. 切换到分支视图（`F3` 或 `b`）。
    2. 按 `n` 创建新分支。
    3. 切换分支（`c`），然后 `m` 合并或 `b` 变基。

  - **解决冲突**：
    1. 拉取远程（`f`）。
    2. 如果冲突，在文件面板查看 diff，按 `e` 编辑文件。
    3. 暂存解决的文件，按 `c` 提交。

  - **撤销操作**：
    - 使用 reflog 视图（`F6`）恢复丢失提交。
    - 按 `z` 快速撤销最近更改。

  - **提示**：
    - 初学者：多按 `?` 查看帮助，避免误操作（如重置）。
    - 性能：对于大仓库，lazygit 可能稍慢；使用 `g` 刷新。
    - 集成 IDE：如 VS Code，可以通过终端插件调用 lazygit。
    - 更新：定期检查 Releases 页面更新版本。
    - 问题排查：如果界面乱码，检查终端字体支持 Unicode；运行 `lazygit --debug` 查看日志。！
