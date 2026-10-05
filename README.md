# Hugo PaperMod

**A fast, clean, and responsive theme for [Hugo](https://gohugo.io/).**

[![hugo-papermod](https://img.shields.io/badge/Hugo--Themes-@PaperMod-blue)](https://themes.gohugo.io/themes/hugo-papermod/)
[![Minimum Hugo Version](https://img.shields.io/static/v1?label=Hugo&message=v0.146.0%2B&color=blue&logo=hugo)](https://github.com/gohugoio/hugo/releases/tag/v0.146.0)
[![Discord](https://img.shields.io/discord/971046860317921340?label=Discord&logo=discord)](https://discord.gg/ahpmTvhVmp)

> Based on [hugo-paper](https://github.com/nanxiaobei/hugo-paper/tree/4330c8b12aa48bfdecbcad6ad66145f679a430b3), with additional features and customization options.

<table>
	<tbody>
		<tr>
			<td>Live Demo</td>
			<td><a href="https://adityatelange.github.io/hugo-PaperMod/">adityatelange.github.io/hugo-PaperMod</a></td>
		</tr>
		<tr>
			<td>Documentation 📚</td>
			<td><a href="https://github.com/adityatelange/hugo-PaperMod/wiki">Github Wiki</a></td>
		</tr>
		<tr>
			<td>Example Site Source</td>
			<td><a href="https://github.com/adityatelange/hugo-PaperMod/tree/exampleSite">exampleSite branch</a></td>
		</tr>
		<tr>
			<td><a href="https://www.star-history.com/adityatelange/hugo-papermod"><img src="https://api.star-history.com/badge?repo=adityatelange/hugo-PaperMod&amp;theme=dark" alt="Star History Rank" /></a></td>
			<td><a href="https://ko-fi.com/H2H229ZWH"><img src="https://ko-fi.com/img/githubbutton_sm.svg" alt="ko-fi" /></a></td>
		</tr>
	</tbody>
</table>


<p align="center">
  <img src="https://user-images.githubusercontent.com/21258296/114303440-bfc0ae80-9aeb-11eb-8cfa-48a4bb385a6d.png" alt="Mockup image" title="Mockup"/>
</p>

---

## Features 💥

`☄️ Fast | ☁️ Fluent | 🌙 Smooth | 📱 Responsive`

- **Asset pipeline** -- Hugo's built-in asset generator with fingerprinting, bundling, and minification.
- **Three layout modes** -- [Regular](https://github.com/adityatelange/hugo-PaperMod/wiki/Features#regular-mode-default-mode), [Home-Info](https://github.com/adityatelange/hugo-PaperMod/wiki/Features#home-info-mode), and [Profile](https://github.com/adityatelange/hugo-PaperMod/wiki/Features#profile-mode).
- **Light and dark themes** -- Automatic switching based on browser preference, plus a manual toggle.
- **Multilingual support** -- Includes a built-in language selector.
- **Search** -- Client-side search powered by Fuse.js.
- **SEO optimized** -- Open Graph, Twitter Cards, and Schema.org structured data out of the box.
- **Cover images** -- Per-post cover images with responsive image support.
- **Table of contents** -- Auto-generated from heading structure.
- **Multiple authors** -- Native support for multi-author sites.
- **Social icons and share buttons** -- Configurable social links and per-post sharing.
- **Breadcrumb navigation**
- **Post archives and taxonomies**
- **Code block copy buttons** -- One-click copying with Chroma syntax highlighting.
- **Related post suggestions**
- **Zero JS build dependencies** -- No webpack, Node.js, or other tooling required.

| Topic                                                                                             | Description                                     |
| ------------------------------------------------------------------------------------------------- | ----------------------------------------------- |
| **[Installation guide](https://github.com/adityatelange/hugo-PaperMod/wiki/Installation)**        | Detailed installation and update instructions   |
| **[Features wiki page](https://github.com/adityatelange/hugo-PaperMod/wiki/Features)**            | In-depth explanations of all features           |
| **[FAQ wiki](https://github.com/adityatelange/hugo-PaperMod/wiki/FAQs)**                          | Common questions and configuration walkthroughs |
| **[Icons wiki](https://github.com/adityatelange/hugo-PaperMod/wiki/Icons)**                       | Documentation for social icons and share icons  |
| **[Variables wiki](https://github.com/adityatelange/hugo-PaperMod/wiki/Variables)**               | List of all available template variables        |
| **[Overiding templates](https://github.com/adityatelange/hugo-PaperMod/wiki/Template_Overrides)** | Guide to customizing templates without forking  |
| **[Releases](https://github.com/adityatelange/hugo-PaperMod/releases)**                           | Detailed history of releases                    |

---

## Performance ☄️

PaperMod consistently scores near-perfect results on [Pagespeed Insights](https://pagespeed.web.dev/report?url=https://adityatelange.github.io/hugo-PaperMod/).

<img width="481" height="116" alt="image" src="https://github.com/user-attachments/assets/497d831b-d143-4a46-bc11-b1d7f8ef4a83" />

---

## Support 🫶

- Star this repository to show your support.
- Share PaperMod with others who might find it useful.
- Sponsor the project on [GitHub Sponsors](https://github.com/sponsors/adityatelange) or [Ko-Fi](https://ko-fi.com/adityatelange).

---

## 本 fork 的站点定制

这个 fork 是 [StreamAzure](https://github.com/StreamAzure) 给站点
**https://streamazure.github.io/** 用的，在上游基础上加了三处东西。
上游更新时只要不冲突就不会被覆盖（两个是新增文件，一个是覆盖上游的空壳）。

| 路径 | 作用 |
| --- | --- |
| `assets/css/extended/toc-sidebar.css` | 宽屏（≥1100px）下把文章目录变成**右侧固定跟随**栏；窄屏不动，保持主题原本的折叠样式 |
| `layouts/_partials/extend_head.html` | 覆盖上游的空壳，按需加载**自托管 KaTeX** 渲染数学公式；页面没有 `$` 时一个字节都不下载 |
| `static/katex/` | KaTeX 本体（JS + CSS + 20 个字体，约 550 KB），发布到站点根 `/katex/`，不依赖外部 CDN |

### 改这几处前必读

1. **`extend_head.html` 在 `<head>` 里执行**，那时正文还没解析完，直接
   `document.querySelector('.post-content')` 一定拿到 `null`。必须包一层 `DOMContentLoaded`。
2. **目录栏的 `grid-row` 必须写 `2`**，不能写 `1 / -1`：写 `1 / -1` 会让目录落进标题那一行，
   跑到标题上方去。
3. **数学分隔符要和站点配置一致**：`hugo.yaml` 里
   `markup.goldmark.extensions.passthrough.delimiters` 必须和这里的
   `renderMathInElement` 的 `delimiters` 对齐，否则公式会渲染两遍或渲染不到。
4. **`static/katex/` 是手工放的**（来自 npm 包 `katex@0.16.11` 的 `dist/`）。
   要升级版本就整个目录替换，注意 `fonts/` 要一起换。

> ⚠️ 站点仓库（`StreamAzure.github.io`）在构建时会用 `.github/build/` 下的同名文件
> **覆盖**这里的 `toc-sidebar.css` 和 `extend_head.html`。
> 也就是说：**这两个文件的"生效版本"以站点仓库的 `.github/build/` 为准**，
> 只改这个 fork 不改站点仓库，线上不会有变化。

---

## Special Thanks 🌟

- [Highlight.js](https://github.com/highlightjs/highlight.js)
- [Fuse.js](https://github.com/krisk/fuse)
- [Feather Icons](https://github.com/feathericons/feather)
- [Simple Icons](https://github.com/simple-icons/simple-icons)
- All contributors and supporters
