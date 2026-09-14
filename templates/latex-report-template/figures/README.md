# figures 目录

把论文/报告里用到的图片放在这里。

## 建议

- **优先矢量图**：图表、示意图导出为 PDF 或 SVG（SVG 需先转成 PDF），任意缩放都清晰；
- **照片/截图**用 PNG 或 JPG；
- 文件名用英文小写 + 短横线，例如 `system-arch.png`、`result-chart.pdf`；
- 正文中引用：

```latex
\begin{figure}[htbp]
  \centering
  \includegraphics[width=0.75\linewidth]{figures/system-arch.png}
  \caption{系统架构图}
  \label{fig:arch}
\end{figure}
```
