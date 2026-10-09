# Fourier 变换

> 内容主要参考 Lieb and Loss 的"Analysis".

---

## $`L^1`$ 中的 Fourier 变换

**Def)**  设 $`f \in L^1(\mathbb{R}^n)`$, 定义

```math
\hat{f}(\xi) := \int_{\mathbb{R}^n} f(x) \, e^{-2\pi i x \xi} \, dx
```

为 $`f`$ 在 $`\xi`$ 点处的 Fourier 变换.

- 映射 $`f \mapsto \hat{f}`$ 为线性映射.

**Prop)**

$`(1)`$ $`f \in L^1(\mathbb{R}^n) \Rightarrow \hat{f} \in L^\infty(\mathbb{R}^n)`$, 且

```math
\|\hat{f}\|_\infty \le \|f\|_{L^1}
```

若 $`f \ge 0`$, 则

```math
\|\hat{f}\|_\infty = \|f\|_{L^1}
```

$`(2)`$  $`f \in L^1(\mathbb{R}^n) \Rightarrow \hat{f}`$ 一致连续.

$`(3)`$  (R-L引理) $`f \in L^1(\mathbb{R}^n) \Rightarrow \lim_{|\xi|\to\infty} \hat{f}(\xi) = 0`$.

**pf.**

$`(1)`$ 对任意 $`\xi\in\mathbb{R}^n`$,

```math
|\hat{f}(\xi)| \le \int_{\mathbb{R}^n} |f(x)| \cdot 1 \, dx = \|f\|_{L^1}.
```

若 $`f \ge 0`$, 则

```math
\|\hat{f}\|_\infty \ge \hat{f}(0) = \int_{\mathbb{R}^n} f(x) \, dx = \|f\|_{L^1}.
```

于是

```math
\|\hat{f}\|_\infty = \|f\|_{L^1}
```

$`(2)`$ 设 $`f`$ 处处有限. 对任意 $`h, \xi \in \mathbb{R}^n`$,

```math
|\hat{f}(\xi + h) - \hat{f}(\xi)|
\le \int_{\mathbb{R}^n} |f(x)| \cdot |e^{-2\pi i x (\xi + h)} - e^{-2\pi i x \xi}| \, dx
```

```math
= \int_{\mathbb{R}^n} |f(x)| \, |e^{-2\pi i x h} - 1| \, dx \quad\text{(与 }\xi\text{ 无关)}
```

而

```math
|f(x)| \, |e^{-2\pi i x h} - 1| \le 2|f(x)| \in L^1(\mathbb{R}^n)
```

由 LDCT,

```math
|\hat{f}(\xi + h) - \hat{f}(\xi)|\to 0 \quad \text{as } h \to 0.
```

$`(3)`$ 采用逼近方法.

先设 $`f \in C_c^\infty(\mathbb{R}^n)`$, 取 $`\alpha = (1, 0, \dots, 0)`$, 有

```math
\hat{f}(\xi) = \int_{\mathbb{R}^n} f(x) \, e^{-2\pi i x \xi} \, dx
```

```math
= \frac{1}{(-2\pi i \xi)^\alpha} \int_{\mathbb{R}^n} \partial_x^\alpha \left( e^{-2\pi i x \xi} \right) f(x) \, dx
```

```math
= \frac{-1}{(-2\pi i \xi)^\alpha} \int_{\mathbb{R}^n} e^{-2\pi i x \xi} \, \partial^\alpha f(x) \, dx.
```

因此

```math
|\hat{f}(\xi)| \le C |\xi|^{-1} \int_{\mathbb{R}^n} |\partial^\alpha f(x)| \, dx \to 0 \quad \text{as } |\xi| \to \infty.
```

实际上, 上述过程就是后面介绍的公式:

```math
\widehat{\frac{\partial f}{\partial x_1}} = 2\pi i \xi_1 \hat{f}(\xi).
```

一般地, 对任意 $`\varepsilon > 0`$, 存在 $`h \in C_c^\infty(\mathbb{R}^n)`$, 使得 $`\|f - h\|_{L^1} < \varepsilon`$, 则

```math
|\hat{f}(\xi)| \le |\widehat{f - h}(\xi)| + |\hat{h}(\xi)|
\le \|f - h\|_{L^1} + |\hat{h}(\xi)|
< \varepsilon + |\hat{h}(\xi)| \to \varepsilon.
```

---

### R-L 引理的推论

作为 R-L 引理的推论, 我们证明下面的数学分析中的命题.

**Crly)** 设 $`f \in R[a, b]`$ ($`a`$ 或 $`b`$ 为 $`\infty`$ 时要求 $`f`$ 绝对可积), 则

```math
\lim_{p \to \infty} \int_a^b f(x) \sin px \, dx
= \lim_{p \to \infty} \int_a^b f(x) \cos px \, dx
= 0.
```

**pf. 证法1.** 仿照 R-L 引理, 利用 $`C_0^\infty`$ 逼近.

对任意 $`\varphi \in C_0^\infty(a, b)`$,

```math
\int_a^b \varphi(x) \sin px \, dx
= -\frac{1}{p} \int_a^b \varphi(x) (\cos px)' \, dx
= \frac{1}{p} \int_a^b \varphi'(x) \cos px \, dx.
```

于是

```math
\left| \int_a^b \varphi(x) \sin px \, dx \right|
\le \frac{1}{|p|} \int_a^b |\varphi'| \to 0 \quad \text{as } |p| \to \infty.
```

对 $`f \in R[a, b]`$, 任意 $`\varepsilon > 0`$, 存在 $`\varphi \in C_0^\infty(a, b)`$, 使得

```math
\int_a^b |f - \varphi| < \varepsilon.
```

因此

```math
\left| \int_a^b f(x) \sin px \, dx \right|
\le \varepsilon + \left| \int_a^b \varphi(x) \sin px \, dx \right|,
```

取上极限即可.

**证法2.** 利用紧支撑的阶梯函数逼近, 证明过程见下面的推论.

**Crly)**  设 $`f \in R[a, b]`$ ($`a`$ 或 $`b`$ 为 $`\infty`$ 时要求 $`f`$ 绝对可积), 若 $`g`$ 以 $`T`$ 为周期, 且 $`g \in R[0, T]`$, 则

```math
\lim_{p \to \infty} \int_a^b f(x) g(px) \, dx
= \int_0^T g \cdot \int_a^b f
```

**pf.** 不妨设 $`\int_0^T g = 0`$. 对任意紧支撑的阶梯函数 $`\varphi`$, 要证

```math
\int_a^b f(x) g(px) \, dx \to 0 \quad \text{as } p \to \infty,
```

只要证对有限的 $`a < b`$, 有

```math
\int_a^b g(px) \, dx \to 0.
```

事实上

```math
\left| \int_a^b g(px) \, dx \right|
= \frac{1}{|p|} \left| \int_{pa}^{pb} g(x) \, dx \right|
\le \frac{1}{|p|} \int_0^T |g| \to 0.
```

对 $`f \in R[a, b], \forall \varepsilon > 0, \exists`$ 上述 $`\varphi(x)`$, 使得

```math
\int_a^b |f - \varphi| < \varepsilon.
```

则

```math
\left| \int_a^b f(x) g(px) \, dx \right|
\le \left( \int_a^b |f - \varphi| \right) \sup_{[0, T]} |g| + \left| \int_a^b \varphi(x) g(px) \, dx \right|
```

取上极限即可.

---

### Fourier 变换的基本性质

> 乘多项式的傅里叶变换是傅里叶变换的导数, 导数的傅里叶变换是傅里叶变换乘多项式.
> 可导性看无穷远性质, 导数转嫁衰减性.

**Prop)**

$`(1)`$ 若 $`f \in L^1(\mathbb{R}^n)`$, 则

- 平移:  $`\tau_h f(x) := f(x - h)`$,

```math
\widehat{\tau_h f}(\xi) = e^{-2\pi i h \cdot \xi} \hat{f}(\xi), \quad \tau_h \hat{f}(\xi) = \widehat{(e^{2\pi i h \cdot x} f)}(\xi).
```

- 伸缩:  $`\delta_a f(x) := f(ax)`$, $`a > 0`$,

```math
\widehat{\delta_a f}(\xi) = a^{-n} \hat{f}\left( \frac{\xi}{a} \right), \quad \delta_a\widehat{f}(\xi) = \widehat{a^{-n} f\left( \frac{x}{a} \right)}.
```

即 $`\delta_a \, \cdot`$ 和 $`\cdot\, _a`$ 在 $`\hat{\cdot}`$ 的一内一外:

```math
\widehat{\delta_a f} = \hat{(f)}_a, \quad \delta_a\widehat{f} = \widehat{f_a}.
```

- 旋转:  设 $`R`$ 是 $`n`$ 阶正交矩阵,

```math
\widehat{f(R\cdot)}(\xi)=\widehat f(R\xi).
```

$`(2)`$

1\. 若 $`f, f \cdot x_k \in L^1(\mathbb{R}^n)`$, 则

```math
\frac{\partial}{\partial \xi_k} \hat{f}(\xi) = \widehat{(-2\pi i x_k f)}(\xi).
```

特别, 若 $`f\in S`$,

```math
\partial^\alpha\hat{f}(\xi) = \widehat{\bigg((-2\pi i x)^\alpha f\bigg)}(\xi).
```

2\. 若 $`f`$ 及其弱导数 $`\partial f / \partial x_k \in L^1(\mathbb{R}^n)`$, 则

```math
\widehat{\frac{\partial f}{\partial x_k}}(\xi) = 2\pi i \xi_k \hat{f}(\xi).
```

特别, 若 $`f\in S`$,

```math
\widehat{\partial^\alpha f}(\xi) = (2\pi i \xi)^\alpha \hat{f}(\xi).
```

**$`(3)`$** 若 $`f, g \in L^1(\mathbb{R}^n)`$, 则

```math
\widehat{f * g} = \hat{f} \cdot \hat{g}.
```

**pf.** $`(2)`$

1\. 由LDCT知积分下求导公式成立:

```math
\frac{\partial}{\partial \xi_k} \int f(x) e^{-2\pi i \xi \cdot x} \, dx
= \int -2\pi i x_k f(x) e^{-2\pi i \xi \cdot x} \, dx.
```

具体证明如下: 若 $`f, f \cdot x_k \in L^1`$, 令 $`h e_k = (0, 0, \dots, h, 0, \dots, 0)`$, 则

```math
\frac{\hat{f}(\xi + h e_k) - \hat{f}(\xi)}{h}
= \int_{\mathbb{R}^n} \frac{e^{-2\pi i h e_k \cdot x} - 1}{h} \cdot f(x) \cdot e^{-2\pi i \xi \cdot x} \, dx.
```

由中值定理,

```math
\left| \frac{e^{-2\pi i h e_k  x} - 1}{h}  f(x) e^{-2\pi i \xi \cdot x} \right|
\le |f(x)| \left| e^{-2\pi i x_k (\theta h e_k)} \right| |-2\pi i x_k|= 2\pi |x_k f(x)| \in L^1,
```

且

```math
\frac{e^{-2\pi i h e_k \cdot x} - 1}{h} \xrightarrow{\text{a.e.}} -2\pi i x_k \quad \text{as } h \to 0.
```

所以

```math
\frac{\hat{f}(\xi + h e_k) - \hat{f}(\xi)}{h}
\to \int_{\mathbb{R}^n} -2\pi i x_k f(x) e^{-2\pi i \xi \cdot x} \, dx \quad \text{as } h \to 0.
```

2\. **证法1.** 若 $`f, \partial f / \partial x_k \in L^1(\mathbb{R}^n)`$, 断言

```math
\frac{\tau_{-h e_k} f - f}{h} \to \frac{\partial f}{\partial x_k} \quad \text{in } L^1 \text{ as } h \to 0.
```

事实上, 由 $`W_{loc}^{1, 1}`$ 函数的微积分基本定理,

```math
\frac{\tau_{-h e_k} f - f}{h} (x)= \int_0^1 \frac{\partial f}{\partial x_k}(x+the_k) \, dt,
```

于是, 由Fubini 定理和积分的平移连续性, 有

```math
\bigg\Vert\frac{\tau_{-h e_k} f - f}{h} - \frac{\partial f}{\partial x_k}\bigg\Vert_{L^1}
\leq \int_0^1 \Vert \tau_{-the_k}\partial_kf-\partial_kf \Vert_{L^1}\, dt\to 0, \quad\text{as }h\to0.
```

因为 Fourier 变换是强 $`(1, \infty)`$ 型, 所以

```math
\frac{e^{2\pi i h e_k \xi} \hat{f}(\xi) - \hat{f}(\xi)}{h}
```

关于 $`\xi`$ 一致收敛于 (特别, 逐点收敛)

```math
\widehat{\frac{\partial f}{\partial x_k} }(\xi), \quad \text{as } h \to 0.
```

而

```math
\lim_{h \to 0} \frac{e^{2\pi i h e_k \xi} - 1}{h} = 2\pi i \xi_k.
```

**证法2.**  断言 $`\lim_{t \to \infty} f(t, x_2, \dots, x_n) = 0`$. 事实上, 由微积分基本定理,

```math
f(x_1, x_2, \dots, x_n)
= f(0, x_2, \dots, x_n) + \int_0^{x_1} \frac{\partial f}{\partial x_1}(t, x_2, \dots, x_n) \, dt.
```

对 a.e. $`x_1 \in \mathbb{R}^1`$ 成立.  由于 $`\partial f / \partial x_1 \in L^1(\mathbb{R}^n)`$,

```math
\int_0^{x_1} \frac{\partial f}{\partial x_1}(t, \dots, x_n) \, dt
```

当 $`x_1 \to \infty`$ 时极限存在, 因此 $`\lim_{t \to \infty} f(t, x_2, \dots, x_n)`$ 存在, 又因为

```math
\int_{-\infty}^{\infty} |f(x_1, x_2, \dots, x_n)| \, dx_1 < \infty,
```

所以极限只能为 0. 于是

```math
\widehat{\frac{\partial f}{\partial x_1}}(\xi)
= \int_{\mathbb{R}^n} \frac{\partial f}{\partial x_1}(x) e^{-2\pi i x \cdot \xi} \, dx
```

```math
= \int_{\mathbb{R}^{n-1}} \left( \int_{-\infty}^{\infty} \frac{\partial f}{\partial x_1}(x) e^{-2\pi i x \xi} \, dx_1 \right) dx_2 \cdots dx_n
```

```math
★= \int_{\mathbb{R}^{n-1}} \left( -\int_{-\infty}^{\infty} f(x) \cdot (-2\pi i \xi_1) e^{-2\pi i x \xi} \, dx_1 \right) dx_2 \cdots dx_n
= 2\pi i \xi_1 \hat{f}(\xi).
```

★ 为什么成立? 或者说为什么有

```math
\int_{-R}^{R} \partial_{x_1} f(x) e^{-2\pi i x \xi} \, dx_1
= f(x)e^{-2\pi i x \xi}\bigg|^{x_1=R}_{x_1=R} - \int_{-R}^{R}  f(x) \partial_{x_1}e^{-2\pi i x \xi} \, dx_1.
```

这是因为 $`f(x)e^{-2\pi i x \xi}`$ 关于变量 $`x_1`$ 是绝对连续的.

**$`(3)`$** 由 Young 不等式知, 卷积是 $`L^1`$ 的, 利用 Fubini 定理

```math
\widehat{f * g}
= \int_{\mathbb{R}^n} \left( \int_{\mathbb{R}^n} f(y) g(x - y) \, dy \right) e^{-2\pi i \xi \cdot x} \, dx
```

```math
= \int_{\mathbb{R}^n} f(y) \left( \int_{\mathbb{R}^n} g(x - y) e^{-2\pi i \xi \cdot (x - y)} \, dx \right) e^{-2\pi i \xi \cdot y} \, dy
= \hat{f} \cdot \hat{g}
```

---

### Fourier 变换的不动点: Gauss 函数

**Prop)**

**$`(1)`$** $`\phi(x) = e^{-\pi x^2}, x \in \mathbb{R} \Rightarrow \hat{\phi}(\xi) = e^{-\pi \xi^2}`$

**$`(2)`$** $`\phi(x) = e^{-\pi|x|^2}, x \in \mathbb{R}^n \Rightarrow \hat{\phi}(\xi) = e^{-\pi|\xi|^2}`$

**$`(3)`$** $`\int_{\mathbb{R}^n} \phi_\varepsilon = 1`$, 其中 $`\phi_\varepsilon(x) := \varepsilon^{-n} \phi(x/\varepsilon)`$

**pf.** $`(1)`$ **证法1.**

```math
\hat{\phi}(\xi)
= \int_{-\infty}^{\infty} e^{-\pi x^2} e^{-2\pi i x \xi} \, dx
= e^{-\pi \xi^2} \int_{-\infty}^{\infty} e^{-\pi (x + i\xi)^2} \, dx
```

```math
= e^{-\pi \xi^2} \int_C e^{-\pi z^2} \, dz, \qquad C := \{ x + i\xi : x \in \mathbb{R} \}
```

```math
= e^{-\pi \xi^2} \int_{-\infty}^{\infty} e^{-\pi x^2} \, dx
= e^{-\pi \xi^2}.
```

第三个等号来源于 Cauchy 积分公式和围道积分的边界估计:

```math
\left| \int_{0 \le y \le \xi} e^{-\pi (R + iy)^2} \, d(R + iy) \right|
\le \xi \cdot e^{-\pi (R + i\xi)^2} \to 0 \quad \text{as } R \to \infty.
```

**证法2.**

```math
\frac{d}{d\xi} \hat{\phi}(\xi)
= \int_{\mathbb{R}} -2\pi i x e^{-\pi x^2} e^{-2\pi i x \xi} \, dx
= \int_{\mathbb{R}} i \left( e^{-\pi x^2} \right)' e^{-2\pi i x \xi} \, dx
```

即

```math
\frac{d}{d\xi} \hat{\phi} = \widehat{(-2\pi ix \phi)} = i \cdot \widehat{\frac{d}{dx} \phi}
= i \cdot 2\pi i \xi \, \hat{\phi}(\xi)
= -2\pi \xi \, \hat{\phi}(\xi)
```

解 ODE 得到 $`\hat{\phi}(\xi) = e^{-\pi \xi^2}`$.

$`(2)`$.  利用 $`(1)`$ 及 Fubini 定理.

**Crly) Gauss 核的 Fourier 变换**

**$`(1)`$** $`\widehat{\phi_\varepsilon}=\delta_\varepsilon\phi`$, 即 $`\hat{\phi}_\varepsilon(\xi) = \phi(\varepsilon \xi) = e^{-\pi |\varepsilon \xi|^2}`$

**$`(2)`$** $`\widehat{\delta_\varepsilon\phi}=\phi_\varepsilon`$, 即 $`\widehat{\phi(\varepsilon x)}(\xi)= \varepsilon^{-n} \hat{\phi}\left( \frac{\xi}{\varepsilon} \right)= \phi_\varepsilon(\xi)`$

**pf.** 伸缩性质结合 $`\hat{\phi}=\phi`$.

---

### 反演公式

**Prop)**

**$`(1)`$** 若 $`f, g \in L^1(\mathbb{R}^n)`$, 则

```math
\int_{\mathbb{R}^n} \hat{f} \, g = \int_{\mathbb{R}^n} f \, \hat{g}.
```

**$`(2)`$** 若 $`f, \hat{f} \in L^1(\mathbb{R}^n)`$, 则

```math
f(x) = \int_{\mathbb{R}^n} \hat{f}(\xi) e^{2\pi i x \cdot \xi} \, d\xi \quad \text{a.e. }x\in \mathbb{R}^n.
```

**$`(3)`$** 若 $`f \in L^1(\mathbb{R}^n)`$, 则 $`\hat{f} = 0 \text{ a.e.} \Rightarrow f = 0 \text{ a.e.}`$

**pf.** $`(1)`$ Fubini 定理.

**$`(2)`$** 令 $`\phi(x) = e^{-\pi|x|^2}`$, 考虑

```math
\int \hat{f}(x) e^{2\pi i x t} e^{-\pi |\varepsilon x|^2} \, dx
```

```math
= \int f(\lambda) \widehat{\bigg( e^{2\pi i x t} \phi(\varepsilon x) \bigg)}(\lambda) \, d\lambda
= \int f(x) \, \tau_t\widehat{\delta_\varepsilon\phi}\, dx
```

```math
= \int f(x) \, \tau_t\widehat{\phi_\varepsilon}\, dx
= f * \phi_\varepsilon (t).
```

由恒等逼近(几乎处处收敛)

```math
\int \hat{f}(x) e^{2\pi i x t} e^{-\pi |\varepsilon x|^2} \, dx
\to f(t), \quad \text{a.e. }t.
```

又由 LDCT,

```math
\int \hat{f}(x) e^{2\pi i x t} e^{-\pi |\varepsilon x|^2} \, dx
\to \int \hat{f}(x) e^{2\pi i x t}\, dx
```

```math
\Rightarrow f(t) = \int \hat{f}(x) e^{2\pi i x t} \, dx.
```

> Rmk: Gauss 核 $`\{\phi_\varepsilon\}`$, 也叫热核, 因为 $`\phi(x) = e^{-\pi|x|^2}`$,  $`\phi_{2\sqrt{\pi t}} (x)`$ 就是热方程的基本解. 它们虽然不紧支撑, 但和标准磨光子一样有很多好的磨光性质.

---

## Plancherel 定理

> Plancherel 定理告诉我们, Fourier 变换是 $`L^1 \cap L^2`$ 到 $`L^2`$ 的等距同构, 因此可以延拓为 $`L^2`$ 到 $`L^2`$ 的等距同构.

**Thm)** 若 $`f \in L^1(\mathbb{R}^n) \cap L^2(\mathbb{R}^n)`$, 则 $`\hat{f} \in L^2(\mathbb{R}^n)`$ 且 $`\|\hat{f}\|_{L^2} = \|f\|_{L^2}`$.

**pf.** 对 $`\forall a > 0`$, 令 $`h_a = \phi_{\sqrt{a/\pi}}`$ , 即

```math
h_a(y) = \left( \sqrt{\frac{\pi}{a}} \right)^n e^{-\frac{\pi^2 |y|^2}{a}}
```

于是 $`\widehat{h_a} \hat{f} \in L^1(\mathbb{R}^n)`$.

```math
\int \widehat{h_a} |\hat{f}|^2
= \int f(y) \int \overline{f(z)} \left( \int e^{2\pi i x (z - y)} \widehat{h_a}(x) \, dx \right) dz \, dy
```

```math
= \int f(y) \int \overline{f(z)} \, h_a(z - y) \, dz \, dy
```

```math
= \int F(y) h_a(y) \, dy, \qquad F(y) := \int f(y + z) \overline{f(z)} \, dz
```

由 Hölder 不等式及积分平移连续性, $`F`$ 在 $`\mathbb{R}^n`$ 一致连续, 特别在 0 连续. 换元, 再利用LDCT, 注意 $`F`$ 是有界的,

```math
\lim_{a \to 0} \int F(y) h_a(y) \, dy = F(0) = \|f\|_{L^2}^2.
```

(这实际上证明了 $`\delta`$ 分布的 Gauss 逼近)

注意到

```math
\widehat{h_a}(x) = \phi (\sqrt{\frac{a}{\pi}} \, x).
```

由 Fatou 引理,

```math
\int |\hat{f}|^2 \le \lim_{a \to 0} \int \widehat{h_a}(x) \,|\hat{f}(x)|^2 \, dx = \|f\|_{L^2}^2
```

```math
\Rightarrow \hat{f} \in L^2(\mathbb{R}^n) \quad \text{且} \quad \|\hat{f}\|_{L^2} \le \|f\|_{L^2}
```

由 LDCT,

```math
\lim_{a \to 0} \int \widehat{h_a} \,|\hat{f}|^2 = \|\hat{f}\|_{L^2}^2
```

```math
\Rightarrow \|\hat{f}\|_{L^2} = \|f\|_{L^2}.
```

---

## $`L^2`$ 上的 Fourier 变换(稠密延拓)

**将 $`L^1\cap L^2`$ 上的 Fourier 变换延拓为 $`L^2`$ 上的 Fourier 变换**

- 本质是有界线性算子的稠密延拓, 这里把具体延拓过程写出;

- $`C^\infty_c \subset L^1 \cap L^2`$, 于是 $`L^1(\mathbb{R}^n) \cap L^2(\mathbb{R}^n)`$ 在 $`L^2(\mathbb{R}^n)`$ 中稠密: $`\forall f \in L^2, \exists \{\varphi_k\} \subset L^1 \cap L^2`$, s.t. $`\|\varphi_k - f\|_{L^2} \to 0`$.

由 Plancherel 定理:

```math
\|\hat{\varphi}_k - \hat{\varphi}_{k+p}\|_{L^2} = \|\varphi_k - \varphi_{k+p}\|_{L^2}
```

又 $`L^2`$ 完备, 故 $`\exists g \in L^2`$, s.t.

```math
\|\hat{\varphi}_k - g\|_{L^2} \to 0
```

**定义**

```math
\hat{f} := g
```

**well-defined: **  如果还有 $`\{\psi_k\} \subset L^1 \cap L^2, \|\hat{\psi}_k - g_2\|_{L^2} \to 0`$, 则

```math
\|\hat{\varphi}_k - \hat{\psi}_k\|_{L^2} = \|\varphi_k - \psi_k\|_{L^2}
\Rightarrow \|g - g_2\|_{L^2} = 0 \Rightarrow g_2 \stackrel{\text{a.e.}}{=} g
```

> Rmk: 若 $`f \in L^1 \cap L^2`$, 则 $`f`$ 作为 $`L^1, L^2`$ 的 Fourier 变换一致.

下面命题的是有界线性算子延拓的结果, 说明 $`\wedge`$ 为 $`L^2(\mathbb{R}^n)`$ 上的等距线性映射.

**Prop)** 设 $`f, g \in L^2(\mathbb{R}^n)`$, 则

**$`(1)`$** 能量不损失:

```math
\|f\|_{L^2} = \|\hat{f}\|_{L^2}
```

**$`(2)`$** 在 $`L^2`$ 范数意义下: (第二个等式的证明要用到反演公式)

```math
\hat{f}(\xi) = \lim_{N \to \infty} \int_{|x| < N} f(x)e^{-2\pi i x \xi} \, dx
```

```math
f(x) = \lim_{N \to \infty} \int_{|\xi| < N} \hat{f}(\xi) e^{2\pi i x \xi} \, d\xi
```

这给出了一个具体的逼近.

**$`(3)`$** Parseval 等式:

```math
\int_{\mathbb{R}^n} f \bar{g} = \int_{\mathbb{R}^n} \hat{f} \overline{\hat{g}}, \qquad \text{i.e. } \langle f, g \rangle = \langle \hat{f}, \hat{g} \rangle
```

**pf.** **$`(1)`$**

```math
\|f\|_{L^2} = \lim \|\varphi_k\|_{L^2} = \lim \|\hat{\varphi}_k\|_{L^2} = \|\hat{f}\|_{L^2}, \qquad \varphi_k \in L^1 \cap L^2
```

**$`(2)`$** 令

```math
f_N := f \cdot \chi_{B(0, N)} \Rightarrow f_N \in L^1 \cap L^2
```

且

```math
\|f - f_N\|_{L^2} \to 0
```

由 $`(1)`$

```math
\Rightarrow \|\hat{f} - \hat{f}_N\|_{L^2} \to 0, \qquad \hat{f}_N(\xi) = \int_{B(0, N)} f(x) e^{-2\pi i x \xi} \, dx
```

由于 $`\hat{f} \in L^2`$, 有

```math
\hat{\hat{f}}(x) = \lim_{N \to \infty} \int_{B(0, N)} \hat{f}(\xi) e^{-2\pi i x \xi} \, d\xi \quad \text{in } L^2
```

```math
\hat{\hat{f}}(-x) = \lim_{N \to \infty} \int_{B(0, N)} \hat{f}(\xi) e^{2\pi i x \xi} \, d\xi
```

由反演公式,

```math
f=\mathcal F^{-1}(\mathcal Ff) =R\mathcal F(\mathcal Ff) =R\mathcal F^2f.
```

**$`(3)`$** 内积可由范数表达:

```math
\langle f, g \rangle_{L^2, L^2}
= \frac{1}{2} \left\{ \|f + g\|_2^2 + i\|f + ig\|_2^2 - (1 + i)\|f\|_2^2 - (1 + i)\|g\|_2^2 \right\}
```

因为 Fourier 变换是线性的, 所以

```math
\langle \hat{f}, \hat{g} \rangle_{L^2, L^2} = \langle f, g \rangle_{L^2, L^2}
```

---

### $`L^2`$ 上的反演公式及 Fourier 逆变换

设 $`f \in L^2(\mathbb{R}^n)`$, 令

```math
\check{f}(x) = \hat{f}(-x)
```

则 $`\vee`$ 是 $`\wedge`$ 的逆映射, 即

```math
(\hat{f})^\vee = f, \quad (\check{f})^\wedge = f
```

**pf.** 只证明第一个等式, 第二个用同样的方法可以证明.

① 当 $`\hat{f} \in L^1 \cap L^2`$ 时: 对 $`\forall g \in L^1 \cap L^2`$(test function), 因为 $`\hat{f}, g`$ 都是 $`L^1`$ 的, 可以使用 Fubini 定理,

```math
\int_{\mathbb{R}^n} \check{\hat{f}} \, \bar{g}
= \int_{\mathbb{R}^n} \hat{\hat{f}}(-x) \overline{g(x)} \, dx
```

```math
= \int_{\mathbb{R}^n} \left( \int_{\mathbb{R}^n} \hat{f}(t) e^{-2\pi i (-x) t} \, dt \right) \overline{g(x)} \, dx
```

```math
= \int_{\mathbb{R}^n} \overline{\hat{g}} \, \hat{f}
= \int_{\mathbb{R}^n} f \, \bar{g}
```

对 $`\forall g \in L^2`$, 取 $`\{g_k\} \subset L^1 \cap L^2, \|g_k - g\|_{L^2} \to 0`$,  则

```math
\int_{\mathbb{R}^n} \check{\hat{f}} \, \bar{g}
= \lim_{k \to \infty} \int_{\mathbb{R}^n} \check{\hat{f}} \, \overline{g_k}
= \lim_{k \to \infty} \int_{\mathbb{R}^n} f \, \overline{g_k}
= \int_{\mathbb{R}^n} f \, \bar{g}
```

```math
\Rightarrow \int_{\mathbb{R}^n} (\check{\hat{f}} - f) \, \bar{g} = 0
```

取 $`g = \check{\hat{f}} - f \in L^2`$, 得

```math
\check{\hat{f}} \stackrel{\text{a.e.}}{=} f
```

② 一般地, 当 $`\hat{f} \in L^2`$ 时:  取 $`\{f_k\} \subset L^2`$ (可以取速降函数), s.t. $`\hat{f}_k \in L^1 \cap L^2`$, 且 $`\|\hat{f}_k - \hat{f}\|_{L^2} \to 0`$

```math
\implies \check{\hat{f}} = \lim \check{\hat{f}}_k = \lim f_k = f \quad \text{in } L^2
```

> $`\wedge`$ 为 $`L^2(\mathbb{R}^n)`$ 到 $`L^2(\mathbb{R}^n)`$ 的等距同构, 是酉算子(保内积的线性满射算子 cf."108"P212).

---

## $`L^p(\mathbb{R}^n)`$ 上的 Fourier 变换$`(1 < p < 2)`$

对 $`1 < p < 2, f \in L^p(\mathbb{R}^n)`$,  $`L^p \subset WL^p \subset L^1 + L^2`$ (cf. GTM249 Ex1.1.10). 事实上, 令

```math
f_1 := f(x) \chi_{\{|f| \ge 1\}}, \qquad f_2 := f(x) \chi_{\{|f| < 1\}}, \qquad f = f_1 + f_2
```

则

```math
\int |f_1| \le \int_{\{|f| \ge 1\}} |f|^p < \infty, \qquad
\int |f_2|^2 = \int_{\{|f| < 1\}} |f|^2 \le \int_{\{|f| < 1\}} |f|^p < \infty
```

**Def) $`L^1 + L^2`$ 上的 Fourier 变换**.

$`\forall f \in L^1(\mathbb{R}^n) + L^2(\mathbb{R}^n), f=f_1+f_2`$,

```math
\hat{f} := \hat{f}_1 + \hat{f}_2
```

于是, 可以定义 $`L^p(\mathbb{R}^n)`$ 上的 Fourier 变换$`(1 < p < 2)`$.

> Rmk: 像定义 $`L^2`$ 上的 Fourier 变换那样, 同样可以用 $`L^1 \cap L^p`$ 函数逼近来定义, 它们都是一致的定义. 关于定义的一致性, 后面会证明这些逼近的定义都等价于速降函数逼近的定义, 也等价于缓增分布的 Fourier 变换的定义.

**well-defined: ** 设 $`f \in L^p(1 < p < 2), f = f_1 + f_2 = g_1 + g_2`$, 则

```math
\hat{f}_1 + \hat{f}_2 = \hat{g}_1 + \hat{g}_2
```

事实上

```math
f_1 - g_1 = g_2 - f_2 \in L^1 \cap L^2
\implies \hat{f}_1 - \hat{g}_1 = \hat{g}_2 - \hat{f}_2
```

---

### 卷积的 Fourier 变换

**Thm)** 设 $`f \in L^1, g \in L^p(1 \le p \le 2)`$, 则

```math
\widehat{f * g}(x) = \hat{f}(x) \, \hat{g}(x), \qquad \text{a.e. } x \in \mathbb{R}^n
```

**pf.** $`p=1`$ 已经证明, $`p=2`$ 利用逼近容易证明. 下面设 $`1<p<2`$. 由 Young 不等式 $`f*g \in L^p`$. 设 $`g = g_1 + g_2, g_1 \in L^1, g_2 \in L^2`$, 则

```math
\hat{h} = \widehat{(f * g_1 + f * g_2)}
= \hat{f} \, \hat{g}_1 + \hat{f} \, \hat{g}_2
= \hat{f} \, \hat{g}
```

**Hausdorff-Young 不等式.** $`\forall f \in L^p(\mathbb{R}^n) (1 \le p \le 2)`$,

```math
\|\hat{f}\|_{L^{p'}} \le \|f\|_{L^p}
```

**证明** 已知

```math
\|\hat{f}\|_{L^\infty} \le \|f\|_{L^1}, \qquad \|\hat{f}\|_{L^2} = \|f\|_{L^2}
```

Riesz-Thorin 插值定理 $`\Rightarrow`$ 对 $`\forall p \in (1, 2)`$:

```math
\begin{cases}
\dfrac{1}{p} = \dfrac{1 - t}{1} + \dfrac{t}{2} \\[8pt]
\dfrac{1}{q} = \dfrac{1 - t}{\infty} + \dfrac{t}{2}
\end{cases}
```

```math
\Rightarrow \frac{1}{q} = \frac{t}{2} = 1 - \frac{1}{p} \Rightarrow q = p' \Rightarrow \|\hat{f}\|_{L^{p'}} \le \|f\|_{L^p}
```

我们给出如下推广的卷积 Fourier 变换公式:

**Thm)** 设 $`f \in L^p(\mathbb{R}^n), g \in L^q(\mathbb{R}^n), 1 + \frac{1}{r} = \frac{1}{p} + \frac{1}{q}, 1 \le p, q, r \le 2`$, 则

```math
\widehat{f * g}(x) = \hat{f}(x) \, \hat{g}(x)
```

**pf.** 由 Young 不等式, $`f*g \in L^r`$, 故 $`\widehat{f*g}`$ 有意义. 由 Hausdorff-Young 不等式,

```math
\hat{f} \in L^{p'}, \qquad \hat{g} \in L^{q'}
```

由 Hölder 不等式, $`\hat{f} \hat{g} \in L^{r'}`$:

```math
\frac{1}{r'} = \frac{1}{p'} + \frac{1}{q'}
```

令 $`h := f*g \in L^r`$, 由 Hausdorff-Young, $`\hat{h} \in L^{r'}`$.

先假设 $`f \in L^1 \cap L^p, g \in L^1 \cap L^q`$, 则有

```math
\widehat{f * g} = \hat{f} \, \hat{g}
```

对一般的 $`f \in L^p, g \in L^q`$, 由逼近过程可得: 取 $`\{f_n\} \subset L^1 \cap L^p, \{g_n\} \subset L^1 \cap L^q`$ 使得

```math
f_n \to f \text{ in } L^p, \qquad g_n \to g \text{ in } L^q
```

则

```math
\hat{f_n} \to \hat{f} \text{ in } L^{p'}, \qquad \hat{g_n} \to \hat{g} \text{ in } L^{q'}
```

由 Holder 不等式,

```math
\widehat{f_n * g_n}-\widehat{f * g} = \hat{f}_n(\hat{g}_n - \hat{g}) + \hat{g}(\hat{f}_n - \hat{f})\to 0 \text{ in } \ L^{r'}.
```

所以, 对 a.e. x 有

```math
\widehat{f * g} = \lim \widehat{f_n * g_n} = \lim \hat{f}_n \cdot \hat{g}_n = \hat{f} \cdot \hat{g}
```

---

## $`|x|^{\alpha-n}`$ 的 Fourier 变换

设 $`f \in C_c^\infty(\mathbb{R}^n), 0 < \alpha < n`$, 则

```math
C_\alpha \left( |\cdot|^{- \alpha} \hat{f}(\cdot) \right)^\vee(x)
= C_{n - \alpha} \int_{\mathbb{R}^n} |x - y|^{\alpha - n} f(y) \, dy
```

其中

```math
C_\alpha := \frac{\Gamma(\alpha/2)}{\pi^{n/2}}
```

cf. "Analysis"P180.

---

## $`S`$ 上 Fourier 变换

> 大部分教材先讨论 $`S`$ 上 Fourier 变换, 它有着最丰富的性质. 然后自然的延拓为 $`L^2`$ 上的酉算子. 它是强 $`(1, \infty)`$ 有界的, 所以可以延拓到 $`L^1`$ 上, 再由插值定理建立 Hausdorff-Young 不等式, 进而可以延拓到 $`L^p(1\leq p\leq 2)`$ 上. 对于 $`L^p(2< p\leq\infty)`$ 函数, 多项式函数(缓增分布的常义函数)的 Fourier 变换, 都归结于缓增分布的 Fourier 变换.

本节有两个任务, 一个是叙述 $`S`$ 上 Fourier 变换的良好性质, 另一个则是证明 $`L^p(1\leq p\leq 2)`$ 函数的两种 Fourier 变换的一致性.

**Prop)**  $`\wedge`$: $`S \to S`$ 是线性的双射, 其逆变换为

```math
\vee: S \to S, \qquad u \mapsto \int_{\mathbb{R}^n} u(x) e^{2\pi i x \xi} \, dx
```

且是序列连续的(S 是拓扑线性空间), 此外还满足

```math
\langle u, v\rangle_{L^2, L^2}=\langle \hat{u}, \hat{v} \rangle_{L^2, L^2}\quad\forall u, v\in S.
```

---

### $`L^q(1 \le q \le \infty)`$ 到 $`S'`$ 的嵌入

我们知道 $`S \subset L^p(1 \le p \le \infty)`$, 下面说明:

```math
L^q (1 \le q \le \infty) \hookrightarrow S'
```

良定性: 定义 $`L^q \to S'`$ 映射:

```math
f \mapsto T_f, \qquad T_f(\phi) = \int f(x) \phi(x) \, dx, \quad \forall \phi \in S
```

设 $`\varphi_n \to 0`$ in $`S`$, 往证 $`T_f(\varphi_n) \to 0`$.

① $`q = 1`$:

```math
|T_f(\phi_n)| \le \|f\|_{L^1} \sup_{x \in \mathbb{R}^n} |\phi_n(x)| \to 0
```

② $`1 < q \leq \infty`$:

```math
|T_f(\phi_n)| \le \|f\|_q \|\phi_n\|_{q'}
```

取 $`t \in \mathbb{N}`$ 满足 $`tq' > N`$, 则

```math
|\phi_n(x)| \le \sup \left| (1 + |x|)^t \phi_n(x) \right| \left( \frac{1}{1 + |x|} \right)^t
```

```math
\|\phi_n\|_{q'}
\le \sup \left| (1 + |x|)^t \phi_n(x) \right|
\left( \int \left( \frac{1}{1 + |x|} \right)^{tq'} dx \right)^{\frac{1}{q'}}
\to 0
```

单射性: $`\forall f, g \in L^q`$, 则 $`f, g \in L^1_{\mathrm{loc}}`$, 由变分学基本引理:

```math
T_f = T_g \Rightarrow f = g
```

(这是 $`L^1_{loc}`$ 函数特有的, $`S' \hookrightarrow D'`$ 单射只能用稠性)

- 对 $`1 < q \le \infty`$ 的泛函证法: 若

```math
\int (f(x) - g(x)) \phi(x) \, dx = 0, \qquad \forall \phi \in S
```

由 $`S`$ 在 $`L^{q'}`$ 中稠密,

```math
\int (f - g) \phi = 0, \qquad \forall \phi \in L^{q'}
```

即 $`f - g`$ 是 $`L^{q'}`$ 上的零泛函. 由 Riesz 表示定理的等距性,

```math
f - g = 0 \quad \text{in } L^q
```

---

### 拓扑线性空间的对偶嵌入

**Prop)** 设 $`X, Y`$ 为线性向量空间, $`X \to Y`$(连续, 稠密), 即存在

```math
i: X \to Y
```

线性连续且 $`i(X)`$ 在 $`Y`$ 中稠密, 则限制泛函是 $`Y^*`$ 到 $`X^*`$ 的嵌入(单射), 这里的限制泛函等于 $`i^T`$.

**pf.** 良定:  $`i`$ 连续 $`\Rightarrow y^* \circ i`$ 连续线性, 即

```math
y^* \mapsto y^* \circ i, \qquad y^* \circ i \in X^*
```

单射:  若 $`y_1^*, y_2^* \in Y^*`$ 且 $`y_1^* \circ i = y_2^* \circ i`$. $`\forall y \in Y, \exists \{x_n\} \subset X`$, s.t. $`i(x_n) \to y`$, 则

```math
y_1^*(y) = \lim y_1^* \circ i(x_n)
= \lim y_2^* \circ i(x_n)
= y_2^*(y)
```

```math
\Rightarrow y_1^* = y_2^*
```

**应用**

**$`1`$.** $`C_c^\infty \subset S \subset C^\infty`$, 每个包含中恒等嵌入是连续的(拓扑的强弱), 且依次稠密

```math
\Rightarrow \mathcal{E}' \hookrightarrow \mathcal{S}' \hookrightarrow \mathcal{D}'
```

**$`2`$.** $`S \subset L^p(1 \le p < \infty)`$, 恒等嵌入连续, 且 $`S`$ 在 $`L^p`$ 中稠密

```math
\Rightarrow L^{p'} \hookrightarrow S'
```

这直接得到了 $`L^q \hookrightarrow S'`$ 的 $`1 \le q < \infty`$ 情形.

**$`3`$.** 命题中的稠密性不可去:

① $`X = \{\theta\}`$, $`Y`$ 非平凡, 则 $`X^*`$ = {零泛函};

② $`X = \{ x \in \mathbb{R}^2 : (x, 0) \}, Y = \mathbb{R}^2`$, 则 $`X^* \cong \mathbb{R}, \quad Y^* \cong \mathbb{R}^2`$

---

### 两种定义在 $`L^p(1 \le p \le 2)`$ 上的一致性

- 稠密延拓: $`\Lambda_1`$:  $`L^p \to L^{p'}`$,

```math
f \mapsto \hat{f}^1 = L^{p'}\text{-}\lim \hat{f}_n, \text{ 其中 } f_n \to f \text{ in } L^p, \ f_n \in S
```

- 缓增分布的 Fourier 变换: $`\Lambda_2`$: $`L^p \to L^{p'}`$,

```math
f \mapsto \hat{f}^2 \quad \langle \hat{f}^2, \varphi \rangle := \langle f, \hat{\varphi} \rangle
```

> 两种定义在 $`p=1, 2`$ 时一致, 由 Riezs 插值定理, 它们都是 $`L^p(1 \le p \le 2)\to L^{p'}`$ 的有界线性算子, 并且在稠子集 $`S`$ 上一致, 所以在 $`L^p(1 \le p \le 2)`$ 一致. 下面直接证明.

**pf.** 对 $`\varphi \in S`$:

```math
\langle \hat{f}^1, \varphi \rangle = \int \hat{f}^1(x) \varphi(x) \, dx
```

```math
= \lim_{n \to \infty} \int \hat{f}_n(x) \varphi(x) \, dx
= \lim_{n \to \infty} \int \varphi(x) \int f_n(s) e^{-2\pi i s x} \, ds \, dx
```

($`\varphi \in L^1, f_n \in L^1`$, 可换序)

```math
= \lim_{n \to \infty} \int f_n(s) \, \hat{\varphi}(s) \, ds
= \int f(s) \, \hat{\varphi}(s) \, ds
= \langle f, \hat{\varphi} \rangle
```

```math
\Rightarrow \hat{f}^1 \stackrel{\text{a.e.}}{=} \hat{f}^2
```

---
