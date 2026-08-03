This is notes on _Stochastic calculus_.

### 2. Preliminaries

#### 2.1 Finite variation integrals

**Definition** A function $a:[0,\infty)\to\mathbb R$ is said to be **càdlàg** if it's right-cts and has left limits. 

<font color='red'>Define integral against nondecreasing càdlàg functions</font>

_Property_ If $a$ is nondecreasing and càdlàg with $a(0)=0$, then there exists a unique Borel measure $da$ on $[0,\infty)$ s.t. $da((s,t])=a(t)-a(s)\forall s<t$.

For $f$ measurable and integrable,one can define **Lebesgue-Stieltjes** integral $f\cdot a$ by $(f\cdot a)(t)=\int_{(0,t]}f(s)da(s)$.

_Property_ $f\cdot a$ is right-cts. When $a$ is cts, $f\cdot a$ is cts. In this case, one can denote $\int_{(0,t]} f(s)da(s)=\int_0^t f(s)da(s)$.

<font color='red'>Define integral against finite variation functions</font>

**Definition** Let $a:[0,\infty)\to\mathbb R$ be a càdlàg function. For any $n\in \mathbb N$ and $t\ge 0$, let $v^n(t)=\sum_{k=0}^{\lceil 2^n t\rceil -1}|a((k+1)2^{-n}-a(k2^{-n}))|$. $v(t)=\lim_{n \to \infty} v^n(t)$ exists for all $t$ and is called **total variation** of 4a$ on $[0,t]$. If $v(t)<\infty$, $a$ is said to have **finite variation on $(0,t]$**. If $v(t)<\infty\forall t$, $a$ is said to have **finite variation**.

**Lemma 2.2** Let $a:[0,\infty)\to\mathbb R$ be a càdlàg function of finite variation. Then $v$ is also càdlàg with $\Delta v(t)=|\Delta a(t)|$ ($\Delta a(x)=a(x)-a(x^-)$), and non-decreasing in $t$. In particular, if $a$ ia cts, so is $v$.

**Proposition 2.3**  Let $a:[0,\infty)\to\mathbb R$ be a càdlàg function. $a$ is the difference of two right-cts and nondecreasing functions, i.e.,  $a=a^+-a^-$ iff $a$ is of finite variation. 

For $f$ measurable and integrable, one can define **Lebesgue-Stieltjes** integral $f\cdot a$ by $(f\cdot a)(t)=\int_{(0,t]}f(s)da^+(s)-\int_{(0,t]}f(s)da^-(s)$.

<font color='red'>Define integral against random finite variation functions</font>

#### 2.2 Random integrator

**Definition 2.4** Given a càdlàg adapted process $A$ (i.e., $A(\omega,t)$ is càdlàg for all $\omega\in\Omega$), its **total variation process** $V$ is defined pathwise by letting $V(\omega,\cdot)$ be the total variation of $A(\omega,\cdot)$ for all $\omega\in \Omega$. $A$ is of **finite variation** if $A(\omega,t)$ is for all $\omega\in\Omega$.

