# lazy-pixelle-video

[懒猫微服](https://lazycat.cloud) 上的 [Pixelle-Video](https://github.com/AIDC-AI/Pixelle-Video) 一键部署 ——
AI 全自动短视频引擎，输入主题自动生成完整视频。

## 安装

下载最新 lpk：[Releases](https://github.com/microlazy-apps/lazy-pixelle-video/releases/latest)

```sh
lpk-manager install ./cloud.lazycat.app.pixelle-video-*.lpk
```

或在懒猫应用商店搜索「Pixelle-Video」直接安装。

## 首次安装填写

安装时填以下参数（之后可在 Web UI 改）：

- **LLM API Key** —— 必填。任一 OpenAI SDK 兼容的 key（OpenAI / Qwen / DeepSeek / Ollama 等）
- **LLM Base URL** —— 默认 `https://api.openai.com/v1`，按 LLM 厂商替换
- **LLM Model** —— 默认 `gpt-4o`
- **RunningHub API Key** —— 可选，但**强烈推荐**。无 GPU 时用云端 ComfyUI 生成图/视频，免本地部署
- **ComfyUI URL** —— 可选。本地 ComfyUI 后端地址（如 `http://192.168.1.x:8188`），需要 GPU

> 没 GPU 也没 RunningHub key 不会启动失败，但视频生成会报"未配置 ComfyUI 后端"。
> 推荐先在 [RunningHub](https://www.runninghub.cn/) 申请 key，按量付费。

## 使用

装好后访问 `https://pixelle-video.{你的微服域名}` 打开 Streamlit Web UI。

输入一个**主题**（如「梵高的一生」、「猫为什么爱睡觉」），Pixelle-Video 自动完成：
- ✍️ 撰写视频文案
- 🎨 生成 AI 配图/视频
- 🗣️ 合成语音解说（Edge-TTS / Index-TTS）
- 🎵 添加背景音乐
- 🎬 一键合成视频

生成的视频保存在 `/lzcapp/var/output/`，可在 Web UI 里下载或分享。

## 开发

仓库结构：Pixelle-Video 上游以 git subtree 形式存放在 `vendor/pixelle-video/`，
所有改动以 patch 形式存在 `patches/`。

详细开发说明（patches 工作流、发布流程、架构选择）见 [CLAUDE.md](CLAUDE.md)。

## License

Apache-2.0。Upstream Pixelle-Video (`vendor/pixelle-video/`) 也是 Apache-2.0 ——
见 `vendor/pixelle-video/LICENSE`。
