---
title: "使用 Jekyll 和 GitHub Pages 搭建并更新个人博客"  # 文章标题
date: 2025-02-20         # 发布日期
categories: [方法记录]       # 分类
tags: [github.io, 个人网页, 教程]       # 标签
---
1. **本地修改** ：添加新文章或修改配置。
2. **本地预览** ：运行 `bundle exec jekyll s`，查看效果。
3. **提交修改** ：用 `git add`、`git commit` 和 `git push` 推送到 GitHub。
4. **自动发布** ：GitHub Actions 会自动构建并发布博客。

## 1. **Jekyll 和 GitHub Pages 的关系**

- **Jekyll**：一个静态网站生成器，可以将 Markdown 文件转换成网页。
- **GitHub Pages**：GitHub 提供的免费托管服务，用于发布静态网站。
- **VSCode**：一个代码编辑器，用于编写博客内容和修改配置文件。

## 2. **搭建博客的步骤**

### **2.1 准备工作**

1. 安装 Ruby、Jekyll 和 Bundler：
   - 按照 [Jekyll 官方文档](https://jekyllrb.com/docs/installation/) 安装 Ruby 和 Jekyll。
   - 安装 Bundler：`gem install bundler`。
2. 安装 Git：
   - 下载并安装 [Git](https://git-scm.com/)。

### **2.2 创建博客仓库**

#### **方法一：使用 Chirpy Starter（推荐）**

1. 打开 [Chirpy Starter](https://github.com/cotes2020/chirpy-starter) 页面。
2. 点击 **“Use this template”** 按钮，创建一个新的仓库。
3. 将仓库命名为 `<你的GitHub用户名>.github.io`。
4. 克隆仓库到本地：
   ```bash
   git clone https://github.com/<你的GitHub用户名>/<你的GitHub用户名>.github.io
   ```

#### **方法二：Fork Chirpy 仓库（不推荐）**

1. 打开 [Chirpy](https://github.com/cotes2020/chirpy) 仓库。
2. 点击 “Fork” 按钮，将仓库复制到你的 GitHub 账号下。
3. 将仓库重命名为 `<你的GitHub用户名>.github.io`。
   克隆到本地：

```
git clone https://github.com/<你的GitHub用户名>/<你的GitHub用户名>.github.io
```

### 2.3 安装依赖：

1. 进入博客文件夹：

```
cd <你的GitHub用户名>.github.io
```

2. 安装依赖：

```
bundle install
```

本地调试
启动本地服务器：

```
bundle exec jekyll s
```

打开浏览器，访问 `http://localhost:4000`，查看博客效果。

### **发布到 GitHub Pages**

1. 确保有 `.github/workflows/pages-deploy.yml` 文件。
2. 将修改推送到 GitHub：

```
git add .
git commit -m "第一次提交"
git push origin main
```

1. 打开 GitHub，进入仓库的 **Settings** → **Pages** ，选择  **GitHub Actions** 。
2. 访问 `https://<你的GitHub用户名>.github.io`，查看发布的博客。

## 3. **更新博客页面**

### **本地修改内容**

#### **发布新文章**

1. 在 `_posts` 文件夹中新建 Markdown 文件，文件名格式为：`YYYY-MM-DD-标题.md`。
2. 在文件开头添加 Front Matter：

```
---
title: "我的第一篇博客"
date: 2024-02-01
categories: [生活]
tags: [博客, 教程]
---
```

3. 编写博客内容。

#### **修改配置**

* 打开克隆到本地的博客仓库。
* 在仓库根目录下找到 `_config.yml` 文件，并编辑它。
* 修改以下配置项：
  - `title`: 博客标题。
  - `description`: 博客描述。
  - `author`: 作者名称。
  - `url`: 博客网址。
  - `permalink`: 文章链接格式。
  - `timezone`: 时区。
  - `theme`: 主题。

#### **调整样式**

1. 编辑 `assets/css/style.scss` 或 `_sass/variables-hook.scss` 文件。

### **本地预览**

1. 启动本地服务器：

```
bundle exec jekyll s
```

2. 访问 `http://localhost:4000`，查看修改效果。

### **提交修改到 GitHub**

1. 添加修改的文件：

```
git add .
```

2. 提交修改：

```
git commit -m "更新：发布新文章《我的第一篇博客》"
```

3. 推送到 GitHub：

```
git push origin main
```

### **自动发布**

1. GitHub Actions 会自动构建并发布博客。
2. 访问 `https://<你的GitHub用户名>.github.io`，查看更新后的博客。

## 4. **常见问题**

* **修改后没生效？**
  确保文件路径和格式正确，重启本地服务器。
* **图片不显示？**
  确保图片放在 `assets/img` 文件夹中，路径正确。
* **评论功能失效？**
  检查 `_layouts/post.html` 中的评论代码是否正确。
