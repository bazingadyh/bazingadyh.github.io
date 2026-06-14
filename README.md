# bazingadyh.github.io

我的个人技术博客，使用 Hugo + PaperMod 主题构建。

## 🚀 快速开始

### 本地开发

```bash
# 安装依赖（如有）
npm install

# 启动开发服务器
hugo server -D

# 访问地址
http://localhost:1313/
```

### 构建部署

```bash
# 构建生产版本
hugo

# 提交代码（自动触发 GitHub Actions 部署）
git add .
git commit -m "Update content"
git push origin main
```

## 📁 项目结构

```
.
├── content/           # 文章内容
│   ├── posts/         # 博客文章
│   ├── about.md       # 关于页面
│   ├── links.md       # 友链页面
│   └── ...
├── static/           # 静态资源
│   └── images/       # 图片目录
├── themes/           # Hugo 主题
├── hugo.toml         # Hugo 配置
└── README.md         # 项目说明
```

## ✨ 功能特性

- ✅ 响应式设计
- ✅ 暗色/亮色模式
- ✅ 代码高亮
- ✅ 文章搜索
- ✅ 评论系统（Giscus）
- ✅ RSS 订阅
- ✅ SEO 优化

## 📝 写作指南

创建新文章：
```bash
hugo new posts/YYYY-MM-DD-文章标题.md
```

## 📄 License

MIT