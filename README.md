# Hy Skill：文章转视频

把文稿、Markdown 文章或知识主题转换成可编辑的 HyperFrames 视频项目，并渲染为 MP4。

## 通过 AI Agent 制作视频

安装 Skill：

```bash
npx skills add juxiu/hy-skill
```

然后在支持 Skills 的 Agent 中提供文章或文件路径，例如：

> 把这篇文章制作成 60 秒左右的中文讲解视频。先提炼主线，再设计分镜，使用简洁的动态图形和字幕，最后用 HyperFrames 渲染 MP4。

默认使用 16:9 画幅、中文、简洁排版。Agent 会创建独立项目，保留原文、分镜和 HTML 源文件，并运行检查和渲染。

## 快速生成文字版草稿

需要 Node.js 22+ 和 FFmpeg。基础脚本会按 Markdown 标题和段落生成一组文字场景，再交给 HyperFrames 预览和渲染：

```bash
node scripts/create-video.mjs ./article.md --out videos/my-article
cd videos/my-article
npx hyperframes lint
npx hyperframes preview
mkdir -p renders
npx hyperframes render --output renders/video.mp4
```

也可以指定标题：

```bash
node scripts/create-video.mjs ./article.md --title "文章标题" --out videos/my-article
```

脚本适合快速得到可运行的初稿；更有表现力的插图、图表、叙事节奏、配音和字幕，由 Agent 按需在 HyperFrames 项目中继续完成。

## 依赖

- Node.js 22+
- FFmpeg（本地渲染 MP4 所需）
- HyperFrames CLI（脚本会在新项目中通过 `npx` 初始化）

官方文档：[HyperFrames](https://github.com/heygen-com/hyperframes) · [CLI 指南](https://github.com/heygen-com/hyperframes/blob/main/docs/developers/cli.mdx)
