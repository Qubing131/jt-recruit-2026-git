# Git 入门学习笔记

## 一、Git 和 GitHub 的区别

- Git 是一个版本管理工具，用来记录文件修改、保存版本历史。
- GitHub 是代码托管与协作平台，可以存放和分享 Git 仓库。
- Git 可以在本地使用，提交不一定需要联网。
- 本地修改不会自动同步到 GitHub，需要进行推送。

## 二、仓库和 README

- 仓库（repository）保存项目文件及其版本历史。
- 本次练习的仓库名称是 `jt-recruit-2026-git`。
- 仓库设置为 Public，其他人可以公开访问。
- `README.md` 用来介绍仓库用途，GitHub 会在仓库首页展示它。
- `.md` 是 Markdown 文件的扩展名，可以使用记事本编辑。
- Markdown 中，`# ` 表示一级标题，`## ` 表示二级标题，`- ` 可以表示列表项。

## 三、检查 Git 是否安装成功

```bash
git --version
```

- 查看电脑上安装的 Git 版本。
- 出现 `git version ...`，说明 Git 命令可以正常使用。

## 四、配置提交者信息

```bash
git config --global user.name "你的昵称"
git config --global user.email "你的邮箱"
```

- `--global` 表示作为当前电脑用户的默认配置。
- 这些信息用于提交署名，不是登录 GitHub。
- 邮箱会写入提交记录，可以使用 GitHub 提供的隐私邮箱。

查看当前配置：

```bash
git config --global user.name
git config --global user.email
```

- 带具体名字或邮箱时，是设置配置。
- 不带具体值时，是查看配置。
- 设置成功后通常没有文字提示，可以通过查看命令确认。


## 五、克隆 GitHub 仓库

```bash
git clone https://github.com/Qubing131/jt-recruit-2026-git.git
```

- `git clone` 将远端仓库复制到电脑。
- 克隆的内容包括项目文件和已有的提交历史。
- Git 还会记住远端仓库地址，方便之后同步。

进入本地仓库：

```bash
cd jt-recruit-2026-git
```

- 后续仓库操作需要在正确的仓库目录中执行。

## 六、打开和编辑文件

```bash
explorer .
```

- 使用 Windows 文件资源管理器打开当前文件夹。
- `.` 代表当前文件夹。
- 这不是 Git 命令。

```bash
notepad notes.md
```

- 使用记事本打开或准备创建 `notes.md`。
- 按 Ctrl + S 只是保存文件内容，不会自动产生 Git 提交。

## 七、查看文件状态

```bash
git status
```

- 查看文件是否修改、是否暂存，以及是否有新文件。
- 这个命令只查看状态，不会修改或上传文件。

常见提示：

- `modified`：已被 Git 跟踪的文件发生了修改。
- `Untracked files`：出现了尚未被 Git 跟踪的新文件。
- `Changes to be committed`：有改动已经暂存，准备提交。
- `nothing to commit, working tree clean`：当前没有待提交的文件变化，但不代表已经推送到 GitHub。

修改 README 后，我看到了：

```text
modified: README.md
```

这说明 Git 发现了文件变化，属于正常提示。

## 八、暂存修改

```bash
git add README.md
```

- 把 README.md 当前的改动放入暂存区。
- 暂存区用于准备下一次提交的内容。
- `git add` 可以暂存新文件，也可以暂存已有文件的修改。
- 这个命令不会上传文件到 GitHub。
- 如果暂存后又修改了文件，需要再次执行 `git add`，才能把后来的修改也放进暂存区。

## 九、提交修改

```bash
git commit -m "补充仓库用途说明"
```

- `git commit` 将暂存区中的内容保存为一次本地版本记录。
- `-m` 后面是本次提交的说明。
- 提交说明应写清楚修改内容，方便以后查看。
- 提交完成后，版本记录保存在电脑上，还没有同步到 GitHub。

我的第一次本地提交结果：

```text
[main 4fab757] 补充仓库用途说明
1 file changed, 3 insertions(+)
```

含义：

- `main`：当前分支名称。
- `4fab757`：本次提交编号的简写。
- `补充仓库用途说明`：本次提交说明。
- `1 file changed`：修改涉及一个文件。
- `3 insertions(+)`：新增三行内容。

## 十、推送到 GitHub

```bash
git push
```

- 将本地提交同步到远端仓库。
- 第一次推送时可能需要在浏览器中登录并完成授权。
- 配置提交者信息是设置署名；登录验证是确认我有权限向仓库推送。

我的推送结果中出现了：

```text
5e273e8..4fab757  main -> main
```

这表示 GitHub 上的 main 分支从旧版本更新到了本次提交，推送成功。

## 十一、保存、暂存、提交和推送的区别

1. 保存：按 Ctrl + S，把编辑内容写入电脑上的文件。
2. 暂存：执行 `git add`，选择本次准备提交的改动。
3. 提交：执行 `git commit`，在本地建立版本记录。
4. 推送：执行 `git push`，把本地提交同步到 GitHub。

常用流程：

```text
修改文件 → 保存文件 → 查看状态 → 暂存 → 提交 → 推送
```

Git 不会自动保存每次编辑的中间状态，需要主动提交值得保留的版本。

## 十二、实际遇到的问题

### 1. 配置名字和邮箱后没有反馈

- 一开始以为命令没有执行成功。
- 后来了解到，Git 设置成功时通常不会显示提示。
- 可以使用不带具体值的配置命令，查看是否设置成功。

### 2. Git Bash 中不能按习惯粘贴

- Ctrl + V 不一定适用于 Git Bash。
- 可以使用右键菜单中的 Paste 粘贴。
- 也可以尝试 Shift + Insert。
- Git Bash 中的 Ctrl + C 通常表示取消当前操作，不是复制。

### 3. 不理解提交和推送的区别

- `git commit` 是在本地保存版本记录。
- `git push` 才是把提交同步到 GitHub。
- 两个操作不能混为一谈。




## Markdown 常用笔记

Markdown 是一种文本标记格式，文件通常以 `.md` 结尾。可以用记事本编辑，GitHub 会显示排版后的效果。

### 1. 标题

使用 `#` 表示标题，符号后面要有空格。

```markdown
# 一级标题
## 二级标题
### 三级标题
```

### 2. 分段和加粗

段落之间空一行；重点文字前后各加两个星号。

```markdown
这是第一段。

这是第二段，其中 **这部分是重点**。
```

### 3. 列表

无序列表用 `-` 加空格，有序列表用数字加英文句点和空格。

```markdown
- 第一个要点
- 第二个要点

1. 第一步
2. 第二步
```

### 4. 行内代码和代码块

句子中的命令、文件名等，用一对英文反引号包起来：

```markdown
使用 `git status` 查看状态。
笔记保存在 `notes.md` 中。
```

多行代码使用三个反引号包住，开头和结尾各占一行。开头可以注明语言，如 `bash`、`c`、`python`。

示例：

````markdown
```bash
git add notes.md
git commit -m "更新学习笔记"
git push
```
````

反引号是 `` ` ``，不是单引号 `'`。代码块结尾的三个反引号不能漏掉。

### 5. 链接

格式是 `[显示文字](网址)`。

```markdown
[我的仓库](https://github.com/Qubing131/jt-recruit-2026-git)
```

### 6. 图片

格式是 `![图片说明](图片路径)`。

```markdown
![运行结果](images/result.png)
```

这个例子要求 Markdown 文件所在目录下有一个 `images` 文件夹，其中保存了 `result.png`。

图片需要一起提交到仓库，不能使用只有自己电脑能访问的 `C:\...` 路径。

### 7. 注意事项

- 标记符号使用英文标点。
- 标题的 `#` 和列表的 `-` 后面要有空格。
- 段落之间空一行，列表和代码块前后也建议空一行。
- Ctrl + S 只保存本地文件；更新到 GitHub 还需要暂存、提交和推送。
- 推送后在 GitHub 打开 `.md` 文件，检查实际显示效果。
