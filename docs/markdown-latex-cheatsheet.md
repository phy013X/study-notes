# Markdown + LaTeX 公式 + 图片写法速查

在这个仓库里写笔记天天用到的语法，按需翻阅。GitHub 网页和 VS Code 预览（`Ctrl+Shift+V`）均支持。

## 1. Markdown 核心语法

```markdown
# 一级标题（笔记里一般从 ## 开始，# 留给文件大标题）
## 二级标题
### 三级标题

**加粗**  *斜体*  ~~删除线~~  `行内代码`

- 无序列表项
  - 缩进二级
1. 有序列表第一项
2. 第二项

- [ ] 未完成的任务
- [x] 已完成的任务（很适合列学习计划）

> 引用：书中的一句话 / 老师强调的重点

[链接文字](https://github.com)
[链接到仓库里的另一篇笔记](../courses/os/README.md)   <!-- 相对路径，可点击跳转 -->

| 算法 | 复杂度 |
|---|---|
| 冒泡 | $O(n^2)$ |
| 归并 | $O(n\log n)$ |

---  <!-- 分隔线 -->
```

## 2. 数学公式（GitHub 原生支持 LaTeX）

**行内公式**用单个 `$`：勾股定理是 $a^2+b^2=c^2$，求和 $\sum_{i=1}^{n}i=\frac{n(n+1)}{2}$。

**行间公式**用 `$$` 且**独占一行**：

```latex
$$
\frac{\partial L}{\partial w},\qquad
\int_{0}^{\infty} e^{-x^2}\,\mathrm{d}x=\frac{\sqrt{\pi}}{2},\qquad
\mathbf{A}\begin{pmatrix}x\\y\end{pmatrix}=\begin{pmatrix}1\\0\end{pmatrix}
$$
```

高频写法速查：

| 效果 | 写法 | 效果 | 写法 |
|---|---|---|---|
| 上标/下标 | `x^2`、`a_i`、`x^{2n}` | 分式 | `\frac{a}{b}` |
| 根号 | `\sqrt{x}`、`\sqrt[3]{x}` | 求和/积分 | `\sum_{i=1}^{n}`、`\int_{a}^{b}` |
| 希腊字母 | `\alpha \beta \gamma \pi \sigma \Delta \Omega` | 不等号 | `\neq \leq \geq \approx \equiv` |
| 向量/矩阵 | `\vec{v}`、`\mathbf{A}`、`\binom{n}{k}` | 箭头 | `\rightarrow \Rightarrow \mapsto` |
| 点乘/省略号 | `\cdot`、`\cdots \vdots` | 帽子/横线 | `\hat{y}`、`\bar{x}`、`\overline{AB}` |

多行公式对齐（推导过程必备）：

```latex
$$
\begin{aligned}
L &= (y-\hat{y})^2 \\
  &= (y-wx)^2 \\
\frac{\partial L}{\partial w} &= -2x(y-wx)
\end{aligned}
$$
```

> ⚠️ GitHub 两个踩坑点：
> 1. 行内 `$` **内侧不要加空格**：写 `$x^2$` 而不是 `$ x^2 $`；结尾 `$` 后**不要紧跟数字**（会被当成货币符号）。
> 2. 代码块里的 `$` 不会被当公式，shell 命令放心写。

## 3. 代码块与图表

代码块用三个反引号并**标注语言**（GitHub 自动高亮）：

````
```python
def fib(n):
    return n if n < 2 else fib(n-1) + fib(n-2)
```
````

GitHub **原生支持 Mermaid 图表**，画流程图、时序图、类图免装工具：

````
```mermaid
flowchart LR
    A[用户输入] --> B[编译器] --> C[可执行文件]
    C --> D[运行结果]
```
````

常用的还有 `sequenceDiagram`（时序图）、`classDiagram`（类图）、`stateDiagram-v2`（状态图）。

## 4. 图片：VS Code 截图直接粘贴

仓库图片统一放 `resources/images/年/月/`。仓库已配置好：截图后在 `.md` 里直接 `Ctrl+V`，
VS Code 自动把图片存进对应目录并生成链接：

```markdown
![截图](resources/images/2026/09/image.png)
```

想控制显示大小（GitHub 的 `![]()` 语法不支持宽度），改用 HTML：

```html
<img src="../../resources/images/2026/09/arch.png" width="480">
```

## 5. 本地预览与写作体验

- **Markdown 预览**：`Ctrl+Shift+V` 全屏预览，或 `Ctrl+K` 松开后按 `V` 开双栏实时预览；
- **笔记互链一律写相对路径**（`../courses/os/xxx.md`），本地、GitHub、未来建站三者都能点开；
- 推荐插件：**Markdown All in One**（目录生成、列表自动续号、快捷键）、**markdownlint**（语法提示）。

## 6. 什么时候改用纯 LaTeX

| 场景 | 用什么 |
|---|---|
| 每日笔记、技术总结、带公式的推导、代码笔记 | **Markdown**（`.md`，GitHub 直接渲染） |
| 要交的课程报告、实验报告、正式论文 | **纯 LaTeX**（用 [`../templates/latex-report-template/`](../templates/latex-report-template/README.md)） |

判据：**给自己看、放网页看 → Markdown；要打印上交、格式有硬性要求 → LaTeX。**
