---
title: "ptt-math [分析] 求範圍"
date: 2020-10-01T11:09:00+08:00
draft: false
dropCap: false
categories:
    - "Math"
---

文章：[[分析] 求範圍 by jazzter@ptt](http://www.ptt.cc/bbs/Math/M.1342593839.A.24E.html)

<!--more-->

題目：證明下列不等式成立。

<div>
$$
\frac{2(a_1^2+a_2^2+a_3^2+a_4^2)}{(a_1+a_2+a_3+a_4)^2} - \frac{(a_1^3+a_2^3+a_3^3+a_4^3)}{(a_1+a_2+a_3+a_4)^3} \geq \frac{7}{16}
$$
</div>

----

解答：直接暴力通分，然後交叉相乘。然後可以化簡拆開成下列諸項：

<div>
$$
\begin{aligned}
&3(a_1^3 + a_2^2a_3 + a_2a_3^2 - 3a_1a_2a_3)\\
&3(a_1^3 + a_2^2a_4 + a_2a_4^2 - 3a_1a_2a_4)\\
&3(a_1^3 + a_3^2a_4 + a_3a_4^2 - 3a_1a_3a_4)\\
&3(a_2^3 + a_1^2a_3 + a_1a_3^2 - 3a_1a_2a_3)\\
&3(a_2^3 + a_1^2a_4 + a_1a_4^2 - 3a_1a_2a_4)\\
&3(a_2^3 + a_3^2a_4 + a_3a_4^2 - 3a_2a_3a_4)\\
&3(a_3^3 + a_1^2a_2 + a_1a_2^2 - 3a_1a_2a_3)\\
&3(a_3^3 + a_1^2a_4 + a_1a_4^2 - 3a_1a_3a_4)\\
&3(a_3^3 + a_2^2a_4 + a_2a_4^2 - 3a_2a_3a_4)\\
&3(a_4^3 + a_1^2a_2 + a_1a_2^2 - 3a_1a_2a_4)\\
&3(a_4^3 + a_1^2a_3 + a_1a_3^2 - 3a_1a_3a_4)\\
&3(a_4^3 + a_2^2a_3 + a_2a_3^2 - 3a_2a_3a_4)\\
&5(a_1^2a_2 + a_2^2a_3 + a_3^2a_1 - 3a_1a_2a_3)\\
&5(a_1^2a_2 + a_2^2a_4 + a_4^2a_1 - 3a_1a_2a_4)\\
&5(a_1^2a_3 + a_3^2a_4 + a_4^2a_1 - 3a_1a_3a_4)\\
&5(a_2^2a_3 + a_3^2a_4 + a_4^2a_2 - 3a_2a_3a_4)
\end{aligned}
$$
</div>

由算幾不等式可得每一項皆是正的，故本題得證。

其它強者的解法：

+ [LimSinE@ptt](https://www.ptt.cc/bbs/Math/M.1342603205.A.B14.html)
+ [JohnMash@ptt](https://www.ptt.cc/bbs/Math/M.1342604850.A.605.html)
+ [TWN2@ptt](https://www.ptt.cc/bbs/Math/M.1342650313.A.2C6.html)