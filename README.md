# dsh-modlens

> A **fork of [liustack/modlens](https://github.com/liustack/modlens)** — the vision plugin for DeepSeek Harness (dsh) — with multi-engine support and per-call engine selection.

Plug-in vision for text-only LLMs. ModLens converts an image into structured JSON evidence (OCR, layout, semantics) so a text-only model can "see". This fork keeps all upstream behavior and adds:

- **`provider` argument on `modlens_read_image`** — pin the vision engine per call (`-p <provider>` passthrough).
- **"Ask which engine" behavior** — the tool description instructs the model to ask the user which engine to use whenever more than one is configured.
- **Doubao / Volcengine Ark recipe** — a tested setup for `doubao-seed-2.1-turbo` via the Ark `ark-coding-plan` endpoint (OpenAI-compatible), alongside Gemini, Anthropic, and Claude Code.

## Why a fork

Upstream ModLens is under active development. This fork carries the `provider` passthrough and the doubao/ark recipe until they land upstream. Prefer upstream for everything else: <https://github.com/liustack/modlens>.

## Install (DeepSeek Harness)

```bash
dsh plugin --profile web add github:YZz-S/dsh-modlens
```

Restart dsh, then look for the `(modlens vision)` model entries and the `modlens_read_image` tool.

## Configure engines

Config lives in `~/.modlens/config.json` (shared with upstream modlens). Run `modlens doctor` to see what is ready.

### Gemini (free, fast)

```bash
modlens config set gemini-api.apiKey <key>   # https://aistudio.google.com
modlens config set provider gemini-api
```

### Doubao / Volcengine Ark (ark-coding-plan)

```bash
modlens config set openai.baseUrl https://ark.cn-beijing.volces.com/api/coding/v3
modlens config set openai.apiKey <ARK_CODING_PLAN_API_KEY>
modlens config set openai.model doubao-seed-2.1-turbo
# optional: modlens config set provider openai
```

### Others

Claude Code (`claude-cli`), Anthropic (`anthropic`), Antigravity (`antigravity-cli`). Full recipes: `skills/modlens/references/configure.md`.

## Per-call engine selection

When the model needs to read an image and more than one engine is configured, it asks you which to use, then calls `modlens_read_image` with the `provider` argument:

```
provider: "gemini-api" | "openai" (doubao/Ark) | "anthropic" | "claude-cli" | "antigravity-cli"
```

Omit `provider` to use the configured default and its failover chain.

## Verify

```bash
modlens doctor          # local diagnostics, spends no quota
modlens -i image.png    # end-to-end read (spends one read)
```

## License

MIT. Original work © 2026 Leon Liu (liustack); fork changes © 2026 `YZz-S`. See [LICENSE](LICENSE).

Upstream: <https://github.com/liustack/modlens>
