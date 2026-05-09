# Introduction to Probability Notes

这是我学习 Dimitri P. Bertsekas 和 John N. Tsitsiklis 的 *Introduction to Probability* 时使用的公开笔记仓库。

推荐的公开方式：把这个 Obsidian vault 作为一个 **public GitHub repository**。主笔记用 Markdown 写，GitHub 可以直接预览；以后有 Python 模拟、小实验或 Jupyter Notebook，也放在同一个仓库里，方便把知识总结和计算实验连在一起。

## Structure

- [Knowledge](Knowledge/00%20-%20Index.md): 概念、定义、定理、公式、例题总结。
- [Thoughts](Thoughts/00%20-%20Index.md): 自己的问题、直觉、误区、学习日志和开放想法。
- [Simulations](Simulations/README.md): Python 概率模拟、小项目、图像和 notebook。

## Writing Rules

- 用自己的话总结，不整段搬运教材原文。
- 重要公式用 LaTeX，例如 `$P(A \mid B) = \frac{P(A \cap B)}{P(B)}$`。
- 每条知识点尽量记录三个部分：它是什么、为什么重要、什么时候会用错。
- 想法和疑问不要强行整理成熟结论，先放进 `Thoughts`，以后再迁移到 `Knowledge`。

## Workflow

1. 在 Obsidian 中写 Markdown 笔记。
2. 在 `Simulations` 中写 Python 脚本或 Jupyter Notebook。
3. 用 Git 把修改提交到 GitHub。
4. GitHub 仓库设为 public 后，这个仓库本身就是公开笔记。

