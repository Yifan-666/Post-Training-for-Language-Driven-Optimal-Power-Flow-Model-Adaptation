# ProOPF Transactions full-paper V1

这是第一版完整论文母稿。它采用官方 IEEE Transactions 的 `IEEEtran` 期刊双栏格式，不受扩展摘要的两页限制。当前 PDF 为 9 页（US Letter、10 pt 正文）。

## 文件

- `main.tex`：论文正文与醒目的红色实验/作者 TODO。
- `references.bib`：当前引用的 23 篇论文、软件和官方运行资料。
- `figures/framework.png`：框架图。
- `main.pdf`：已编译的 V1 预览。

## 编译

在本目录运行：

```bash
latexmk -pdf -interaction=nonstopmode -file-line-error main.tex
```

清理辅助文件但保留 PDF：

```bash
latexmk -c
```

本机安装的 IEEEtran 1.8b 会对官方示例使用的 `lettersize` 选项给出一个无害警告；实际输出已经核验为 Letter 纸张、10 pt、双栏。当前没有未解析引用、交叉引用、表格越栏或致命编译错误。

## 当前证据边界

| 内容 | V1 状态 |
|---|---|
| DP-v11/BP-v6 数据规模、split、post-state 审计与回归测试 | 可复核，已作为正文事实 |
| DP-v11/BP-v6 上的最终 SFT/baseline | 尚未运行，保留 TODO |
| 正文中的 SFT 与 baseline 数值 | 来自旧 DP-v10/BP-v5，仅标为 preliminary `E2E_obj` |
| 三阶段 Physics-Aware reward | 方法设计已写入，最终权重未定 |
| parameter/structure verifier | 已用于审计和严格候选评测；尚未接入最终 RL reward |
| RL 性能 | 当前不作性能结论；旧 L3 提升不可复核 |
| feasibility residual/solver termination 指标 | 尚未进入现有 evaluator，正文已明确为 TODO |
| 作者、顺序、通讯作者、基金与致谢 | 待老师确认 |

## 完稿前优先顺序

1. 决定 49 条含内部 level 名称的 rationale 是否一次性重写并事实审计。
2. 冻结 parser、目标值容差及严格指标；必要时补全 4,523 条 gold 的逐条结构审计。
3. 用 DP-v11 train/dev 重跑课程 SFT，只用 dev 选 checkpoint。
4. 在 BP-v6 上一次性运行最终 baseline/SFT 严格评测，替换旧结果表。
5. 根据 SFT 的 dev 错误类型确定三级奖励权重，把确定性 verifier 接入 `RL/proopf_reward.py`，完成 reward parity tests 后再做 GRPO。
6. 补课程/replay、rationale 权重、reward gate、结构 verifier 和 solver feedback 消融。
7. 补两个人工可读工程案例、AC/DC/系统规模/对象/结构族分组结果及训练和求解成本。
8. 确认作者信息，并最终核对 2025--2026 文献的卷期、页码、DOI 与 API 模型版本。

红色 `TODO` 是有意保留的：它们用于区分已完成事实、拟议方法和缺失实验，最终投稿前必须全部删除或替换。
