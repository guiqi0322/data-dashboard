# 数据面板项目 - 配置指南

> 在新电脑上配置此项目的完整指南

---

## 📋 目录

1. [环境要求](#环境要求)
2. [快速配置](#快速配置)
3. [详细配置步骤](#详细配置步骤)
4. [日常使用](#日常使用)
5. [常见问题](#常见问题)

---

## 🖥️ 环境要求

- **Git**: [下载地址](https://git-scm.com/downloads)
- **文本编辑器**: VS Code / Sublime Text / 记事本（任意）
- **GitHub 账号**: https://github.com/

---

## 🚀 快速配置（5 分钟）

### 步骤 1：安装 Git

下载安装 Git：https://git-scm.com/downloads

安装时保持默认选项即可。

### 步骤 2：配置 Git

打开 **Git Bash** 或 **PowerShell**，执行：

```bash
# 配置用户信息
git config --global user.name "guiqi0322"
git config --global user.email "guiqi0322@users.noreply.github.com"

# 配置 SSH 命令（Windows 路径）
git config --global core.sshCommand "ssh -i C:/Users/你的用户名/.ssh/id_ed25519_github"

# 配置 deploy 别名
git config --global alias.deploy "!git add . && git commit -m 'deploy update' && git push"
```

### 步骤 3：配置 SSH Key

#### 检查是否已有 SSH Key

```bash
ls ~/.ssh/
# 或 Windows: dir %USERPROFILE%\.ssh\
```

如果看到 `id_ed25519_github` 和 `id_ed25519_github.pub`，跳到步骤 4。

#### 生成新的 SSH Key

```bash
ssh-keygen -t ed25519 -C "guiqi0322@users.noreply.github.com"
```

一路回车（使用默认设置）。

#### 复制公钥

```bash
# Linux/Mac
cat ~/.ssh/id_ed25519_github.pub

# Windows PowerShell
Get-Content $env:USERPROFILE\.ssh\id_ed25519_github.pub | clip

# Windows CMD
type %USERPROFILE%\.ssh\id_ed25519_github.pub
```

#### 添加到 GitHub

1. 打开：https://github.com/settings/keys
2. 点击 **New SSH key**
3. 填写：
   - **Title**: `Home PC`（或任意名字）
   - **Key Type**: `Authentication Key`
   - **Key**: 粘贴刚才复制的公钥
4. 点击 **Add SSH key**

#### 测试连接

```bash
ssh -T git@github.com
```

成功会显示：
```
Hi guiqi0322! You've successfully authenticated...
```

### 步骤 4：克隆项目

```bash
# 选择存放位置
cd C:\Projects  # 或你喜欢的目录

# 克隆项目
git clone git@github.com:guiqi0322/data-dashboard.git

# 进入项目目录
cd data-dashboard
```

### 步骤 5：验证配置

```bash
# 查看配置
git config --global --list

# 应该看到：
# user.name=guiqi0322
# user.email=guiqi0322@users.noreply.github.com
# core.sshcommand=ssh -i C:/Users/你的用户名/.ssh/id_ed25519_github
# alias.deploy=!git add . && git commit -m 'deploy update' && git push
```

---

## 📝 详细配置步骤

### Windows 系统

#### 1. 安装 Git

下载 Windows 版 Git：https://git-scm.com/download/win

安装时注意：
- 选择 **Use Git from Git Bash only** 或 **Git from the command line**
- 其他选项保持默认

#### 2. 打开 Git Bash

- 开始菜单搜索 **Git Bash**
- 或右键文件夹 → **Git Bash Here**

#### 3. 配置 Git

```bash
# 用户信息
git config --global user.name "guiqi0322"
git config --global user.email "guiqi0322@users.noreply.github.com"

# SSH 命令（注意路径用正斜杠）
git config --global core.sshCommand "ssh -i C:/Users/你的用户名/.ssh/id_ed25519_github"

# deploy 别名
git config --global alias.deploy "!git add . && git commit -m 'deploy update' && git push"
```

#### 4. 配置 SSH

```bash
# 生成 SSH Key
ssh-keygen -t ed25519 -C "guiqi0322@users.noreply.github.com"

# 复制公钥（Windows）
cat ~/.ssh/id_ed25519_github.pub
# 手动复制输出内容

# 或 PowerShell
Get-Content $env:USERPROFILE\.ssh\id_ed25519_github.pub | Set-Clipboard
```

添加到 GitHub：https://github.com/settings/keys

#### 5. 克隆项目

```bash
cd C:\Projects
git clone git@github.com:guiqi0322/data-dashboard.git
cd data-dashboard
```

---

### Mac 系统

#### 1. 安装 Git

```bash
# 通常会提示安装 Xcode Command Line Tools
git --version
```

或从 https://git-scm.com/download/mac 下载

#### 2. 配置 Git

```bash
git config --global user.name "guiqi0322"
git config --global user.email "guiqi0322@users.noreply.github.com"
git config --global core.sshCommand "ssh -i ~/.ssh/id_ed25519_github"
git config --global alias.deploy "!git add . && git commit -m 'deploy update' && git push"
```

#### 3. 配置 SSH

```bash
# 生成 SSH Key
ssh-keygen -t ed25519 -C "guiqi0322@users.noreply.github.com"

# 复制公钥
cat ~/.ssh/id_ed25519_github.pub | pbcopy
```

添加到 GitHub：https://github.com/settings/keys

#### 4. 克隆项目

```bash
cd ~/Projects
git clone git@github.com:guiqi0322/data-dashboard.git
cd data-dashboard
```

---

### Linux 系统

```bash
# 安装 Git
sudo apt install git  # Ubuntu/Debian
sudo yum install git  # CentOS/RHEL

# 配置 Git
git config --global user.name "guiqi0322"
git config --global user.email "guiqi0322@users.noreply.github.com"
git config --global core.sshCommand "ssh -i ~/.ssh/id_ed25519_github"
git config --global alias.deploy "!git add . && git commit -m 'deploy update' && git push"

# 生成 SSH Key
ssh-keygen -t ed25519 -C "guiqi0322@users.noreply.github.com"

# 复制公钥
cat ~/.ssh/id_ed25519_github.pub | xclip -selection clipboard

# 克隆项目
cd ~/Projects
git clone git@github.com:guiqi0322/data-dashboard.git
cd data-dashboard
```

---

## 📅 日常使用

### 修改代码并部署

```bash
# 1. 进入项目目录
cd E:\data-dashboard  # 或你的路径

# 2. 修改代码（用任何编辑器）
notepad index.html  # 或 VS Code、Sublime 等

# 3. 一键部署
git deploy
```

完成！1-2 分钟后网站自动更新。

### 查看修改状态

```bash
# 查看哪些文件被修改
git status

# 查看具体改了什么
git diff
```

### 撤销修改

```bash
# 撤销单个文件的修改
git checkout -- index.html

# 撤销所有修改
git checkout -- .
```

### 查看历史

```bash
# 查看提交历史
git log

# 查看最近 5 次提交
git log -5
```

---

## 🔧 常见问题

### 问题 1：`git: 'deploy' is not a git command`

**解决**：配置 deploy 别名

```bash
git config --global alias.deploy "!git add . && git commit -m 'deploy update' && git push"
```

---

### 问题 2：`Permission denied (publickey)`

**解决**：SSH Key 没有正确配置

```bash
# 1. 检查是否有 SSH Key
ls ~/.ssh/

# 2. 如果没有，生成新的
ssh-keygen -t ed25519 -C "guiqi0322@users.noreply.github.com"

# 3. 复制公钥到 GitHub
cat ~/.ssh/id_ed25519_github.pub
# 添加到：https://github.com/settings/keys

# 4. 配置 git 使用这个 key
git config --global core.sshCommand "ssh -i C:/Users/你的用户名/.ssh/id_ed25519_github"

# 5. 测试
ssh -T git@github.com
```

---

### 问题 3：`Failed to connect to github.com port 443: Timed out`

**解决**：网络问题，配置代理或使用 SSH

```bash
# 方法 1：使用 SSH 而不是 HTTPS
git remote set-url origin git@github.com:guiqi0322/data-dashboard.git

# 方法 2：配置代理（如果你有）
git config --global http.proxy http://127.0.0.1:7890
git config --global https.proxy http://127.0.0.1:7890
```

---

### 问题 4：`Your branch is behind 'origin/main'`

**解决**：拉取最新代码

```bash
git pull
```

---

### 问题 5：修改后网站没有更新

**解决**：GitHub Pages 需要 1-2 分钟构建

1. 检查是否成功推送：
   ```bash
   git log -1
   ```

2. 查看构建状态：
   https://github.com/guiqi0322/data-dashboard/actions

3. 清除浏览器缓存（Ctrl+Shift+R）

---

### 问题 6：SSH Key 文件名不同

如果你的 SSH Key 文件名不是 `id_ed25519_github`：

```bash
# 查看你的 SSH Key 文件
ls ~/.ssh/

# 假设文件名是 id_rsa
git config --global core.sshCommand "ssh -i C:/Users/你的用户名/.ssh/id_rsa"
```

---

## 📱 手机端修改

### 方法 1：GitHub 网页编辑

1. 手机浏览器打开：
   ```
   https://github.com/guiqi0322/data-dashboard/edit/main/index.html
   ```

2. 编辑代码

3. 点击 **Commit changes**

### 方法 2：使用其他 AI

给 AI 提供链接：
```
项目说明：https://raw.githubusercontent.com/guiqi0322/data-dashboard/main/AI_CONTEXT.md
代码文件：https://raw.githubusercontent.com/guiqi0322/data-dashboard/main/index.html
```

AI 修改后，在 GitHub 网页编辑提交。

---

## 🔗 快速参考

### 项目链接
- **在线访问**: https://guiqi0322.github.io/data-dashboard/
- **GitHub 仓库**: https://github.com/guiqi0322/data-dashboard
- **GitHub 编辑**: https://github.com/guiqi0322/data-dashboard/edit/main/index.html
- **Pages 设置**: https://github.com/guiqi0322/data-dashboard/settings/pages

### 常用命令
```bash
# 一键部署
git deploy

# 拉取最新代码
git pull

# 查看状态
git status

# 查看历史
git log -5

# 撤销修改
git checkout -- .
```

### 配置文件位置
- **Git 配置**: `~/.gitconfig`
- **SSH Key**: `~/.ssh/id_ed25519_github`
- **项目目录**: `E:\data-dashboard`（或你选择的路径）

---

## ✅ 配置检查清单

完成配置后，检查以下项目：

- [ ] Git 已安装
- [ ] Git 用户名和邮箱已配置
- [ ] SSH Key 已生成
- [ ] SSH Key 已添加到 GitHub
- [ ] SSH 连接测试成功
- [ ] 项目已克隆
- [ ] `git deploy` 命令可用
- [ ] 网站可以正常访问

---

## 🆘 获取帮助

如果遇到问题：

1. 查看 Git 错误信息
2. 检查网络连接
3. 确认 SSH Key 配置正确
4. 查看 GitHub Actions 构建状态

---

**配置完成后，你就可以在任何电脑上修改和部署项目了！** 🎉
