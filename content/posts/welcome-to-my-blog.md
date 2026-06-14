+++
title = "欢迎来到我的博客"
date = "2024-01-01"
draft = false
tags = ["博客", "Hugo", "教程"]
categories = ["技术"]
keywords = ["Hugo", "博客搭建", "静态博客"]
description = "这是我的第一篇博客文章，介绍了博客的搭建过程和主要功能。"
showToc = true
TocOpen = true
weight = 1

[cover]
  image = "images/cover.jpg"
  alt = "博客封面"
  caption = "我的博客"
  relative = false
+++

## 🎉 欢迎来到我的博客

这是我的第一篇博客文章，记录了博客的搭建过程和主要功能。

### 为什么选择 Hugo？

Hugo 是一个快速、现代的静态网站生成器，具有以下优势：

1. **构建速度快**：毫秒级构建时间
2. **易于使用**：简单的命令行工具
3. **主题丰富**：社区提供了大量主题
4. **Markdown 支持**：使用 Markdown 编写文章
5. **部署简单**：可以部署到 GitHub Pages、Gitee Pages 等

### 博客功能展示

#### 代码高亮

支持多种编程语言的语法高亮：

```python
# Python 示例
def hello_world():
    print("Hello, World!")
    
hello_world()
```

```javascript
// JavaScript 示例
const greeting = (name) => {
    console.log(`Hello, ${name}!`);
};

greeting('World');
```

```go
// Go 示例
package main

import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```

#### 表格支持

| 功能 | 状态 | 说明 |
|------|------|------|
| 代码高亮 | ✅ | 支持多种语言 |
| 目录生成 | ✅ | 自动生成 TOC |
| 标签分类 | ✅ | 支持标签和分类 |
| RSS 订阅 | ✅ | 自动生成 RSS |
| 搜索功能 | ✅ | 全文搜索 |

#### 数学公式

支持 LaTeX 数学公式：

行内公式：$E = mc^2$

块级公式：

$$
\frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
$$

#### 引用和提示

> 这是一段引用文字，可以用来强调重要内容。

#### 列表

有序列表：
1. 第一项
2. 第二项
3. 第三项

无序列表：
- 项目 A
- 项目 B
- 项目 C

#### 图片

![示例图片](/images/example.jpg)

### 博客搭建步骤

1. **安装 Hugo**
   ```bash
   # macOS
   brew install hugo
   
   # Windows
   choco install hugo-extended
   ```

2. **创建新站点**
   ```bash
   hugo new site my-blog
   cd my-blog
   ```

3. **添加主题**
   ```bash
   git init
   git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
   ```

4. **配置主题**
   编辑 `hugo.toml` 文件，设置主题和参数。

5. **创建文章**
   ```bash
   hugo new posts/my-first-post.md
   ```

6. **本地预览**
   ```bash
   hugo server -D
   ```

7. **构建部署**
   ```bash
   hugo
   ```

### 后续计划

- [ ] 添加评论系统
- [ ] 集成统计分析
- [ ] 添加更多自定义页面
- [ ] 优化 SEO
- [ ] 添加 RSS 订阅说明

### 联系方式

如果你有任何问题或建议，欢迎通过以下方式联系我：

- GitHub: [@bazingadyh](https://github.com/bazingadyh)
- Email: your@email.com

---

感谢你的阅读！希望这个博客能记录下我的成长历程，也希望能帮助到有需要的人。