# company-research-skill

用「三个问题 × 五个动作」框架快速拆解一家陌生公司（方法来源：[【@迪迪碎碎念_AI】](https://www.bilibili.com/video/BV1mqLJ6CERW/)）。核心不是堆数据，而是**用对的问题把用户推到独立判断的阶段**。

## 框架总览

| 阶段 | 核心问题 | 动作 |
|------|---------|------|
| 1 | 这家公司是谁？ | ① 类比 → ② 画业务版图 |
| 2 | 凭什么活着？ | ③ 找命脉 |
| 3 | 会不会死？ | ④ 反方辩手 → ⑤ 形成判断 |

三个问题的顺序不能换。先搞清楚公司是谁，再谈护城河，最后看风险。

## 核心设计原则

- **不是研报工具**：产出是"判断"，不是 50 页报告
- **允许不完美**：信息永远不完备，标注"暂缺"继续
- **判断优于数据**：宁可有偏的判断，不要完美的数据搬运
- **证据等级分离**：五级证据体系（A 级-公司披露 → E 级-AI 推理），语气强度绑定证据等级

## 数据纪律

参见 SKILL.md 中的：
- A 级证据优先获取路径（§1.3）— 明确搜索只是入口，原始披露才决定证据等级
- 五级证据体系（§1.4）— 含语气强度绑定规则
- 反幻觉约束（§1.5）
- 财务细节注释（环比趋势 + 异常信号解释）
- 技术演进路径与公司卡位
- 输出前检查清单

## 版本

当前版本：**v1.0**

### v1.0 能力
- 用「三个问题 × 五个动作」拆解公司
- 引入五级证据体系，语气强度绑定证据等级
- 加入反幻觉约束、数据冲突显性化和输出前检查清单
- 支持技术演进路径、风险排序和独立判断模板

## 示例输出

完整框架输出示例（含五级证据标注、语气绑定、thesis break conditions、可信度摘要）：

- [中际旭创（300308）公司拆解](examples/中际旭创%20-%20公司拆解%2020260527.md) — 通信/光模块行业（光模块全球龙头）

## 安装

`SKILL.md` 可被多种兼容 Agent 使用；本仓库优先维护并推荐 **Codex** 使用方式。

### 一行命令

```bash
# Claude Code
mkdir -p ~/.claude/skills/leon-company-research && curl -fsSL https://raw.githubusercontent.com/pamler1004/company-research-skill/main/SKILL.md -o ~/.claude/skills/leon-company-research/SKILL.md

# Codex CLI
mkdir -p ~/.codex/skills/leon-company-research && curl -fsSL https://raw.githubusercontent.com/pamler1004/company-research-skill/main/SKILL.md -o ~/.codex/skills/leon-company-research/SKILL.md
```

### 其它兼容 agent

把同一份 `SKILL.md` 放进对应目录即可，无需改动文件内容：

| Agent | Skills 目录 | 调用方式 |
|-------|------------|---------|
| Claude Code | `~/.claude/skills/leon-company-research/` | 描述命中时自动触发 |
| Codex | `~/.codex/skills/leon-company-research/` | `$leon-company-research` 或描述命中 |
| GitHub Copilot | `.github/skills/leon-company-research/`（项目级） | Copilot 编码 agent |

> 手动安装：克隆仓库后把 `SKILL.md` 拷到上述任一目录；或用其它 agent 的 plugin/skill 市场按本仓库地址安装。

## 数据源与责任边界

- Longbridge MCP 与相关 `longbridge-*` Skill 是可选增强，不随本仓库提供。
- 没有专用金融数据工具时，可使用公司官网 IR、监管披露和公开网络资料；必须保留来源和数据日期。
- 输出用于研究和形成判断，不构成投资建议。财务数据、估值与一致预期在对外使用前应再次核验。

## License

MIT
