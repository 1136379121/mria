# 将项目发布到 GitHub 的完整指南

## 前置准备

### 1. 安装 Git

如果您的系统上还没有安装 Git，请先下载安装：

- **下载地址**：https://git-scm.com/download/win
- 安装完成后，重启命令行工具

### 2. 配置 Git（首次使用需要）

打开 PowerShell 或命令提示符，执行以下命令：

```bash
git config --global user.name "您的用户名"
git config --global user.email "您的邮箱"
```

## 发布步骤

### 步骤 1：初始化 Git 仓库

在项目根目录（`D:\Mria-Cursor\Mria-C`）打开 PowerShell，执行：

```bash
git init
```

### 步骤 2：添加所有文件到暂存区

```bash
git add .
```

### 步骤 3：创建首次提交

```bash
git commit -m "初始提交：添加项目文档、原型和UI设计"
```

### 步骤 4：在 GitHub 上创建新仓库

1. 登录 GitHub（如果没有账号，请先注册：https://github.com）
2. 点击右上角的 "+" 号，选择 "New repository"
3. 填写仓库信息：
   - **Repository name**: `Mria-C`（或您喜欢的名称）
   - **Description**: `Mria 项目 - 包含需求文档、原型和UI设计`
   - **Visibility**: 选择 Public（公开）或 Private（私有）
   - **不要**勾选 "Initialize this repository with a README"（因为本地已有文件）
4. 点击 "Create repository"

### 步骤 5：连接远程仓库并推送

GitHub 创建仓库后，会显示仓库地址，格式类似：`https://github.com/您的用户名/Mria-C.git`

然后执行以下命令（**请将 URL 替换为您的实际仓库地址**）：

```bash
# 添加远程仓库
git remote add origin https://github.com/您的用户名/Mria-C.git

# 将代码推送到 GitHub
git branch -M main
git push -u origin main
```

如果 GitHub 要求身份验证，您可能需要：
- 使用 **Personal Access Token**（推荐）：
  1. GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)
  2. 生成新 token，勾选 `repo` 权限
  3. 推送时使用 token 作为密码

- 或者使用 **GitHub CLI**：
  ```bash
  gh auth login
  ```

## 后续更新

以后如果修改了文件，使用以下命令更新 GitHub：

```bash
git add .
git commit -m "描述您的更改"
git push
```

## 常见问题

### Q: 如果推送时提示需要身份验证怎么办？
A: GitHub 已不再支持密码验证，请使用 Personal Access Token 或 SSH 密钥。

### Q: 如何创建 SSH 密钥？
A: 执行以下命令生成 SSH 密钥：
```bash
ssh-keygen -t ed25519 -C "您的邮箱"
```
然后将 `~/.ssh/id_ed25519.pub` 的内容添加到 GitHub → Settings → SSH and GPG keys

### Q: 如何忽略某些文件？
A: 编辑项目根目录的 `.gitignore` 文件，添加要忽略的文件或目录。

## 快速命令总结

```bash
# 初始化仓库
git init

# 添加文件
git add .

# 提交更改
git commit -m "提交说明"

# 添加远程仓库（仅首次）
git remote add origin https://github.com/您的用户名/仓库名.git

# 推送到 GitHub
git push -u origin main
```
