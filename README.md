# 词间 · 英语单词学习

访问：https://feworker.github.io/words/

使用 React、TypeScript、shadcn/ui、Tailwind、CVA 与 lucide。支持词库导入、讲解、双语例句、收藏、学习记录、笔记和微软语音播放。

## GitHub Actions 音频构建与发布

`.github/workflows/pages.yml` 从 `source.zip` 解压完整源码，安装锁定依赖，读取与页面共用的 `src/lib/words.ts`，为每个单词和英文例句生成 Jenny、Aria、Ryan 三种 Microsoft 神经语音 MP3。

所有音频经 ffprobe 校验后，Actions 构建页面并部署 GitHub Pages。合成需要在构建阶段连接微软，线上播放使用静态 MP3，无需 TTS 服务。缓存复用未变更音频，失败重试；任一音频失败则停止发布，保留上次线上版本。

Pages Source：GitHub Actions。源码或工作流推送到 main 会触发构建，也支持 Actions 中手动 Run workflow。仓库根目录的旧静态构建文件不再作为发布源。

更新词库：解压 source.zip，修改 src/lib/words.ts 的 samples，重新打包 source.zip 并提交。完整本地启动说明见源码 README。

浏览器中新导入/搜索的词汇仅保存于该浏览器；需导出并加入仓库词库、重新构建才能生成静态音频。联网查词仍需要独立服务。
