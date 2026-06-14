+++
title = "GitHub Pages 部署指南"
date = "2024-01-01"
draft = false
+++

## GitHub Pages 部署步骤

### 1. 仓库设置

你的博客仓库地址：`https://github.com/bazingadyh/bazingadyh.github.io`

**重要说明**：
- 仓库名为 `bazingadyh.github.io`，这是 GitHub Pages 的特殊命名规则
- GitHub 会自动将此仓库部署到 `https://bazingadyh.github.io/`
- 无需额外配置域名

### 2. 启用 GitHub Pages

1. 进入仓库的 **Settings** 页面
2. 找到 **Pages** 选项
3. 在 **Source** 中选择：
   - **Branch**: `main` 或 `master`
   - **Folder**: `/(root)` 或 `/docs`
4. 点击 **Save**

### 3. 部署方式选择

#### 方式一：直接部署 public 目录（推荐）

将 Hugo 生成的 `public/` 目录内容推送到仓库：

```bash
# 构建博客
hugo

# 进入 public 目录
cd public

# 初始化 Git（如果还没有）
git init
git add .
git commit -m "Initial deployment"

# 推送到 GitHub
git remote add origin https://github.com/bazingadyh/bazingadyh.github.io.git
git push -u origin main
```

#### 方式二：使用 GitHub Actions 自动部署（推荐）

创建 `.github/workflows/deploy.yml` 文件：

```yaml
name: Deploy Hugo site to Pages

on:
  push:
    branches:
      - main
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
        with:
          submodules: recursive
      
      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: 'latest'
          extended: true
      
      - name: Build
        run: hugo --minify
      
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: ./public

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

### 4. 配置 Giscus 评论系统

#### 步骤一：启用 Discussions

1. 进入仓库 **Settings**
2. 在 **Features** 中勾选 **Discussions**
3. 创建一个 Discussion 分类，命名为 `Announcements`

#### 步骤二：安装 Giscus App

1. 访问 https://github.com/apps/giscus
2. 点击 **Install**
3. 选择你的仓库 `bazingadyh/bazingadyh.github.io`
4. 授权访问

#### 步骤三：获取配置参数

1. 访问 https://giscus.app/zh-CN
2. 输入仓库：`bazingadyh/bazingadyh.github.io`
3. 选择映射方式：`pathname`
4. 选择分类：`Announcements`
5. 复制生成的 `repo-id` 和 `category-id`

#### 步骤四：更新配置

更新 `hugo.toml` 文件：

```toml
[params.giscus]
  enable = true
  repo = "bazingadyh/bazingadyh.github.io"
  repoId = "从 giscus.app 获取的 repo-id"
  category = "Announcements"
  categoryId = "从 giscus.app 获取的 category-id"
  mapping = "pathname"
  reactionsEnabled = "1"
  emitMetadata = "0"
  inputPosition = "top"
  theme = "light"
  lang = "zh-CN"
  loading = "lazy"
```

### 5. 验证部署

部署完成后，访问以下地址验证：

- **博客地址**：https://bazingadyh.github.io/
- **RSS 订阅**：https://bazingadyh.github.io/index.xml
- **网站地图**：https://bazingadyh.github.io/sitemap.xml

### 6. 更新博客流程

#### 使用 GitHub Actions 自动部署

```bash
# 创建新文章
hugo new posts/新文章.md

# 编辑文章内容
# ...

# 本地预览
hugo server -D

# 推送到 GitHub（自动触发部署）
git add .
git commit -m "Add new post"
git push
```

#### 手动部署

```bash
# 创建新文章
hugo new posts/新文章.md

# 编辑文章内容
# ...

# 本地预览
hugo server -D

# 构建
hugo

# 部署到 GitHub
cd public
git add .
git commit -m "Update blog"
git push
```

### 7. 常见问题

#### Q: 为什么我的博客没有更新？

A: 检查以下几点：
1. GitHub Pages 是否正确配置
2. 是否正确推送了 `public/` 目录内容
3. GitHub Actions 是否成功运行（如果使用自动部署）

#### Q: 如何查看部署状态？

A: 
1. 进入仓库的 **Actions** 页面查看工作流状态
2. 进入仓库的 **Pages** 页面查看部署状态

#### Q: 如何自定义域名？

A:
1. 在仓库 **Settings** → **Pages** → **Custom domain** 中添加域名
2. 在域名 DNS 设置中添加 CNAME 记录指向 `bazingadyh.github.io`
3. 更新 `hugo.toml` 中的 `baseURL`

### 8. 推送当前项目

如果你还没有推送当前项目到 GitHub，执行以下命令：

```bash
# 初始化 Git（如果还没有）
git init

# 添加所有文件
git add .

# 提交
git commit -m "Initial blog setup"

# 添加远程仓库
git remote add origin https://github.com/bazingadyh/bazingadyh.github.io.git

# 推送到 GitHub
git push -u origin main
```

---

祝你博客部署成功！如果有任何问题，可以查阅 GitHub Pages 官方文档或 Hugo 官方文档。