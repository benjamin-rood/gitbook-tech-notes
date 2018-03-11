## KaTeX

You can render LaTeX mathematical expressions using [KaTeX](https://khan.github.io/KaTeX/):

### Usage

```
Using the templating syntax:
{% math %}\int_{-\infty}^\infty g(x) dx{% endblock %}

Inline math: $$\int_{-\infty}^\infty g(x) dx$$
```



```
Block math:

$$
\int_{-\infty}^\infty g(x) dx
$$
```


$$
\int_{-\infty}^\infty g(x) dx
$$


You can also use the shortcut `$$`: So, `$$a \ne 0$$` $$\mapsto$$ $$a \ne 0$$, for example.

#### Examples

When $$a \ne 0$$, there are two solutions to $$(ax^2 + bx + c = 0)$$ and they are $$x = {-b \pm \sqrt{b^2-4ac} \over 2a}$$

The _Gamma function_ satisfying $$\ \Gamma(n) = (n-1)! \ \ \forall\  n\in\mathbb{N}\ \,$$  
is via the Euler integral,


$$
\Gamma(z) = \int_0^\infty t^{z-1}e^{-t}dt\,.
$$


