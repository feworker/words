# 词间 · 英语单词学习

访问：https://feworker.github.io/words/

使用 shadcn/ui、React、TypeScript、Tailwind、CVA 与 lucide。支持词库导入、词义讲解、双语例句、收藏、学习记录、笔记与微软语音播放。

当前仓库根目录是 GitHub Pages 构建产物；完整可运行源码与 Python 查词/TTS 后端在 [source.zip](./source.zip) 中。解压后 `npm install && npm start` 本地运行；`npm run build:pages` 重建 /words/ 部署产物。发布包不含本机用户学习数据或凭据。

Pages 设置：Deploy from a branch → main → /(root)。

## 语音与查词

预置 12 词、18 条例句使用真实 Microsoft Jenny MP3，可直接播放。新词查词与非预置音频需要联网服务。GitHub Pages 不运行 Python 后端；请在页面播放设置中填写 HTTPS 服务地址，或配置 words-config.js 的 WORDS_SERVICE_ENDPOINT。后端需支持 POST /api/lookup、POST /api/tts 并允许 https://feworker.github.io 跨域。服务端示例与详细启动方法见源码 README。

当前没有配置公网后端，因此新词联网补全和动态微软发音待配置；默认不使用系统语音代替。
