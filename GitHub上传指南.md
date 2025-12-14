# 将项目上传到 GitHub 的完整指南

## 前置要求

1. **安装 Git**
   - 下载地址: https://git-scm.com/download/win
   - 安装后重启终端或 IDE

2. **GitHub 账号**
   - 如果没有，请先注册: https://github.com/signup

## 步骤 1: 检查 Git 安装

打开 PowerShell 或命令提示符，运行：

```bash
git --version
```

如果显示版本号，说明 Git 已安装。

## 步骤 2: 初始化 Git 仓库

在项目根目录（`C:\Users\Lenovo\Desktop\111`）运行：

```bash
# 初始化 Git 仓库
git init

# 检查当前状态
git status
```

## 步骤 3: 配置 Git（首次使用需要）

```bash
# 设置用户名（替换为你的 GitHub 用户名）
git config --global user.name "你的用户名"

# 设置邮箱（替换为你的 GitHub 邮箱）
git config --global user.email "your.email@example.com"
```

## 步骤 4: 添加文件到 Git

```bash
# 添加所有文件（.gitignore 会自动排除不需要的文件）
git add .

# 查看将要提交的文件
git status
```

**注意**: `.env.local` 文件会被自动忽略，不会上传到 GitHub（这是安全的）。

## 步骤 5: 创建首次提交

```bash
# 创建提交
git commit -m "Initial commit: ClearView AI project"
```

## 步骤 6: 在 GitHub 上创建仓库

1. 登录 GitHub: https://github.com
2. 点击右上角的 **+** 号，选择 **New repository**
3. 填写仓库信息：
   - **Repository name**: `clearview-ai` (或你喜欢的名字)
   - **Description**: `AI-powered watermark remover and video restorer using Google Gemini`
   - **Visibility**: 选择 Public（公开）或 Private（私有）
   - **不要**勾选 "Initialize this repository with a README"（因为我们已经有了）
4. 点击 **Create repository**

## 步骤 7: 连接本地仓库到 GitHub

GitHub 创建仓库后会显示连接命令，类似这样：

```bash
# 添加远程仓库（替换 YOUR_USERNAME 和 YOUR_REPO_NAME）
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git

# 例如：
# git remote add origin https://github.com/yourusername/clearview-ai.git
```

## 步骤 8: 推送代码到 GitHub

```bash
# 推送代码到 GitHub（首次推送）
git branch -M main
git push -u origin main
```

如果提示输入用户名和密码：
- **用户名**: 你的 GitHub 用户名
- **密码**: 使用 **Personal Access Token**（不是 GitHub 密码）
  - 获取 Token: https://github.com/settings/tokens
  - 点击 "Generate new token (classic)"
  - 勾选 `repo` 权限
  - 复制生成的 token 作为密码使用

## 步骤 9: 验证上传

访问你的 GitHub 仓库页面，应该能看到所有代码文件。

## 后续更新代码

当你修改代码后，使用以下命令更新 GitHub：

```bash
# 查看修改的文件
git status

# 添加修改的文件
git add .

# 提交修改
git commit -m "描述你的修改内容"

# 推送到 GitHub
git push
```

## 重要提示

### ✅ 会被上传的文件
- 所有源代码文件（`.tsx`, `.ts`, `.json` 等）
- 配置文件（`vite.config.ts`, `tsconfig.json` 等）
- README.md 和文档文件

### ❌ 不会被上传的文件（已在 .gitignore 中）
- `node_modules/` - 依赖包（太大，不需要上传）
- `.env.local` - 包含 API Key 的敏感文件
- `dist/` - 构建输出
- 编辑器配置文件

### 🔒 安全建议

1. **永远不要**将 API Key 提交到 GitHub
2. 如果意外提交了敏感信息：
   ```bash
   # 从 Git 历史中删除文件
   git rm --cached .env.local
   git commit -m "Remove sensitive file"
   git push
   ```

3. 在 README 中说明如何配置环境变量：
   ```markdown
   ## 环境配置
   
   创建 `.env.local` 文件并添加：
   ```
   GEMINI_API_KEY=你的API密钥
   ```
   ```

## 常见问题

### Q: 如何更新 README.md？
A: 编辑 README.md 文件，然后：
```bash
git add README.md
git commit -m "Update README"
git push
```

### Q: 如何创建新的分支？
A: 
```bash
git checkout -b feature/新功能名称
# 进行修改后
git add .
git commit -m "添加新功能"
git push -u origin feature/新功能名称
```

### Q: 如何回退到之前的版本？
A:
```bash
# 查看提交历史
git log

# 回退到指定提交（替换 COMMIT_ID）
git reset --hard COMMIT_ID
```

## 完成！

现在你的项目已经成功上传到 GitHub 了！🎉

其他人可以通过以下方式克隆你的项目：

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
cd YOUR_REPO_NAME
npm install
# 创建 .env.local 并配置 API Key
npm run dev
```

