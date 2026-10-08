> 主要定义过程参考 Lieb and Loss 的"Analysis".

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

## R-L 引理的推论

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

## Fourier 变换的基本性质

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
\widehat{\delta_a f}(\xi) = a^{-n} \hat{f}\left( \frac{\xi}{a} \right).
```

$`(2)`$

1\. 若 $`f, f \cdot x_k \in L^1(\mathbb{R}^n)`$, 则

```math
\frac{\partial}{\partial \xi_k} \hat{f}(\xi) = \widehat{(-2\pi i x_k f)}(\xi).
```

2\. 若 $`f`$ 及其弱导数 $`\partial f / \partial x_k \in L^1(\mathbb{R}^n)`$, 则

```math
\widehat{\frac{\partial f}{\partial x_k}}(\xi) = 2\pi i \xi_k \hat{f}(\xi).
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

## Fourier 变换的不动点: Gauss 函数

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

**pf.** 由伸缩性质:

```math
\widehat{f(ax)}(\xi) = a^{-n} \hat{f}\left( \frac{\xi}{a} \right), \qquad a > 0.
```

则

```math
\widehat{\varepsilon^{-n} \phi\left( \frac{\xi}{\varepsilon} \right)}
= \varepsilon^{-n} \cdot \varepsilon^n \hat{\phi}(\varepsilon \xi)
= \hat{\phi}(\varepsilon \xi).
```

---

## 反演公式

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

> Notice: Gauss 核 $`\{\phi_\varepsilon\}`$, 也叫热核, 因为 $`\phi(x) = e^{-\pi|x|^2}`$,  $`\phi_{2\sqrt{\pi t}} (x)`$ 就是热方程的基本解. 它们虽然不紧支撑, 但和标准磨光子一样有很多好的磨光性质.

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
