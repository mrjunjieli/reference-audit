# Reference Audit

用于核查学术参考文献真实性与元数据准确性的 Codex skill。支持 PDF、DOCX、BibTeX 和粘贴的参考文献文本。

## 功能

- 逐条核查作者、题名、年份、刊名、卷期、页码、文章号、DOI 和 arXiv 标识符。
- 优先采用出版社、会议官网及原文证据，并为判定和修改建议提供可追溯链接。
- 区分疑似虚构、实质性错误、定位信息缺失、格式问题和基本正确。
- 检索预印本的正式发表版本，避免把独立的后续研究或扩展版直接当作替代品。
- 保留用户选择的 BibTeX 类型和引用键，支持统一使用 `@misc`。
- 避免将文章号存储在 `pages` 字段或由模板渲染为 `pp.` 误判为事实错误。

## 安装

将本仓库克隆到 Codex 的个人技能目录：

```sh
git clone https://github.com/mrjunjieli/reference-audit.git "${CODEX_HOME:-$HOME/.codex}/skills/reference-audit"
```

如果目标目录已存在，请先保留原有自定义内容，再合并或更新。重新打开 Codex 会话后使用。

## 使用示例

```text
使用 $reference-audit 核查这份论文的全部参考文献。
逐条提供官方来源，区分实质错误与格式建议；
检查预印本是否正式发表，并给出可追溯的修改建议。
```

```text
使用 $reference-audit 复核这三条被标记为错误的文献，检查是否误报。
```

## 文件结构

```text
SKILL.md                       核查流程及判定规则
agents/openai.yaml             技能显示信息与默认提示
references/source-strategy.md  证据来源优先级与检索策略
references/report-format.md    报告格式、BibTeX 和验证规则
```

## 运行条件与范围

需要可用的网页检索或浏览能力。处理文档时还需要相应的 PDF/DOCX 读取工具；验证引用排版时需要目标 BibTeX/BibLaTeX 工具链。此仓库提供工作流指令，不附带这些工具。

默认核查书目记录，不自动判断论文正文中的每项论断是否得到所引文献支持。网页不可访问或记录冲突时，应明确说明限制，不把无法确认等同于文献不存在。
