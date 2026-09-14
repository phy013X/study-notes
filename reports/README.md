# reports · 正式报告（LaTeX）

需要打印上交、对格式有硬性要求的课程报告、实验报告、课程论文放在这里。
日常学习笔记仍然用 Markdown，写在 `daily/`、`courses/` 等目录。

## 模板

通用中文技术文档模板在 [`../templates/latex-report-template/`](../templates/latex-report-template/README.md)：

- 标准 `article` + `ctex`，**XeLaTeX** 编译；
- 内置公式、定理、代码高亮、三线表、GB/T 7714 国标参考文献示例；
- 编译：`latexmk -xelatex main.tex`。

## 用法

1. 把模板文件夹复制到这里并改名，如 `reports/2026-os-lab3/`；
2. 改 `main.tex` 的标题、姓名、学号，删除示例章节后写正文；
3. 编译生成的 PDF 可以提交（仓库默认保留 PDF，方便在 GitHub 上直接预览）。

## 索引

- 暂无
