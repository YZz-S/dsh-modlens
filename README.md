# dsh-modlens

[English](#english) · [中文](#中文)

> A **fork of [liustack/modlens](https://github.com/liustack/modlens)** — the vision plugin for DeepSeek Harness (dsh) — with multi-engine support and per-call engine selection.
>
> 这是 [liustack/modlens](https://github.com/liustack/modlens) 的**分支**——DeepSeek Harness（dsh）的视觉插件，支持多引擎与按调用选择引擎。

## English

[中文](#中文) · [← Back to DeepSeekHarnessPlugins](../README.md)

Plug-in vision for text-only LLMs. ModLens converts an image into structured JSON evidence (OCR, layout, semantics) so a text-only model can "see". This fork keeps all upstream behavior and adds:

- **`provider` argument on `modlens_read_image`** — pin the vision engine per call (`-p <provider>` passthrough).
- **"Ask which engine" behavior** — the tool description instructs the model to ask the user which engine to use whenever more than one is configured.
- **Doubao / Volcengine Ark recipe** — a tested setup for `doubao-seed-2.1-turbo` via the Ark `ark-coding-plan` endpoint (OpenAI-compatible), alongside Gemini, Anthropic, and Claude Code.

### Why a fork

Upstream ModLens is under active development. This fork carries the `provider` passthrough and the doubao/ark recipe until they land upstream. Prefer upstream for everything else: <https://github.com/liustack/modlens>.

### Install (DeepSeek Harness)

```bash
dsh plugin --profile web add github:YZz-S/dsh-modlens
```

Restart dsh, then look for the `(modlens vision)` model entries and the `modlens_read_image` tool.

### Configure engines

Config lives in `~/.modlens/config.json` (shared with upstream modlens). Run `modlens doctor` to see what is ready.

#### Gemini (free, fast)

```bash
modlens config set gemini-api.apiKey <key>   # https://aistudio.google.com
modlens config set provider gemini-api
```

#### Doubao / Volcengine Ark (ark-coding-plan)

```bash
modlens config set openai.baseUrl https://ark.cn-beijing.volces.com/api/coding/v3
modlens config set openai.apiKey <ARK_CODING_PLAN_API_KEY>
modlens config set openai.model doubao-seed-2.1-turbo
# optional: modlens config set provider openai
```

#### Others

Claude Code (`claude-cli`), Anthropic (`anthropic`), Antigravity (`antigravity-cli`). Full recipes: `skills/modlens/references/configure.md`.

### Per-call engine selection

When the model needs to read an image and more than one engine is configured, it asks you which to use, then calls `modlens_read_image` with the `provider` argument:

```
provider: "gemini-api" | "openai" (doubao/Ark) | "anthropic" | "claude-cli" | "antigravity-cli"
```

Omit `provider` to use the configured default and its failover chain.

### Verify

```bash
modlens doctor          # local diagnostics, spends no quota
modlens -i image.png    # end-to-end read (spends one read)
```

### License

MIT. Original work © 2026 Leon Liu (liustack); fork changes © 2026 `YZz-S`. See [LICENSE](LICENSE).

Upstream: <https://github.com/liustack/modlens>

---

## 中文

[English](#english) · [← 返回 DeepSeekHarnessPlugins](../README.md)

为纯文本 LLM 提供视觉能力。ModLens 把图片转换为结构化 JSON 证据（OCR、布局、语义），让纯文本模型也能"看见"。本分支保留全部上游行为，并新增：

- **`modlens_read_image` 增加 `provider` 参数**——每次调用可指定视觉引擎（`-p <provider>` 透传）。
- **"询问使用哪个引擎"行为**——工具描述指示模型在配置了多个引擎时，先询问用户要用哪个。
- **豆包 / 火山方舟 Ark 配方**——经由 Ark `ark-coding-plan` 端点（OpenAI 兼容）使用 `doubao-seed-2.1-turbo` 的实测配置，与 Gemini、Anthropic、Claude Code 并列。

### 为什么做分支

上游 ModLens 正在积极开发中。本分支承载 `provider` 透传与豆包/Ark 配方，直到它们合入上游。其他一切请优先使用上游：<https://github.com/liustack/modlens>。

### 安装（DeepSeek Harness）

```bash
dsh plugin --profile web add github:YZz-S/dsh-modlens
```

重启 dsh，然后查找 `(modlens vision)` 模型条目与 `modlens_read_image` 工具。

### 配置引擎

配置位于 `~/.modlens/config.json`（与上游 modlens 共用）。运行 `modlens doctor` 查看哪些已就绪。

#### Gemini（免费、快速）

```bash
modlens config set gemini-api.apiKey <key>   # https://aistudio.google.com
modlens config set provider gemini-api
```

#### 豆包 / 火山方舟 Ark（ark-coding-plan）

```bash
modlens config set openai.baseUrl https://ark.cn-beijing.volces.com/api/coding/v3
modlens config set openai.apiKey <ARK_CODING_PLAN_API_KEY>
modlens config set openai.model doubao-seed-2.1-turbo
# 可选：modlens config set provider openai
```

#### 其他

Claude Code（`claude-cli`）、Anthropic（`anthropic`）、Antigravity（`antigravity-cli`）。完整配方：`skills/modlens/references/configure.md`。

### 按调用选择引擎

当模型需要读取图片且配置了多个引擎时，它会先询问你使用哪个，然后带 `provider` 参数调用 `modlens_read_image`：

```
provider: "gemini-api" | "openai"（豆包/Ark）| "anthropic" | "claude-cli" | "antigravity-cli"
```

省略 `provider` 则使用配置的默认引擎及其故障转移链。

### 验证

```bash
modlens doctor          # 本地诊断，不消耗额度
modlens -i image.png    # 端到端读取（消耗一次读取）
```

### 许可

MIT。原始作品 © 2026 Leon Liu（liustack）；分支改动 © 2026 `YZz-S`。见 [LICENSE](LICENSE)。

上游：<https://github.com/liustack/modlens>

---

[English](#english) · [中文](#中文)
