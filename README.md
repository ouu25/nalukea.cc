# Nalukea

https://nalukea.cc

## 站点结构

```
nalukea.cc/             → 首页（项目导航）
nalukea.cc/pathways/    → 海外升学路线规划
```

## 部署方式

本站通过 **GitHub Pages** 托管，**Cloudflare** 管理 DNS 和 CDN。

### 首次部署步骤

#### 1. GitHub 仓库设置

```bash
# 在本地创建仓库
cd nalukea-deploy
git init
git add .
git commit -m "Initial commit"

# 创建 GitHub 仓库（建议命名为 nalukea.cc）
# 然后推送
git remote add origin git@github.com:YOUR_USERNAME/nalukea.cc.git
git branch -M main
git push -u origin main
```

#### 2. 开启 GitHub Pages

1. 进入仓库 **Settings → Pages**
2. Source 选择 **Deploy from a branch**
3. Branch 选择 **main**，目录选 **/ (root)**
4. 保存

此时网站会部署到 `YOUR_USERNAME.github.io/nalukea.cc`

#### 3. Cloudflare DNS 配置

在 Cloudflare 的 nalukea.cc 域名管理中添加以下 DNS 记录：

| 类型 | 名称 | 内容 | 代理状态 |
|------|------|------|----------|
| CNAME | @ | YOUR_USERNAME.github.io | 已代理 (橙色云) |
| CNAME | www | nalukea.cc | 已代理 (橙色云) |

#### 4. GitHub Pages 自定义域名

1. 回到仓库 **Settings → Pages**
2. 在 **Custom domain** 输入 `nalukea.cc`
3. 勾选 **Enforce HTTPS**
4. GitHub 会自动创建 CNAME 文件（或手动创建）

#### 5. Cloudflare SSL 设置

在 Cloudflare 的 **SSL/TLS** 设置中：
- 加密模式选择 **Full (strict)**
- 确保 **Always Use HTTPS** 已开启

### 后续更新

```bash
# 修改文件后
git add .
git commit -m "Update: xxx"
git push

# GitHub Pages 会自动部署，通常 1-2 分钟生效
```

## 添加新项目

在根目录 `index.html` 的 `.projects` div 中添加新卡片，然后创建对应子目录即可：

```html
<a href="/new-project/" class="project-card">
  <div class="pc-label">Category</div>
  <div class="pc-title">新项目名称</div>
  <div class="pc-desc">项目描述</div>
</a>
```

## 字体说明

- **Fraunces / IBM Plex Mono**：通过 `fonts.loli.net`（Google Fonts 国内镜像）加载，SIL Open Font License，免费商用
- **中文字体**：回退到系统字体（PingFang SC / Microsoft YaHei），零延迟加载
- 如果镜像也不稳定，可考虑自托管字体文件到 `/fonts/` 目录

## 许可

内容：CC BY-NC-SA 4.0
