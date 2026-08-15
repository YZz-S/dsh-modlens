# dsh-modlens

> [liustack/modlens](https://github.com/liustack/modlens) 的**增强分支（fork）**——DeepSeek Harness（dsh）视觉插件，新增多引擎支持与「按次选择引擎」。

为纯文本大模型提供视觉能力：ModLens 把图片转成结构化 JSON 证据（OCR、版面、语义），让纯文本模型也能「看图」。本分支保留上游全部行为，并新增：

- **`modlens_read_image` 新增 `provider` 参数**——单次调用指定视觉引擎（透传 `-p <provider>`）。
- **「主动询问用哪个引擎」**——工具描述里指示模型：当配置了多个引擎且用户未指定时，先问用户用哪个。
- **豆包 / 火山方舟 Ark 接入配方**——实测可用的 `doubao-seed-2.1-turbo`（走 Ark `ark-coding-plan` OpenAI 兼容端点），与 Gemini、Anthropic、Claude Code 并存。

## 为什么是 fork

上游 ModLens 在持续开发中。本分支承载 `provider` 透传与豆包/Ark 配方，直到它们合入上游。其余一切优先用上游：<https://github.com/liustack/modlens>。

## 安装（DeepSeek Harness）

```bash
npx -y @deepseek-ai/dsh plugin --profile web add dsh-modlens@3.16.6
```

重启 dsh，在模型选择器里找 `(modlens vision)` 条目和 `modlens_read_image` 工具。

> 发布前请把 `dsh-modlens` 和 `<your-org>` 替换成你自己的包名与 GitHub 组织。

## 配置引擎

配置在 `~/.modlens/config.json`（与上游 modlens 共享）。用 `modlens doctor` 查看哪些引擎就绪。

### Gemini（免费、快）

```bash
modlens config set gemini-api.apiKey <key>   # https://aistudio.google.com
modlens config set provider gemini-api
```

### 豆包 / 火山方舟 Ark（ark-coding-plan）

```bash
modlens config set openai.baseUrl https://ark.cn-beijing.volces.com/api/coding/v3
modlens config set openai.apiKey <ARK_CODING_PLAN_API_KEY>
modlens config set openai.model doubao-seed-2.1-turbo
# 可选：modlens config set provider openai
```

### 其他

Claude Code（`claude-cli`）、Anthropic（`anthropic`）、Antigravity（`antigravity-cli`）。完整配方见 `skills/modlens/references/configure.md`。

## 按次选择引擎

模型需要读图且配置了多个引擎时，会先问你用哪个，再带着 `provider` 参数调用 `modlens_read_image`：

```
provider: "gemini-api" | "openai"（豆包/Ark）| "anthropic" | "claude-cli" | "antigravity-cli"
```

省略 `provider` 则使用配置的默认引擎及其 failover 链。

## 验证

```bash
modlens doctor          # 本地诊断，不消耗配额
modlens -i image.png    # 端到端读图（消耗一次读图）
```

## 许可证

MIT。原作品 © 2026 Leon Liu (liustack)；fork 改动 © 2026 `<Your Name>`。见 [LICENSE](LICENSE)。

上游：<https://github.com/liustack/modlens>
