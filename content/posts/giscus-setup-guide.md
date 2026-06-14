+++
title = "Giscus 评论系统配置说明"
date = "2024-01-01"
draft = false
+++

## Giscus 评论系统配置步骤

### 1. 创建 GitHub 仓库

1. 在 GitHub 上创建一个新的公开仓库，用于存放评论数据
2. 仓库名建议：`blog-comments` 或 `yourusername-blog-comments`

### 2. 启用 Discussions

1. 进入仓库设置（Settings）
2. 在 Features 中勾选 "Discussions"
3. 创建一个新的 Discussion 分类，建议命名为 "Announcements"

### 3. 安装 Giscus App

1. 访问 https://github.com/apps/giscus
2. 点击 "Install"
3. 选择你创建的评论仓库
4. 授权 Giscus App 访问该仓库

### 4. 获取配置参数

访问 https://giscus.app/zh-CN，按照以下步骤：

1. 输入你的仓库地址（如：`bazingadyh/blog-comments`）
2. 选择页面 ↔️ Discussions 映射关系（推荐：pathname）
3. 选择 Discussion 分类（推荐：Announcements）
4. 选择主题（推荐：light 或 preferred_color_scheme）
5. 复制生成的配置参数

### 5. 更新 hugo.toml 配置

将获取的参数更新到 `hugo.toml` 文件中：

```toml
[params.giscus]
  enable = true
  repo = "yourusername/blog-comments"
  repoId = "从 giscus.app 获取"
  category = "Announcements"
  categoryId = "从 giscus.app 获取"
  mapping = "pathname"
  reactionsEnabled = "1"
  emitMetadata = "0"
  inputPosition = "top"
  theme = "light"
  lang = "zh-CN"
  loading = "lazy"
```

### 6. 测试评论功能

1. 运行 `hugo server -D` 启动本地服务器
2. 访问任意文章页面
3. 在页面底部应该能看到评论输入框

### 注意事项

- 仓库必须是公开的
- 必须启用 Discussions 功能
- 必须安装 Giscus App
- 评论数据存储在 GitHub Discussions 中

### 替代方案

如果你不想使用 Giscus，也可以选择：

1. **Utterances**：基于 GitHub Issues
2. **Waline**：支持邮件通知，需要后端服务
3. **Twikoo**：支持邮件通知，需要云函数服务