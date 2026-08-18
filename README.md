# 简洁学术个人主页模板

这是一套不需要安装任何框架、可直接放到 GitHub Pages 的极简静态主页模板。页面只保留照片与基本信息、两段个人介绍和论文列表，并支持手机浏览。

## 文件说明

```text
.
├─ index.html                    # 个人资料与页面内容：主要编辑这个文件
├─ styles.css                    # 颜色、字号、间距和手机端样式
├─ assets/
│  ├─ profile-placeholder.svg    # 示例头像，请换成自己的照片
│  └─ favicon.svg                # 浏览器标签页小图标
├─ .nojekyll                     # 告诉 GitHub 按纯静态网站发布
└─ README.md                     # 这份使用说明（不会显示在主页上）
```

## 一、先在电脑上预览

直接双击 `index.html`，它会在浏览器中打开。修改文件并保存后，在浏览器中按 `Ctrl + R` 刷新即可看到变化。

推荐使用 Visual Studio Code 编辑，但记事本也可以。

## 二、把示例内容换成自己的信息

打开 `index.html`，搜索“修改 1”到“修改 4”。这些注释依次标出了：

1. 标签页标题和搜索简介；
2. 照片、姓名、学校、邮箱和学术链接；
3. 两段个人介绍；
4. 论文列表。

不要删除形如 `<标签>` 和 `</标签>` 的尖括号结构，只替换它们中间的文字最安全。

### 替换头像

1. 准备一张正方形照片，推荐至少 `600 × 600` 像素；
2. 改名为 `profile.jpg`；
3. 放进 `assets` 文件夹；
4. 在 `index.html` 中找到：

```html
src="assets/profile-placeholder.svg"
```

改成：

```html
src="assets/profile.jpg"
```

同时把 `alt="Portrait of Your Name"` 中的姓名换成自己的姓名。

### 添加一篇论文

在 `Publications` 部分复制一整段：

```html
<article class="publication">
  ...
</article>
```

粘贴到下一篇论文前面或后面，然后替换年份、题目、作者、会议和链接。用 `<strong>Your Name</strong>` 加粗自己的名字。

### 修改颜色

打开 `styles.css`，最上方有两行主题色：

```css
--accent: #990000;
--gold: #d9ad3a;
```

只改这两个十六进制颜色值即可。可以在任意在线取色器中挑选颜色。

## 三、发布到 GitHub Pages（完全不会 GitHub 也可以）

### 第 1 步：确认邮箱已验证

登录 GitHub，依次打开头像 → **Settings** → **Emails**。确认主邮箱旁边显示已经验证。若未验证，先点击 GitHub 发来的验证邮件。

### 第 2 步：新建个人主页仓库

1. 点击 GitHub 右上角的 **+** → **New repository**；
2. **Owner** 选择 `27OExpert`；
3. **Repository name** 精确填写：

```text
27oexpert.github.io
```

4. 选择 **Public**；
5. 可以勾选 **Add a README file**，这样会直接建立 `main` 分支；
6. 点击 **Create repository**。

GitHub 要求用户名含大写字母时，个人主页仓库名使用全小写。这里的 `o` 是英文字母 o，不是数字 0。

### 第 3 步：上传模板

1. 进入刚建立的仓库；
2. 点击 **Add file** → **Upload files**；
3. 上传本模板中的 `index.html`、`styles.css`、`assets` 文件夹、`.nojekyll` 等内容；
4. 注意：要上传“文件夹里面的内容”，不能把最外层模板文件夹再套一层；
5. 上传后，仓库首页必须能直接看到全小写的 `index.html`；
6. 在页面底部点击 **Commit changes**。

### 第 4 步：开启 GitHub Pages

1. 进入仓库的 **Settings**；
2. 左侧点击 **Pages**；
3. 在 **Build and deployment** 中，将 **Source** 选择为 `Deploy from a branch`；
4. **Branch** 选择 `main`，文件夹选择 `/(root)`；
5. 点击 **Save**。

### 第 5 步：打开公开主页

GitHub 官方提示首次部署最长可能需要约 10 分钟。回到 **Settings** → **Pages**，看到 `Your site is live at ...` 后即可访问：

```text
https://27oexpert.github.io/
```

### 以后怎样更新

- **修改文字**：仓库中打开 `index.html` → 点击右上角铅笔 → 修改 → **Commit changes**。
- **替换头像**：点击 **Add file** → **Upload files**，上传同名文件覆盖旧文件，然后提交。
- 每次提交到 `main` 分支后，GitHub Pages 都会自动重新部署，通常几分钟内完成。

### GitHub 官方说明

- [创建 GitHub Pages 站点](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site)
- [配置发布来源](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)
- [上传文件到仓库](https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository)
- [排查 GitHub Pages 的 404](https://docs.github.com/en/pages/getting-started-with-github-pages/troubleshooting-404-errors-for-github-pages-sites)

## 常见问题

- **页面打开后没有样式**：确认 `styles.css` 和 `index.html` 在同一层，文件名大小写完全一致。
- **头像不显示**：确认照片位于 `assets` 文件夹，且 HTML 中的文件名与实际文件名完全一致。
- **GitHub 上已经更新，网站没变**：最长等待 10 分钟，然后按 `Ctrl + F5` 强制刷新。
- **网站显示 404**：确认 Pages 设置是 `main` + `/(root)`，并确认根目录直接存在全小写的 `index.html`；还可以在仓库的 **Actions** 页面查看部署日志。
- **链接打不开**：外部链接必须以 `https://` 开头；邮箱链接应以 `mailto:` 开头。

## License

你可以自由修改并用于自己的个人主页。页面内容、照片和论文资料请替换为你自己的信息。
