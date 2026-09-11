# academic-editor-zh

面向中文学术论文、技术论文与 LaTeX 稿件的深度编辑 Skill。它不以逐句改病句为主，而先检查章节结构、论证链、重复解释与证据边界，再统一中文学术语体。

核心目标：让论文清晰、准确、连贯、克制，同时减少英文句法直译、AI 套路、工程黑话和项目内部实现细节对正文的污染。

## 主要能力

- 章节级、段落级重构：先判断是否应合并、拆分、重排或移入附录，再做句子精修。
- 严格评审：检查“问题—缺口—方法—证据—结论”是否闭环，贡献是否可检验，对比是否公平。
- 中文学术语体：减少名词化、长前置定语、机械被动、无信息量连接词与翻译腔。
- 工程黑话清理：警惕“口径、门禁、闭环、链路、基座、赋能、沉淀、对齐、颗粒度、兜底”等抽象词，要求还原成具体条件、动作、对象与结果。
- 项目特化信息清理：变量名、字段名、枚举值、错误码、文件名、配置项、内部代号原则上不进入论文正文。
- LaTeX 完整性：保护 citation key、label key、公式、宏、路径等非自然语言对象；章间引用使用 `\label{}` + `\ref{}` / `\cref{}`。
- 独立 subagent 审稿：环境支持时，将不同问题类型交给互相隔离的审稿 agent；不向它们泄露主审结论和拟修改方案，降低锚定偏差。

## 安装

### skills.sh / Skills CLI

```bash
npx skills add modenicheng/academic-editor-zh
```

也可使用完整仓库地址：

```bash
npx skills add https://github.com/modenicheng/academic-editor-zh
```

### Git 克隆

```bash
git clone https://github.com/modenicheng/academic-editor-zh.git
```

随后将仓库目录放入所用 Agent 的 skills 目录即可。

## 使用示例

```text
深度审阅并修改这篇中文论文。先检查结构和论证，再润色；不要改变技术事实、数据和引用。
```

```text
只做严格审稿，不改文件。重点检查贡献证据、比较公平性、重复解释和工程文档语气。
```

```text
扫描全文中的“口径、门禁、闭环、链路、基座、能力、对齐”等抽象词。有明确学科含义的保留，其余改成具体条件和动作。
```

## 设计原则

本 Skill 吸收 [`humanizer-yu`](https://github.com/modenicheng/humanizer-yu) 中适合学术中文的直接动词、去名词化、去翻译腔和去 AI 套路原则，但不会机械执行“凡被动必改”“凡‘的’必删”或固定字数阈值。论文准确性与领域术语优先。

对于“统计口径”“闭环控制”“通信链路”“序列对齐”“理论框架”等已有稳定专业含义的词，不因命中警报词而删除。具体规则见 [`references/anti-calques-and-jargon.md`](references/anti-calques-and-jargon.md)。

## 仓库结构

```text
SKILL.md
README.md
LICENSE
agents/
  openai.yaml
references/
  anti-calques-and-jargon.md
  chinese-academic-style.md
  latex-integrity.md
  output-contract.md
  review-protocol.md
```

## License

MIT. See [LICENSE](LICENSE).
