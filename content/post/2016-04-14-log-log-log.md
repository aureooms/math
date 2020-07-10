---
date: 2016-04-14T00:00:00Z
title: Log Log Log
url: /2016/04/14/log-log-log/
thumbnail:
  src: https://ipfs.c.ovfefe.cf/ipfs/QmRqy5uiX5KXLUe52bF5ADozyxHPuNAgdWiVbZ8vqZUnYi
tags:
  - Identities
  - Inequalities
  - Analysis of Algorithms
---

## Theorem

$$
\frac{\log n}{\log \log n}! = \Theta(n)
$$

<!--more-->
## Proof

$$
\begin{aligned}
K^2! &= \sqrt{\frac{\log n}{\log \log n}}^2!\\
&= \frac{\log n}{\log \log n}!\\
\lim_{K^2 \to \infty} K^2! &= \sqrt{2\pi \frac{\log n}{\log \log n}}
\left( \frac{\frac{\log n}{\log \log n}}{e}\right)^\frac{\log n}{\log \log
n}\\
\lim_{n \to \infty} K^2! &= \sqrt{2\pi \frac{\log n}{\log \log n}}
\left( \frac{\frac{\log n}{\log \log n}}{e}\right)^\frac{\log n}{\log \log
n}\\
&= \sqrt{2\pi \frac{\log n}{\log \log n}}
\left( \frac{\log n}{e \log \log n}\right)^\frac{\log n}{\log \log n}\\
&= \sqrt{2\pi \frac{\log n}{\log \log n}}
\frac{2^{\log \log n\frac{\log n}{\log \log n}}}{2^{\log \log \log n\frac{\log n}{\log \log n}}
2^{\log e\frac{\log n}{\log \log n}}
}\\
&= \sqrt{2\pi \frac{\log n}{\log \log n}}
\frac{n}{n^{\frac{\log \log \log n}{\log \log n}}
n^{\frac{\log e}{\log \log n}}
}\\
&= \sqrt{2\pi \frac{2^{\log \log n}}{2^{\log \log \log n}}}
\frac{n}{n^{\frac{\log \log \log n}{\log \log n}}
n^{\frac{\log e}{\log \log n}}
}\\
&= \sqrt{2\pi \frac{n^{\frac{\log \log n}{\log n}}}{n^{\frac{\log \log \log
n}{\log n}}}}
\frac{n}{n^{\frac{\log \log \log n}{\log \log n}}
n^{\frac{\log e}{\log \log n}}
}\\
&= \sqrt{2\pi} \frac{n^{\frac{\log \log n}{2\log n}}}{n^{\frac{\log \log \log
n}{2\log n}}}
\frac{n}{n^{\frac{\log \log \log n}{\log \log n}}
n^{\frac{\log e}{\log \log n}}
}\\
&= \sqrt{2\pi} \frac{n^{\frac{\log \log n}{2\log n}}}{n^{\frac{\log \log \log
n}{2\log n}}}
\frac{n}{n^{\frac{\log \log \log n + \log e}{\log \log n}}
}\\
&= \sqrt{2\pi} \frac{n^{\frac{(\log \log n)^2}{2\log n\log\log
n}}}{n^{\frac{\log \log n \log
\log \log n}{2\log n \log \log n}}}
\frac{n}{n^{\frac{2 \log n \log \log \log n + 2 \log n \log e}{2\log n \log \log n}}
}\\
&= \sqrt{2\pi}
\frac{n}{n^{\frac{2 \log e \log n + 2 \log n \log \log \log n + \log \log n
\log \log \log n - (\log \log n)^2}{2\log n \log \log n}}
}\\
&= \sqrt{2\pi}
\frac{n}{n^{\frac{2 \log n \log \log \log n}{2\log n \log \log n}}
}\\
&= \sqrt{2\pi}
\frac{n}{n^{\frac{\log \log \log n}{\log \log n}}
}\\
&= \sqrt{2\pi} n^{1 - \frac{\log \log \log n}{\log \log n}}\\
\end{aligned}
$$
