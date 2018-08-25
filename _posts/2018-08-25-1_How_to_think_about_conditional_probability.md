---
layout: post
title: 理解条件概率：极限角度
date: 2018-08-25 16:54:06 
tag: 概率与统计
---



<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

# 引言
条件概率是概率论中的一个重要概念。在一般的“概率论”教材中，它出现的位置往往十分地靠前，常跟随在概率公理的后面，或出现在同一章里。它的定义可以帮助我们更轻松地计算欲求概率，进而得到我们所需要的信息。对于绝大多数的读者而言，条件概率的定义简单到可以很容易地背诵并应用在各种场景中。然而，关于“它的定义是如何产生的”这一有趣的问题，本可以有更进一步的讨论。

当然，为了方便之后的讨论，我先在这里引入条件概率的定义[^def]。对于这个定义，我暂时不做任何说明。

$$
Definition \quad 1 \\
If  \quad P(F)>0, then \quad P(E|F)=\frac{P(EF)}{P(F)}
$$

在进行下一步讨论之前，我先来讲一讲韦恩图[^Venndef]在证明概率论中的定理的例子。
## 韦恩图证明容斥原理的特例

$$
Proposition \quad 1 \\ 
P(E\cup F) =P(E)+P(F)-P(E \cap F)
$$

![](/images/posts/1/Venn.png)

由图可知：

$$
E \cup F = I \cup II \cup III \\
E= I \cup II \\
F = II \cup III \\
EF = II
$$

由于这三个事件互不相交,由第三概率公理有：

$$
P(E \cup F )= P(I) + P(II) + P(III) \\
P(E) = P(I) + P(II) \\
P(F) = P(II) +P( III) \\
P(EF) = P(II)
$$

所以，

$$
P(E\cup F)=P(E)+P(F)-P(E \cap F)
$$

这里，韦恩图与概率之间的加减法联系在了一起。这是韦恩图的定义与第三概率公理共同作用的结果：**韦恩图负责展示哪个事件是由哪些互不相关的小事件合并而成，第三概率公理负责将这个关系翻译成含有加减算符的等式。**
## “概率除法”
**对于条件概率的定义，很多人在用“概率除法”的角度去理解[^div]，甚至试图通过韦恩图来为这个想法背书。但这样做实际上是不行的——至少是不显然的。**
正如之前的例子所展示的那样，韦恩图确实可以跟概率之间的数值运算联系起来，也确实可以用于对某些定理的证明。然而，这仅限于加减法。且不论在这里韦恩图只是事件间关系的不严格的直观表达，单在概率公理中便找不到与除法有关的内容。**如果无法与概率公理直接或间接的联系起来，这样的理解便是有问题的。**

因此，有必要从一种新的角度来理解条件概率的定义。这就是我将要在下文中做出的工作。
# 概率：频率的极限
事实上，一个事件的概率可以用这样的定义来表示：

$$
P(E) = \lim_{N \rightarrow \infty } \frac{N(E)}{N}
$$

其中N表示实验的次数，N(E)表示事件E发生的次数。概率公理可以保证这样的极限总是收敛的。[^review]

那么，我们要怎样计算\\(P(E|F)\\)呢？我们想找的其实是，在F发生的情况下，E事件发生的概率。
换句话说，就是E随F发生的频率的极限。

想象我们做了N次实验，我们首先找出F发生的那些实验。`如果N(F)>0的话`，我们就把它们挑出来。然后我们再数挑出来后的实验中，E发生的次数，也就是N(EF)。
于是，根据定义，就有了：
\\[
P(E|F) = \lim_{N \rightarrow \infty } \frac{N(EF)}{N(F)}
\\]
进一步操作：
\\[
\lim_{N \rightarrow \infty } \frac{N(EF)}{N(F)} = \lim_{N \rightarrow \infty } \frac{ \frac{N(EF)}{N}  }{   \frac{N(F)}{N}   }
\\]
由于主分式分子分母的极限存在：
\\[
\lim_{N \rightarrow \infty } \frac{ \frac{N(EF)}{N}  }{   \frac{N(F)}{N}   }
=
 \frac{ \lim_{N \rightarrow \infty } \frac{N(EF)}{N}  }{ \lim_{N \rightarrow \infty }  \frac{N(F)}{N}   }
 =
 \frac{P(EF)}{P(F)}
\\]
即：

\\[
P(E|F)=\frac{P(EF)}{P(F)}
\\]


[^def]:Ross, S. M. (1998). A first course in probability. American Statistician, 56(3), 247-247.

[^div]:[如何理解条件概率？ - 知乎](https://www.zhihu.com/question/27462939)

[^Venndef]:实际上更多地是叫文氏图，参看[百度百科-文氏图](https://baike.baidu.com/item/%E6%96%87%E6%B0%8F%E5%9B%BE/5017234?fr=aladdin)

[^review]:其实这里又有一个新的问题，即如何看待这样的一个定义。但是我懒得写了。

