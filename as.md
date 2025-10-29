

## $\S 5$ 不可约多项式

### 一、不可约多项式的定义

```ad-def
title:定义8 不可约多项式
设 $f(x)\in \mathbb{P}[x]$ 且 $\deg f(x) \ge 1$。  
若 $f(x)$ 不能写成两个次数小于它的非常数多项式的乘积，即：
$$
f(x)=g(x)h(x)\Rightarrow \text{$g(x)$ 或 $h(x)$ 为常数多项式，}
$$
则称 $f(x)$ 在域 $\mathbb{P}$ 上**不可约**。  
否则称为**可约多项式**。
```

```ad-note
title:说明
1. 不可约性的讨论依赖于系数所在的域。  
   例如：$x^2+1$ 在 $\mathbb{R}[x]$ 中不可约，但在 $\mathbb{C}[x]$ 中可约；
2. 一次多项式必不可约；
3. 若 $f(x)$ 为不可约多项式，则其任意常数倍 $c f(x)\ (c\ne0)$ 亦不可约；
4. 若 $f(x)$ 可约，则必存在非常数公因式。
```

---

### 二、不可约多项式的基本性质

```ad-theorem
title:定理5 不可约多项式的整除性质
设 $p(x)$ 是 $\mathbb{P}[x]$ 上的不可约多项式。  
若 $p(x)\mid f(x)g(x)$，则 $p(x)\mid f(x)$ 或 $p(x)\mid g(x)$。
```

```ad-proof
collapse:closed
若 $p\nmid f$，则 $\gcd(p,f)=1$（否则存在非常数公因式，违背不可约性）。  
由贝祖等式，存在 $u,v\in\mathbb{P}[x]$ 使
$$
p(x)u(x)+f(x)v(x)=1。
$$
两边乘以 $g(x)$，得：
$$
g(x)=p(x)(u(x)g(x))+f(x)(v(x)g(x))。
$$
因为 $p\mid f(x)g(x)$，故 $p\mid f(x)(v(x)g(x))$，从而 $p\mid g(x)$。
```

---

```ad-corollary
title:推论1
若 $p(x)$ 不可约，且 $p(x)\mid f_1(x)f_2(x)\cdots f_n(x)$，  
则 $p(x)$ 至少整除其中一个 $f_i(x)$。
```

```ad-proof
collapse:closed
对 $n$ 用数学归纳法。  
当 $n=2$ 时即为定理结论。  
设对 $n=k$ 成立，若 $p\mid f_1\cdots f_{k+1}$，  
若 $p\nmid f_{k+1}$，则 $p\mid f_1\cdots f_k$，由归纳假设得证。
```

---

```ad-corollary
title:推论2
若 $p(x)$ 不可约，且 $p(x)\mid f(x)g_1(x)$、$p(x)\mid f(x)g_2(x)$，  
则 $p(x)\mid f(x)\gcd(g_1,g_2)$。
```

```ad-proof
collapse:closed
由 $p\mid fg_1,\, p\mid fg_2$，得 $p\mid f(u g_1+v g_2)$，  
其中 $u,v$ 使 $u g_1+v g_2=\gcd(g_1,g_2)$。  
故 $p\mid f\gcd(g_1,g_2)$。
```

---

### 三、因式分解定理（存在性）

```ad-theorem
title:定理6 多项式的因式分解存在定理
任意非零、非常数多项式 $f(x)\in\mathbb{P}[x]$，  
都可以表示为若干不可约多项式的乘积：
$$
f(x)=p_1(x)p_2(x)\cdots p_r(x)，
$$
其中各 $p_i(x)$ 不可约。
```

```ad-proof
collapse:closed
用次数归纳法。  
若 $\deg f=1$，显然成立。  
假设次数小于 $n$ 的多项式均可分解为不可约因式。  
当 $\deg f=n>1$ 时：  
- 若 $f$ 不可约，结论成立；  
- 若 $f$ 可约，设 $f=g h$，且 $\deg g,\deg h<n$。  
由归纳假设，$g,h$ 各可分解为不可约多项式之积，  
于是 $f$ 也可分解为不可约多项式的积。
```

---

### 四、因式分解的唯一性

```ad-theorem
title:定理7 多项式因式分解唯一性定理
设 $f(x)\in\mathbb{P}[x]$，  
若存在两种不可约分解：
$$
f(x)=p_1p_2\cdots p_r=q_1q_2\cdots q_s，
$$
其中每个 $p_i,q_j$ 均不可约且首项系数为 1，  
则 $r=s$，并且经过重新排列后有 $p_i=q_i$。
```

```ad-proof
collapse:closed
由存在性定理，分解必存在。  
我们证明唯一性：  
$p_1\mid q_1q_2\cdots q_s$，  
由定理5 知 $p_1\mid q_j$ 对某 $j$ 成立。  
因二者均首一且不可约，故 $p_1=q_j$。  
消去该因式后，  
对余式重复同理，归纳得 $r=s$ 且 $p_i=q_i$。
```

---

```ad-corollary
title:推论3
域 $\mathbb{P}$ 上的一元多项式环 $\mathbb{P}[x]$  
是一个**唯一分解整环（UFD）**。
```

---

### 五、标准分解式

```ad-def
title:标准分解式
若
$$
f(x)=a p_1^{k_1}(x)p_2^{k_2}(x)\cdots p_t^{k_t}(x)
$$
为 $f(x)$ 的分解式，且各 $p_i(x)$ 均首一并互素，  
则称此式为 $f(x)$ 的**标准分解式**。
```

```ad-corollary
title:推论4
多项式的标准分解式在 $\mathbb{P}[x]$ 中是唯一的。
```

---

### 六、小结

```ad-summary
title:本节要点
- **不可约定义：** $f=gh$ ⇒ $g$ 或 $h$ 为常数；
- **依域性：** 不可约性取决于系数域；
- **基本性质：** $p\mid fg$ ⇒ $p\mid f$ 或 $p\mid g$；
- **存在性：** 任意非零多项式都可分解为不可约因式；
- **唯一性：** 不可约分解除顺序与常数倍外唯一；
- **标准分解式：** 各因子首一且互素，唯一确定；
- **结论：** $\mathbb{P}[x]$ 是唯一分解整环（UFD）。
```

---
