# 通用中文报告 / 技术文档 LaTeX 模板

一个简洁、无封面的中文 LaTeX 模板，适合写**课程实验报告、技术总结、学习笔记**。
基于标准 `article` 类 + `ctex`，开箱即用，关键处都有中文注释。

## 特性

- 中文支持（XeLaTeX + ctex，Windows / macOS / Linux 自动适配系统字体）
- 数学公式、定理 / 引理 / 定义环境
- 代码高亮（`listings`，内置 Python / Java / C++ / Bash 等）
- 图片、三线表
- 参考文献：**GB/T 7714-2015 国标格式**，写 `.bib` 即可，编号排序全自动
- A4、页边距 2.5 cm、1.5 倍行距、深蓝色链接

## 文件说明

| 文件 | 作用 |
|---|---|
| `main.tex` | 模板正文，所有示例和中文注释都在这里，写新报告只改它 |
| `references.bib` | 参考文献库（BibTeX 格式） |
| `figures/` | 放图片 |
| `main.pdf` | 编译产物，可直接打开看效果 |

## 编译方法

中文**必须用 XeLaTeX**（不能用 pdfLaTeX）。

### 命令行（推荐 latexmk，自动处理参考文献编译次数）

```bash
latexmk -xelatex main.tex
```

清理中间文件（保留 PDF）：

```bash
latexmk -c
```

### 手动编译（不用 latexmk 时）

```bash
xelatex main
biber main
xelatex main
xelatex main
```

### VS Code（LaTeX Workshop 插件）

设置中将默认 recipe 设为 **latexmk (xelatex)**，或在 `settings.json` 中添加：

```json
"latex-workshop.latex.recipe.default": "latexmk (xelatex)"
```

保存 `main.tex` 后会自动编译，点击右上角按钮可预览 PDF。

## 使用方式

1. 复制整个文件夹，改成你的报告名（如 `os-lab3-page-replace/`）；
2. 打开 `main.tex`，修改「文档信息」区的标题、姓名、学号、邮箱；
3. 删掉示例章节，开始写正文；
4. 新文献往 `references.bib` 里加条目（Google 学术 / DBLP 可直接复制 BibTeX）；
5. 图片放进 `figures/`，用 `\includegraphics` 引用。

## 常见问题

**Q：编译报字体错误？**
A：ctex 默认自动检测系统字体。若失败，在 `main.tex` 中手动指定字体集：
Windows 用 `\usepackage[fontset=windows]{ctex}`，macOS 用 `fontset=mac`，Linux 用 `fontset=fandol`。

**Q：参考文献显示不出来 / 是 `[?]`？**
A：必须跑 `biber`，用 `latexmk -xelatex` 会自动完成；手动编译要按上面的四步顺序来。

**Q：代码块里想要中文注释 / 字符串？**
A：`listings` 对中文支持不好（可能错位）。代码内注释建议用英文；如果确需中文，
可改用 `minted` 宏包——需先安装 Python 与 Pygments（`pip install Pygments`），
并用 `xelatex -shell-escape` 编译，示例：

```latex
\usepackage{minted}
\begin{minted}{python}
print("你好")  # 中文注释
\end{minted}
```

**Q：想要封面 / 课程论文样式？**
A：在此模板基础上加一个 `titlepage` 环境即可；也可以让我再帮你做一个带封面的版本。
