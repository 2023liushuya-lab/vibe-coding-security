# Vibe Coding Security Checklist

> AI lowers the bar to *building* something, but not to *building it securely*.

A Claude Code **skill** for reviewing AI-generated code before launch — covering the 5 critical security pitfalls that vibe-coded apps consistently miss.

[中文版 ↓](#vibe-coding-安全审查清单)

---

## Why This Exists

Vibe coding (Cursor, Windsurf, Copilot, Claude) lets you ship fast — but AI optimizes for *working* code, not *secure* code. Common findings across studies:

- **45%** of AI-generated code contains an OWASP Top 10 vulnerability
- **61%** of AI code works correctly, but only **10.5%** is secure

This skill bridges that gap: a structured security review you run before going live.

## The 5 Dimensions

| # | Dimension | Core Risk |
|---|-----------|-----------|
| 1 | **CAPTCHA & Rate Limiting** | No image captcha, no IP rate limiting, no daily per-number caps → SMS bombing, account brute-force |
| 2 | **UGC Content** | No review of avatars/nicknames/comments → ads, scams, liability for violating content |
| 3 | **File Upload** | No size/format validation, no hotlink protection, predictable paths → abused as free image host |
| 4 | **AI Chat** | Prompt injection to leak system prompts, induce policy-violating output, expose other users' data |
| 5 | **Demo-as-Product** | No auth, SQL injection, hardcoded keys, misconfigured CORS, no CSRF, missing security headers |

Each dimension in the skill includes:
- Detailed checklist (YAML-style, check-off-able)
- Attack scenario walkthrough
- Code examples (Python/JS pseudocode)
- Fix recommendations

## Installation

```bash
git clone https://github.com/2023liushuya-lab/vibe-coding-security.git ~/.claude/skills/vibe-coding-security
```

Then invoke with:
```
/vibe-coding-security review this project before launch
```

## Usage

The skill walks through your project's routes, API endpoints, and config files against the 5 dimensions, then outputs a structured security report with risk levels and fix steps.

## Principles

> **AI lowers the barrier to creation, but not the barrier to responsibility.**

- Features can iterate; security baselines cannot be retrofitted
- Attackers don't follow your test paths
- User data privacy must be designed in, not bolted on

## Related

- [OWASP Top 10 for LLM Applications](https://genai.owasp.org/)
- [taskade/awesome-vibe-coding](https://github.com/taskade/awesome-vibe-coding)
- [subinium/awesome-claude-code](https://github.com/subinium/awesome-claude-code)

## License

MIT

---

# Vibe Coding 安全审查清单

AI 降低了"做出来"的门槛，但没有降低"做得安全"的门槛。

本仓库是 Claude Code 的 **Vibe Coding 安全审查 skill**，用于审查 AI 生成代码在上线前的 5 个关键安全坑位。

## 适用场景

用 Cursor / Windsurf / Copilot / Claude 等 AI 工具快速开发的 App，准备上线前做一轮安全检查。

## 5 个安全维度

| # | 维度 | 核心风险 |
|---|------|---------|
| 1 | 验证码与限流 | 无图形验证码、无 IP 限频、无单号日上限 → 短信轰炸 |
| 2 | UGC 内容 | 头像/昵称/评论无审核 → 广告、诈骗、违规内容连带责任 |
| 3 | 文件上传 | 无大小/格式校验、无防盗链、路径可预测 → 被当免费图床 |
| 4 | AI 聊天 | 提示词注入套出 System Prompt、诱导输出违规内容 |
| 5 | Demo 即产品 | 无鉴权、SQL 注入、硬编码密钥、CORS 配置错误等 |

## 安装

```bash
git clone https://github.com/2023liushuya-lab/vibe-coding-security.git ~/.claude/skills/vibe-coding-security
```

然后用 `/vibe-coding-security` 调用。

## 使用方式

```
/vibe-coding-security 审查一下我这个项目的安全问题
```

输出一份包含详细检查清单、风险等级和修复建议的安全审查报告。

## 原则

> **AI 降低了创造的门槛，但没有降低责任的门槛。**

- 功能可以迭代，安全底线不能后补
- 攻击者不会按你的测试路径来
- 用户数据隐私要纳入设计

## License

MIT
