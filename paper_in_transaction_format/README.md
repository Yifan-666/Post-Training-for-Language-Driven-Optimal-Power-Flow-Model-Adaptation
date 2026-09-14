# ProOPF paper in IEEE Transactions format

ProOPF 论文的 IEEE Transactions 格式稿件。当前版本位于 [`V1/`](V1/)，包含 LaTeX 正文、参考文献、框架图和已编译的 PDF 预览。

- [论文源码](V1/main.tex)
- [PDF 预览](V1/main.pdf)
- [参考文献](V1/references.bib)
- [V1 说明与待完成事项](V1/README.md)

## 编译

需要 LaTeX 环境、`IEEEtran` 文档类和 `latexmk`。在 `V1` 目录运行：

```bash
latexmk -pdf -interaction=nonstopmode -file-line-error main.tex
```

清理辅助文件并保留 PDF：

```bash
latexmk -c
```

仓库保留源码、图片和 PDF，忽略可重新生成的 LaTeX 编译辅助文件。文中的 TODO 和实验结果以该版本稿件及其说明为准；此目录不会自动同步项目其他位置的新实验结果。
