# Bloom 静态资源

Bloom(专注花园)App 的官方静态站点,包含产品落地页、隐私政策 / 服务条款,以及 Android 安装包分发。通过 GitHub Pages 托管,无需构建步骤。

- 线上地址:https://swiftmass.github.io/bloom-static/
- 仓库:`git@github.com:SwiftMass/bloom-static.git`

## 目录结构

```
bloom-static/
├── index.html              # 落地页(单文件,内联 React 18 + Babel Standalone + CSS)
├── privacy/                # 隐私政策与服务条款(中/英各一份)
│   ├── privacy-policy-zh.html
│   ├── privacy-policy-en.html
│   ├── terms-of-service-zh.html
│   └── terms-of-service-en.html
├── apk/
│   └── bloom-release.apk   # Android 发布包(约 81 MB)
├── assets/
│   └── screens/            # 应用截图(focus/garden/mindful/sleep/together/insights,中英各一套)
└── README.md
```

## 落地页说明

`index.html` 是一个自包含的单文件页面,不依赖打包工具:

- 通过 CDN(unpkg)引入 `react` / `react-dom` 生产版与 `@babel/standalone`,在浏览器端即时编译 JSX。
- 样式内联在 `<style>` 中,使用 CSS 变量定义配色与字体(Fraunces / Newsreader / Inter,来自 Google Fonts)。
- 页面锚点分区:`intention`、`mechanic`、`flowers`、`garden`、`together`、`milestones`、`tour`、`support`、`get`(下载)。

## 本地预览

纯静态页面,任意静态服务器均可(需用 HTTP 而非 `file://`,否则 CDN 脚本与字体可能被拦截):

```bash
cd bloom-static
python3 -m http.server 8080
# 打开 http://localhost:8080/
```

## 部署

推送到 `main` 分支后由 GitHub Pages 自动发布,无额外构建流程。

- 更新落地页 / 隐私文档:直接修改对应 HTML 并提交。
- 更新 Android 安装包:替换 `apk/bloom-release.apk` 后提交(注意 GitHub 单文件 100 MB 上限)。

## 相关

Bloom App 主工程(Expo / React Native + Supabase)在同一 monorepo 的其他目录中,本仓库仅承载对外静态资源。
