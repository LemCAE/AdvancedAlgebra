## 基本概念

```ad-def
title: p-adic 数
**p-adic 数**是实数的一种替代完备化，基于完全不同的度量观念。对于固定素数 $p$，p-adic 数的绝对值由**整除性**而非**大小**决定。
```

---

## p-adic 赋值 (Valuation)

### **定义与性质**

```ad-def
title: p-adic 赋值
对于整数 $a \neq 0$ 和素数 $p$，**p-adic 赋值** $v_p(a)$ 定义为满足 $p^k \mid a$ 的最大整数 $k$。

即：$v_p(a) = \max\{k \in \mathbb{Z} : p^k \mid a\}$

特殊约定：$v_p(0) = \infty$
```

```ad-example
title: p-adic 赋值计算
- $v_2(12) = 2$（因为 $12 = 2^2 \times 3$）
- $v_3(27) = 3$（因为 $27 = 3^3$）
- $v_5(7) = 0$（因为 $5^0 = 1$ 整除 7，但 $5^1$ 不整除）
- $v_2(0) = \infty$
```

### **扩展到有理数**

```ad-def
title: 有理数的 p-adic 赋值
对于有理数 $r = \frac{a}{b}$（$a,b \in \mathbb{Z}$，$b \neq 0$）：
$$v_p\left(\frac{a}{b}\right) = v_p(a) - v_p(b)$$
```

```ad-example
title: 有理数的 p-adic 赋值
- $v_2\left(\frac{3}{4}\right) = v_2(3) - v_2(4) = 0 - 2 = -2$
- $v_3\left(\frac{18}{5}\right) = v_3(18) - v_3(5) = 2 - 0 = 2$
```

---

## p-adic 绝对值

```ad-def
title: p-adic 绝对值
对于非零有理数 $x$，**p-adic 绝对值**定义为：
$$|x|_p = p^{-v_p(x)}$$

特殊约定：$|0|_p = 0$
```

```ad-example
title: p-adic 绝对值计算
- $|12|_2 = 2^{-v_2(12)} = 2^{-2} = \frac{1}{4}$
- $|27|_3 = 3^{-3} = \frac{1}{27}$
- $\left|\frac{3}{4}\right|_2 = 2^{-(-2)} = 2^2 = 4$
```

### **与通常绝对值的对比**

```ad-lemma
title: 不同绝对值的性质比较
| 性质 | 通常绝对值 $\lvert\cdot\rvert$ | p-adic 绝对值 $\lvert\cdot\rvert_p$ |
|------|---------------------|--------------------------|
| **定义基础** | 大小比较 | 整除性 |
| **值域** | $[0, \infty)$ | $\{0\} \cup \{p^k : k \in \mathbb{Z}\}$ |
| **大数概念** | 数值很大 | 被高次幂整除 |
| **小数概念** | 接近 0 | 被高次幂整除 |
| **三角不等式** | $\lvert x+y\rvert \leq \lvert x\rvert + \lvert y\rvert$ | $\lvert x+y\rvert _p \leq \max(\lvert x\rvert _p, \lvert y\rvert _p)$ |
```

---

## p-adic 数的构造

### **完备化过程**

```ad-def
title: p-adic 完备化
类似于从有理数构造实数，通过柯西序列的等价类构造 **p-adic 数域** $\mathbb{Q}_p$：

1. 以 p-adic 绝对值定义度量：$d_p(x,y) = |x-y|_p$
2. 在此度量下，有理数集 $\mathbb{Q}$ 不完备
3. 添加所有柯西序列的极限点，得到完备域 $\mathbb{Q}_p$
```

### **p-adic 展开**

```ad-lemma
title: p-adic 数的级数表示
每个 p-adic 数可以唯一表示为：
$$x = \sum_{k=m}^{\infty} a_k p^k$$
其中 $m \in \mathbb{Z}$，$a_k \in \{0, 1, \ldots, p-1\}$，且 $a_m \neq 0$。

此时 $v_p(x) = m$，$|x|_p = p^{-m}$。
```

```ad-example
title: p-adic 展开示例
在 $\mathbb{Q}_2$ 中：
- $1 = 1 \times 2^0$（$v_2(1) = 0$）
- $2 = 1 \times 2^1$（$v_2(2) = 1$）
- $-1 = 1 + 2 + 2^2 + 2^3 + \cdots$（在 2-adic 意义下收敛）
```

---

## 在多项式理论中的应用

### **p-adic 根的性质**

```ad-lemma
title: 亨泽尔引理 (Hensel's Lemma)
如果多项式 $f(x) \in \mathbb{Z}[x]$ 模 $p$ 有单根 $a$（即 $f(a) \equiv 0 \pmod{p}$ 但 $f'(a) \not\equiv 0 \pmod{p}$），则在 $\mathbb{Q}_p$ 中存在唯一的根 $\alpha$ 满足 $\alpha \equiv a \pmod{p}$。

这允许我们将模 $p$ 的根"提升"到 p-adic 根。
```

### **牛顿多边形与 p-adic 根**

```ad-lemma
title: 牛顿多边形定理的完整表述
多项式 $f(x) \in \mathbb{Q}[x]$ 在 $\mathbb{Q}_p$ 中的根的 p-adic 赋值由牛顿多边形的**斜率**决定：

如果牛顿多边形有一条从 $(i, v_p(a_i))$ 到 $(j, v_p(a_j))$ 的边，斜率为 $-m$，则 $f(x)$ 在 $\mathbb{Q}_p$ 中恰好有 $j-i$ 个根满足 $v_p(\alpha) = m$。
```

```ad-example
title: 牛顿多边形与 p-adic 根的关系
考虑 $f(x) = 2x^3 + 3x^2 + 6x + 9$，取 $p=3$：

系数与 3-adic 赋值：
- $a_3=2$：$v_3(2)=0$，点 $(3,0)$
- $a_2=3$：$v_3(3)=1$，点 $(2,1)$  
- $a_1=6$：$v_3(6)=1$，点 $(1,1)$
- $a_0=9$：$v_3(9)=2$，点 $(0,2)$

牛顿多边形有两条边：
1. $(0,2)$ 到 $(2,1)$，斜率 $-\frac{1}{2}$ → 2 个根满足 $v_3(\alpha) = \frac{1}{2}$
2. $(2,1)$ 到 $(3,0)$，斜率 $-1$ → 1 个根满足 $v_3(\alpha) = 1$
```

---

## 重要性质

### **非阿基米德性质**

```ad-lemma
title: 强三角不等式
p-adic 绝对值满足**强三角不等式**：
$$|x + y|_p \leq \max(|x|_p, |y|_p)$$

等号成立当 $|x|_p \neq |y|_p$。

这导致许多反直觉的结果，如收敛级数的条件更宽松。
```

### 完备性与紧致性

```ad-lemma
title: p-adic 域的性质
1. **完备性**：$\mathbb{Q}_p$ 在 p-adic 度量下是完备的
2. **局部紧致性**：$\mathbb{Z}_p$（p-adic 整数）是紧致的
3. **不连通性**：$\mathbb{Q}_p$ 是完全不连通的
```

---

## 与其他理论的联系

### **与实数理论的对比**

```ad-lemma
title: 实数与 p-adic 数的对偶性
根据**奥斯特洛夫斯基定理**，有理数 $\mathbb{Q}$ 上本质上只有两种绝对值（等价类）：

1. **通常绝对值**：导向实数 $\mathbb{R}$
2. **p-adic 绝对值**：对于每个素数 $p$，导向 p-adic 数 $\mathbb{Q}_p$

这种对偶性反映了数论的深刻对称性。
```

---

## 总结

p-adic 性质的核心思想是：

1. **重新定义"接近"**：两个数接近当且仅当它们的差能被高次幂整除
2. **度量基于整除性**：p-adic 绝对值衡量一个数被 $p$ 整除的程度
3. **局部信息**：每个素数 $p$ 提供一个"局部"视角
4. **几何应用**：通过牛顿多边形等工具，p-adic 性质可用来研究多项式的不可约性和根的分布
