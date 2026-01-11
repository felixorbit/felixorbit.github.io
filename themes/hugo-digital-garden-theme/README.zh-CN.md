# Hugo Digital Garden 主题使用说明

[English](./README.md) | 中文

一个受 Maggie Appleton 网站启发的 Hugo 数字花园主题。

[**在线演示**](https://hugo-digital-garden-demo.netlify.app/)

![首页截图](https://github.com/paulmartins/hugo-digital-garden-theme/blob/main/images/screenshot.png)

## 目录

- [功能特点](#功能特点)
- [快速开始](#快速开始)
- [安装主题](#安装主题)
- [配置说明](#配置说明)
- [内容组织](#内容组织)
- [内容状态系统](#内容状态系统)
- [Frontmatter 字段参考](#frontmatter-字段参考)
- [短代码](#短代码)
- [自定义样式](#自定义样式)
- [更新主题](#更新主题)

---

## 功能特点

- **数字花园** - 带有标签过滤功能的博客文章
- **项目展示** - 个人作品集页面
- **读书笔记** - 书籍笔记管理
- **深色模式** - 支持明暗主题切换
- **响应式设计** - 适配各种设备
- **Mermaid 图表** - 支持流程图、时序图等
- **图片处理** - 内置图片缩放、裁剪等处理

---

## 快速开始

1. **安装 Hugo**

   推荐使用扩展版本（Extended Edition）以支持 SCSS/SASS 等功能：

   ```bash
   # macOS
   brew install hugo

   # Windows (Chocolatey)
   choco install hugo-extended

   # Linux
   sudo apt install hugo
   ```

   验证安装：
   ```bash
   hugo version
   ```

2. **创建新站点**

   ```bash
   hugo new site my-digital-garden
   cd my-digital-garden
   ```

---

## 安装主题

### 方法一：Git 子模块（推荐）

```bash
git submodule add https://github.com/paulmartins/hugo-digital-garden-theme.git themes/hugo-digital-garden-theme
```

### 方法二：直接克隆

```bash
cd themes
git clone https://github.com/paulmartins/hugo-digital-garden-theme.git
```

编辑站点的 `config.toml`，添加主题：

```toml
theme = "hugo-digital-garden-theme"
```

---

## 配置说明

### 基础配置

编辑站点根目录下的 `config.toml`：

```toml
baseURL = "https://your-domain.com"
languageCode = "zh-cn"
title = "我的数字花园"
theme = "hugo-digital-garden-theme"
```

### 参数配置

在 `[params]` 部分配置网站信息：

```toml
[params]
  name = "你的名字"
  description = "你的个人简介"
  initials = "NM"  # 显示在导航栏的缩写
  googleAnalytics = "G-XXXXXXXXXX"  # Google Analytics ID（可选）

  # 社交链接
  [[params.social]]
    name = "Twitter"
    link = "https://twitter.com/yourname"
    icon = "fab fa-twitter"

  [[params.social]]
    name = "GitHub"
    link = "https://github.com/yourname"
    icon = "fab fa-github"

  [[params.social]]
    name = "Medium"
    link = "https://medium.com/@yourname"
    icon = "fab fa-medium-m"
```

### 菜单配置

```toml
[menu]
  [[menu.main]]
    name = "数字花园"
    url = "/garden/"
    weight = 1

  [[menu.main]]
    name = "项目"
    url = "/projects/"
    weight = 2

  [[menu.main]]
    name = "读书库"
    url = "/library/"
    weight = 3

  [[menu.main]]
    name = "关于"
    url = "/about/"
    weight = 4
```

### 分类法配置

```toml
[taxonomies]
  garden_tags = 'garden_tags'     # 花园文章的标签
  project_tags = 'project_tags'   # 项目的标签
  library_tags = 'library_tags'   # 读书笔记的标签
```

### Markdown 渲染配置

```toml
[markup]
  defaultMarkdownHandler = 'goldmark'
  [markup.goldmark.renderer]
    unsafe = true  # 允许渲染原始 HTML
  [markup.goldmark.parser]
    autoHeadingID = true
    autoHeadingIDType = 'github'
  [markup.highlight]
    style = 'monokailight'  # 代码高亮主题
```

---

## 内容组织

主题支持三种类型的内容，放在 `content` 目录下：

```
content/
├── garden/       # 数字花园（博客文章）
│   ├── _index.md
│   └── my-post.md
├── projects/     # 项目展示
│   ├── _index.md
│   └── my-project/
│       └── index.md
├── library/      # 读书笔记
│   ├── _index.md
│   └── my-book/
│       └── index.md
└── about/        # 关于页面
    └── index.md
```

### 花园文章示例

`content/garden/my-article.md`:

```yaml
---
title: "我的第一篇文章"
date: 2024-01-01
lastmod: 2024-01-15
draft: false
garden_tags: ["技术", "编程"]
summary: "文章摘要，用于显示在卡片上"
status: "growing"
---

# 文章内容

这里是文章的正文内容...
```

### 项目示例

`content/projects/my-project/index.md`:

```yaml
---
title: "我的项目"
date: 2024-01-01
draft: false
project_tags: ["Web", "React"]
status: "evergreen"
weight: 1
summary: "项目简介"
links:
    external_link:
        text: "在线演示"
        icon: "fas fa-external-link-alt"
        href: "https://demo.example.com"
        weight: 1
    github_link:
        text: "源代码"
        icon: "fab fa-github"
        href: "https://github.com/your/project"
        weight: 2
---

项目详细介绍...
```

### 读书笔记示例

`content/library/my-book/index.md`:

```yaml
---
title: "书名"
author: "作者名"
date: 2024-01-01
draft: false
library_tags: ["编程", "设计"]
summary: "这本书的简短描述"
---

笔记内容...
```

### 首页内容展示

首页会展示各内容类型的最新内容，数量限制如下：

| 内容类型 | 展示数量 |
|---------|---------|
| Garden（花园文章） | 6 条 |
| Projects（项目展示） | 6 条 |
| Library（读书笔记） | 3 条 |

内容按日期降序排列（最新的排在前面）。如需修改展示数量，需要编辑 `layouts/index.html` 文件中的 `first N` 数值。

### 排序规则说明

| 页面 | 排序字段 | 排序方式 |
|------|---------|---------|
| 首页 | `lastmod`（最后修改日期） | 降序（最新在前） |
| Garden 列表页 | `publishdate`（发布日期） | 降序 |
| Projects 列表页 | `publishdate`（发布日期） | 降序 |
| Library 列表页 | `publishdate`（发布日期） | 降序 |

首页使用 `site.RegularPages`，列表页使用 `.Pages.ByPublishDate.Reverse`。

### 自定义排序

如需使用其他排序方式，可以修改模板：

```go
// 按 weight 排序
{{ range .Pages.ByWeight }}

// 按标题字母排序
{{ range .Pages.ByTitle }}

// 按日期升序（最老的在前）
{{ range .Pages.ByPublishDate }}
```

---

## 内容状态系统

主题支持使用 `status` 字段标记内容的成熟度：

| 状态 | 值 | 显示 | 含义 |
|------|-----|------|------|
| 播种 | `seeding` | 🌱 Seeding | 新开始的内容 |
| 生长 | `growing` | 🌿 Growing | 正在完善的内容 |
| 常青 | `evergreen` | 🌳 Evergreen | 成熟完善的内容 |

在文章 front matter 中设置：

```yaml
status: "seeding"   # 新文章
status: "growing"   # 进行中的文章
status: "evergreen" # 完成的文章
```

---

## Frontmatter 字段参考

主题中的内容使用 YAML front matter 定义元数据。以下是所有支持的字段：

### 通用字段

所有内容类型都支持以下字段：

| 字段 | 说明 | 示例 |
|------|------|------|
| `title` | 文章标题 | `title: "我的文章"` |
| `date` | 发布日期 | `date: 2024-01-01` |
| `lastmod` | 最后修改日期 | `lastmod: 2024-01-15` |
| `draft` | 草稿状态，设为 `true` 则不会发布 | `draft: false` |
| `summary` | 摘要，显示在卡片和搜索结果中 | `summary: "这是文章摘要"` |
| `status` | 内容成熟度状态 | `status: "growing"` |
| `tags` | 通用标签（显示在文章顶部） | `tags: ["tech", "programming"]` |

### Garden（花园文章）专用字段

| 字段 | 说明 | 示例 |
|------|------|------|
| `garden_tags` | 花园标签，用于分类和过滤 | `garden_tags: ["编程", "笔记"]` |

### Projects（项目展示）专用字段

| 字段 | 说明 | 示例 |
|------|------|------|
| `project_tags` | 项目标签，用于分类和过滤 | `project_tags: ["web", "react"]` |
| `weight` | 排序权重，数字越小越靠前 | `weight: 1` |
| `links` | 外部链接列表，显示在项目标题下方 | 详见下方示例 |

#### links 配置示例

```yaml
links:
    demo:
        text: "在线演示"
        icon: "fas fa-external-link-alt"
        href: "https://demo.example.com"
        weight: 1
    github:
        text: "源代码"
        icon: "fab fa-github"
        href: "https://github.com/your/project"
        weight: 2
    docs:
        text: "文档"
        icon: "fas fa-book"
        href: "https://docs.example.com"
        weight: 3
```

可用的图标类（FontAwesome）：
- 外部链接: `fas fa-external-link-alt`
- GitHub: `fab fa-github`
- 文档: `fas fa-book`
- 下载: `fas fa-download`

### Library（读书笔记）专用字段

| 字段 | 说明 | 示例 |
|------|------|------|
| `library_tags` | 读书笔记标签，用于分类和过滤 | `library_tags: ["技术", "设计"]` |
| `author` | 作者姓名 | `author: "鲁迅"` |
| `Imgonly` | 设为 `true` 仅显示封面图片 | `Imgonly: true` |

### 特色图片

对于 **Projects** 和 **Library** 类型的内容，可以在内容目录中添加封面图片：

```
content/projects/my-project/
├── index.md          # 项目内容
└── featured.jpg      # 封面图片（命名为 featured.*）

content/library/my-book/
├── index.md          # 读书笔记
└── featured.png      # 封面图片
```

主题会自动识别并处理这些图片。

### 完整示例对比

**Garden 文章：**
```yaml
---
title: "深入理解 Go 语言"
date: 2024-01-01
lastmod: 2024-01-15
draft: false
garden_tags: ["编程", "Go语言"]
summary: "本文深入介绍 Go 语言的核心特性..."
status: "evergreen"
tags: ["技术"]
---

# 正文内容
```

**Project 项目：**
```yaml
---
title: "任务管理系统"
date: 2024-01-01
draft: false
project_tags: ["Web", "FullStack"]
status: "evergreen"
weight: 1
summary: "一个基于 Vue 和 Node.js 的任务管理应用"
links:
    demo:
        text: "在线演示"
        icon: "fas fa-external-link-alt"
        href: "https://demo.example.com"
        weight: 1
    github:
        text: "源代码"
        icon: "fab fa-github"
        href: "https://github.com/your/project"
        weight: 2
---

项目详细介绍...
```

**Library 读书笔记：**
```yaml
---
title: "代码整洁之道"
author: "Robert C. Martin"
date: 2024-01-01
draft: false
library_tags: ["编程", "软件工程"]
summary: "编写优雅代码的实践指南"
status: "growing"
Imgonly: false
---

读书笔记内容...
```

---

## 短代码

### 图片处理

```markdown
{{< image "filename.jpg" "Resize" "800x" >}}
```

支持的图像处理命令：

- `Fit` - 按比例缩放，适应指定尺寸
- `Resize` - 按指定尺寸缩放
- `Fill` - 填充到指定尺寸（可能裁剪）
- `Crop` - 裁剪到指定尺寸

带标题的图像：

```markdown
{{< image "photo.jpg" "Fit" "600x" >}}
这是图片的标题
{{< /image >}}
```

使用 Hugo 内置的 figure 短代码：

```markdown
{{< figure src="image.jpg" title="图片标题" width="100%" attr="作者" link="https://example.com" >}}
```

### Mermaid 图表

```markdown
{{< mermaid align="center" >}}
graph TD
    A[开始] --> B{判断}
    B -->|是| C[执行]
    B -->|否| D[结束]
{{< /mermaid >}}
```

支持的图表类型：
- `graph` / `graph TD` - 流程图
- `sequenceDiagram` - 时序图
- `classDiagram` - 类图
- `stateDiagram` - 状态图
- `pie` - 饼图
- `gantt` - 甘特图

### Bootstrap 栅格布局

```markdown
{{< row class="justify-content-center" >}}
{{< column col="6" >}}
左侧内容
{{< /column >}}
{{< column col="6" >}}
右侧内容
{{< /column >}}
{{< /row >}}
```

---

## 自定义样式

### 创建自定义 CSS

在站点根目录创建 `static/css/my_style.css`，该文件会自动覆盖主题的默认样式。

示例：

```css
/* 自定义表格样式 */
table {
  border-collapse: collapse;
  width: 100%;
}

table th {
  background-color: #f8f9fa;
  font-weight: bold;
}

/* 自定义字体 */
body {
  font-family: 'Noto Sans SC', sans-serif;
}

/* 自定义链接颜色 */
a {
  color: #0A94C8;
}
```

参考：[示例自定义 CSS 文件](https://github.com/IdiosApps/IdiosApps.github.io/blob/main/static/css/my_style.css)

### 禁用深色模式

如需禁用深色模式功能，需要修改主题源码或覆盖相关 CSS。

---

## 启动开发服务器

在站点根目录运行：

```bash
hugo server
```

访问 http://localhost:1313 查看站点。

### 测试主题

如果想在 exampleSite 目录测试主题：

```bash
cd themes/hugo-digital-garden-theme/exampleSite
hugo server --themesDir ../../
```

---

## 更新主题

### 使用 Git 子模块

```bash
git submodule update --remote --rebase
```

### 直接克隆

```bash
cd themes/hugo-digital-garden-theme
git pull
```

---

## 字体说明

主题默认使用以下 Google Fonts：

| 用途 | 字体 |
|------|------|
| 标题 | Mulish |
| 正文 | Frank Ruhl Libre |
| 副标题 | Encode Sans Semi Condensed |

---

## 参考链接

- [Hugo 官方文档](https://gohugo.io/documentation/)
- [Maggie Appleton's Digital Garden](https://maggieappleton.com/)
- [Markdown 语法指南](https://www.markdownguide.org/basic-syntax/)
- [Mermaid 文档](https://mermaid.js.org/)
