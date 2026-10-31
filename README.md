# 拜肥鱼教 · 落地页

单页静态站点，无构建、无依赖、无外部字体，只有 `index.html` + `assets/`。

## 本地预览

直接双击 `index.html`，或者：

```powershell
python -m http.server 8000 --directory site
# 打开 http://127.0.0.1:8000
```

## 部署到 GitHub Pages

```powershell
cd site
git init
git add .
git commit -m "拜肥鱼教"
git branch -M main
git remote add origin https://github.com/<你的账号>/<仓库名>.git
git push -u origin main
```

然后在仓库 **Settings → Pages**：Source 选 `Deploy from a branch`，Branch 选 `main` / 目录 `/ (root)`，保存。
一两分钟后访问 `https://<账号>.github.io/<仓库名>/`。

> 本目录里的 `index.html` 必须放在仓库根目录（或 Pages 指定的目录）下，`assets/` 要和它同级。
> `.nojekyll` 已放好，避免 Pages 用 Jekyll 处理静态文件。

## 结构

```
site/
├── index.html          页面本体（内联样式与脚本）
├── .nojekyll
└── assets/
    ├── hero.png        半身圣像（首屏）
    ├── front.png       正面设定
    ├── side.png        侧面设定
    ├── back.png        背面设定
    └── sheet.png       四视图整张
```

## 改什么

- **祷词**：`index.html` 里 `const prayers = [...]`，随便加，首屏默认按「当天日期」轮换，点按钮随机。
- **教义**：`#doctrine` 区块里的 6 个 `<article class="card">`。
- **入教凭证**：`prefix` / `suffix` 两个数组决定教名，`certText` 决定复制出去的文本。
- **配色**：`:root` 里的 `--blue` / `--sky` / `--gold`。
- **圣像**：换 `assets/` 下的同名文件即可，尺寸不必一致（用的是 `object-fit: contain`）。

## 素材来源

角色四视图由站主提供；人格设定的上游是
[shirachino/astrbot-persona-prompts](https://github.com/shirachino/astrbot-persona-prompts)。
