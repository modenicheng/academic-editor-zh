# LaTeX 源码完整性

## 不可误改对象

润色自然语言时跳过：

- 数学环境及公式内容
- `\cite{...}` 内 citation key
- `\label{...}`、`\ref{...}`、`\cref{...}` 内 key
- 自定义宏名和命令参数中非自然语言字段
- `\includegraphics` 路径
- `\input` / `\include` 路径
- 代码环境、伪代码标识符
- BibTeX key

## 交叉引用

不要写死“第 3 章”“第 3.2 节”“上一章”。

推荐：

```tex
\section{方法}\label{sec:method}

如第~\ref{sec:method}~节所述，……
```

若项目使用 `cleveref`，优先遵循现有 `\cref{}` 风格。

## 修改策略

- 尽量复用已有 label，避免无意义改 key。
- 新增 label 时采用项目既有命名风格。
- 重排章节后检查所有交叉引用。
- 删除段落前确认其中没有唯一 label、citation 或后文依赖。
- 表格重构时保持数值、单位、脚注、引用对应关系。
