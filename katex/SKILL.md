---
name: katex-math
description: Use KaTeX-compatible mathematical notation in Markdown responses when equations, formulas, matrices, or symbolic relationships would be clearer than prose. The session viewer renders inline and display math.
---

# KaTeX Mathematical Notation

The session viewer renders KaTeX in conversation messages and Markdown documents. Use this capability when mathematical notation
materially improves precision or readability; do not avoid useful notation because the response will be viewed as Markdown.

## Syntax

Use single dollar delimiters for short inline expressions:

```markdown
The runtime is $O(n \log n)$ and the loss is $L(\theta)$.
```

Use double dollar delimiters for important, long, or multiline expressions:

```markdown
$$
\operatorname{cost}
= \frac{t_{in}}{10^6}p_{in}
+ \frac{t_{out}}{10^6}p_{out}
$$
```

For multiline equations, use `aligned` inside a display block:

```markdown
$$
\begin{aligned}
f(x) &= x^2 + 2x + 1 \\
     &= (x + 1)^2
\end{aligned}
$$
```

## Guidance

- Prefer standard KaTeX-supported TeX commands and environments.
- Keep short expressions inline; reserve display blocks for equations that benefit from visual separation.
- Use `aligned`, not the top-level `align` environment, inside `$$` blocks.
- Do not place intended rendered mathematics inside backticks or fenced code blocks.
- Escape literal paired dollar signs as `\$` when they could otherwise be parsed as math.
- Avoid MathJax-specific extensions, dynamic `\require`, and unusual LaTeX packages unless the user explicitly needs them and KaTeX compatibility has been verified.
- When an uncommon command is unnecessary, rewrite it using simpler supported notation rather than risking a broken expression.
