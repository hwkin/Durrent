## Chapter 2 Laws of Large Numbers

### 2.1 Independence

***Definition*** (i)Two events $A$ and $B$ are **independent** if $P(AB)=P(A)P(B)$; (ii)two random variables $X$ and $Y$ are **independent** if for all $C,D\in\mathcal R$, $P(X\in C,Y\in D)=P(X\in C)P(Y\in D)$; (iii)two $\sigma$-field $\mathcal F,\mathcal G$ are **independent** if any two events respectively are independent. 

(i) is a special case of (ii) and (ii) is a special case of (iii).

**Theorem 2.1.1** (i) If X and Y are independent, so are $\sigma(X),\sigma(Y)$ (ii) if $\mathcal F,\mathcal G$ are independent, so is $X\in\mathcal F$,$Y\in\mathcal G$.

**Theorem 2.1.2** (i) If $A$ and $B$ are independent then so are $A^c$ and $B$, $A$ and $B^c$, $A^c$ and $B^c$. (ii) conversely, $A$ and $B$ are independent iff $1_A$ and $1_B$ are independent.

Now we generalize to "several things to be independent". We begin by reducing to the case of finite many objects and an infinite collection of objects is aaid to be independent if every finite subcollection is.

***Definition*** (i) $\sigma$-fields $\mathcal F_1,...,\mathcal F_n$ are **independent** if whenever $A_i\in \mathcal F_i$ we have $P(\cap A_i)=\prod P(A_i)$; (ii) r.v. $X_1,...,X_N$ are **independent** if whenever $B_i\in\mathcal R$ we have $P(\cap\{X_i\in B_i\})=\prod P(X_i\in B_i)$; (iii) sets $A_1,...,A_n$ are independent if for any $I\subset\{1,..,n\}$, $P(\cap_{i\in I} A_i)=\prod_{i\in I} P(A_i)$. Notice we need the equality hold for all subcollection. As for former 2 definition, taking $\Omega$ or $R$ can cancel some items.

**Theorem 2.1.3** Let $A_1,...,A_n$ be independent. (i) $A_1^c,A_2,...,A_n$ are independent (ii) $1_{A_1},...,1_{A_n}$ are independent.

_Remark_ If the events $A_1,...,A_n$ only satisfy that for all $i\neq j$, $P(A_iA_j)=P(A_i)P(A_j)$, they are called **pairwise independent**. Independent random variables are pairwise independent, but not vise versa.

**Example 2.1.4** Let $X_1$, $X_2$, $X_3$ i.i.d.$\sim B(0,1/2)$, let $A_1=\{X_2=X_3\},A_2=\{X_1=X_3\},A_3=\{X_1=X_2\}$. They are pairwise independent but not independent.

However, to check r.v. to be independent, we have to check every Borel sets. Now we consider the sufficient conditions for independence.

#### 2.1.1 Sufficient Conditions for Independence

***Definition*** Collections of sets$\mathcal A_1,...,\mathcal A_n\subset\mathcal F$ are said to be independent if whenever $A_i\in\mathcal A_i$ and $I\subset\{1,...,n\}$, we have $P(\cap_{i\in I} A_i)=\prod_{i\in I}P(A_i)$.

**Lemma 2.1.5** WLOG we can suppose each $A_i$ contains $\Omega$, then in the definition $I=\{1,...,n\}$ is enough.

We rely on an important theorem:

> ***Definition*** We say that $\mathcal A$ is a $\pi$-system if it is closed under intersection, say that $\mathcal L$ is a $\lambda$-system if: (i) $\Omega\in\mathcal L$ . (ii) If $A,B \in \mathcal  L$ and $A\subset B$ then $B-A\in\mathcal L$(iii) If $A_n\in\mathcal L$ and $A_n\uparrow A$ then $A\in \mathcal L$.
>
> Theorem 2.1.6 $\pi-\lambda$ theorem. If $\mathcal P$ is a $\pi$-system and $\mathcal L$ is a $\lambda$-system that contains $\mathcal P$, then it contains $\sigma(\mathcal P)$.

**Theorem 2.1.7** Suppose $\mathcal A_1,...,\mathcal A_n$ are independent and each $\mathcal A_i$ is a $\pi$-system, then $\sigma(\mathcal A_1),...,\sigma(\mathcal A_n)$ are independent.

<font color='red'>_proof of Theorem 2.1.7_</font>  The strategy is to find suitable $\lambda$-system and expand $\mathcal A_i$ to $\sigma(\mathcal A_i)$.

Let $A_2,...,A_n$ be sets with $A_i\in\mathcal A_i$, and consider $\mathcal L:=\{A: P(A\cap F)=P(A)P(F), F=\cap_{i=2}^n A_i\}$. Verify this is a $\lambda$-system which contains $\mathcal A_1$, so $\sigma(\mathcal A_1)\in\mathcal L$, i.e., $\sigma(\mathcal A_1),\mathcal A_2,...,\mathcal A_n$ are independent. Continue this process.

_Remark_ it's not easy to show that $\mathcal L$ is closed under intersection or union, but it's easy to verify properties of a $\lambda$-system.

This result indicates that we need only to verify on less sets for independence.

**Theorem 2.1.8** In order for $X_1,...,X_n$ to be independent, it's sufficient to show for all $x_1,...,x_n\in(-\infty,\infty]$, $P(X_1\leq x_1,...,X_n\leq x_n)=\prod P(X_i\leq x_i)$.

Now we consider the function of independent r.v.

**Theorem 2.1.9** Suppose $\mathcal F_{i,j},1\leq i\leq n, 1\leq j\leq m(i)$ are independent and let $\mathcal G_i=\sigma(\cup_j\mathcal F_{i,j}).$ Then $\mathcal G_1,...,\mathcal G_n$ are independent. 

<font color='red'>_proof of Theorem 2.1.9_</font> The strategy is just as in **Theorem 2.1.7**.

**Theorem 2.1.10** If for $1\leq i\leq n,1\leq j\leq m(i)$, $X_{i,j}$ are independent and $f_i$ are measurable then $f_i(X_{i,1},...,X_{i,m(i)})$ are independent.

#### 2.1.2 Independence, Distribution and Expectation

Our next goal is to obtain formulas for the distribution and expectation of independent random variables.

**Theorem 2.1.11** Suppose $X_1, . . . , X_n$ are independent random variables and $X_i$ has distribution $\mu_i$, then $(X_1, . . . , X_n)$ has distribution $\mu_1\times\cdots\mu_n$.

**Theorem 2.1.12.** Suppose $X$ and $Y$ are independent and have distributions $\mu$ and $\nu$. If $h$ is a measurable function which is nonnegative or integrable (*ensure Fubini's theorem can be used*), then $Eh(X,Y)=\iint h(x,y)\mu(dx)\nu(dy)$. In particular, if $h(x,y)=f(x)g(y)$ where $f$ and $g$ are measurable and nonnegative/integrable, then $Ef(X)g(Y)=Ef(X)Eg(Y)$. 

**Theorem 2.1.13** If $X_1,...,X_n$ are independent and are nonnegative/integrable, then $E\prod_{i=1}^n X_i=\prod_{i=1}^n EX_i$.

_Remark_ The inverse is not true. In the case $X$ and $Y$ are square integrable and satisfy $EXY=EXEY$, $X$ and $Y$ are called **uncorrelated**. $EXY<\infty$ by Cauchy-Schwarz.

#### 2.1.3 Sums of Independent Random Variables

**Theorem 2.1.15** If $X$ and $Y$ are independent with distribution functions $F$ and $G$, then $P(X+Y\leq z)=\int F(z-y)dG(y)$. The integral is called **convolution** of $F$ and $G$ and is denoted by $F*G$.

**Theorem 2.1.16** If $X$ has density $f$ and $Y$ has distribution function $G$ and they are independent, then $X+Y$ has density $h9x)=\int f(x-y)dG(y)$. If $Y$ has density function $g$. the formular can be written as $h(x)=\int f(x-y)g(y)dy$.

Some application is to prove "additionality" of parameterized distributions.

**Example 2.1.17** The **gamma density** with parameters $\alpha$ and $\lambda$ is given by 
$$
f(x) =
\begin{cases}
\lambda^\alpha x^{\alpha - 1} e^{-\lambda x} / \Gamma(\alpha) & \text{for } x \ge 0 \\
0 & \text{for } x < 0
\end{cases}
$$
**Theorem 2.1.18** If $X\sim gamma(\alpha,\lambda)$ and $Y\sim gamma(\beta,\lambda)$ and they are independent, then $X+Y\sim (\alpha+\beta,\lambda)$. Consequently if $X_1,...,X_n\sim Exp(\lambda)$ are i.i.d., then $X_1+...+X_n\sim gamma(n,\lambda)$.

**Theorem 2.1.20** If $X\sim \mathcal N(\mu,a)$ and $Y\sim\mathcal N(\nu,b)$ are independent, then $X+Y\sim\mathcal N(\mu+\nu,a+b)$.

#### 2.1.4 Construct Independent Random Variables

We now address the existence of independent r.v.

Finite case: If we are given a finite number of distribution function $F_i$, then we can construct independent $X_1,...,X_n$ with corresponding distributional function:

Let $\Omega=\mathbf R^n$ and $\mathcal F=\mathcal R^n$, $X_i(\omega_1,...,\omega_n)=\omega_i$, and let P be the measure that has $P((a_1,b_1]\times\cdots\times(a_n,b_n])=\prod_{i=1}^n (F_i(b_i)-F_i(a_i))$. if $\mu_i$ is the measure with distribution function $F_i$ then $P=\mu_1\times\cdots\times\mu_n$.

For the cases of $\mathbf R^{\mathbf N }$ and $\mathcal R^{\mathbf N}$, we have

**Theorem 2.1.21 Kolmogorov's extension theorem** Suppose we are given probability measures $\mu_n$ on $(\mathbf R^n,\mathcal R^n)$ that are consistent, i.e.,$\mu_{n+1}((a_1,b_1]\times \cdots \times (a_n,b_n]\times \mathbf{R})
= \mu_n((a_1,b_1]\times \cdots \times (a_n,b_n])$ , then there is a unique probability measure $P$ on $(\mathbf R^\mathbf N,\mathcal R^\mathbf N)$ with $P\left( \omega : \omega_i \in (a_i, b_i], 1 \leq i \leq n \right) = \mu_n\left( (a_1, b_1] \times \cdots \times (a_n, b_n] \right)$.

Now we construct sequences of random variables that take values in other measurable spaces. However, **Theorem 2.1.21** is not valid for arbitrary space. Now we consider a class of space where the theorem can be generalized.

***Definition*** $(S,\mathcal S)$ is said to be **nice** if there is a bijection with itself and inverse measurable from $S$ to $\mathbf R$. Such spaces are called **standard Borel spaces**.

**Theorem 2.1.22** If $S$ is a Borel subset of a complete separable metric space $M$, and $\mathcal S$ is the collection of Borel subsets of $S$, then $(S,\mathcal S)$ is nice.

**Exercise 2.1.1** Suppose $\vec{X}$ has density $f(\vec{x})$, which can be written as $g_1(x_1)...g_n(x_n)$, where $g_i$ are nonnegative and measurable, then $X_1,...,X_n$ are independent.

**Exercise 2.1.4** Let $\Omega=(0,1)$,$\mathcal F$ be the collection of Borel sets, and $P$ be the Lebesgue measure, then $X_n(\omega)=\sin(2\pi n\omega)$ are uncorrelated but not independent.



### 2.2 Weak Laws of Large Numbers

***Definition*** we say $X_n\rightarrow X$ **in prob.** if $\forall\epsilon>0, P(|X_n-X|>\epsilon)\rightarrow 0$.

The weak laws of large numbers are in the form that under certain conditions, there is a convergence in prob.

#### 2.2.1 $L^2$ Weak Laws

Our first set of weak laws come from computing variances and using Chebyshev’s inequality.

For the weak laws, we need some preparation.

***Definition*** A family of random variables $X_i,i\in I$ with $EX_i^2<\infty$ is said to be **uncorrelated** if we have $EX_iX_j=EX_iEX_j$ whenever $i\neq j$.

**Theorem 2.2.1** Let $X_1,...,X_n$ are uncorrelated. Then $var(X_1+...+X_n)=var(X_1)+...+var(X_n)$.

**Lemma 2.2.2** If $p>0$ and $E|Z_n|^p\rightarrow 0$ then $Z_n\rightarrow 0$ in prob.

Now we can claim

**Theorem 2.2.3 $L^2$ weak law** Let $X_1,...$ be uncorrelated r.v. with $EX_i=\mu$ and $var(X_i)<C<\infty$. If $S_n=X_1+...+X_n$ then $S_n/n\rightarrow \mu$ in $L^2$ and in prob.

<font color='red'>_proof of Theorem 2.2.3_</font> first observe that $ES_n/n=\mu$, so
$$
E(S_n/n-\mu)^2=var(S_n/n)\leq\frac{Cn}{n^2}\rightarrow 0
$$
By **Lemma 2.2.2**, convergence in $L^2$ implies in prob.

The most common case is when the r.v. are i.i.d..

**Example 2.2.4 Polynomial approximation** Let $f$ be a continuous function on $[0,1]$ and let $f_n(x)=\sum_{m=0}^n C_n^m x^m(1-x)^{n-m}f(m/n)$ be the **Bernstein polynomial of degree n** w.r.t. $f$, then $f_n\rightrightarrows f$.

<font color='red'>_proof of Example 2.2.4_</font> Let $X_i\sim B(1,x)$ i.i.d., then $f_n(x)=Ef(S_n/n)$, and $S_n/n\rightarrow x$ in prob. To estimate the difference, consider 
$$
P(|S_n/n-x|>\delta)\leq \delta^{-2}var(S_n/n)=\frac{x(1-x)}{\delta^2n}\leq \frac{1}{4n\delta^2}\rightarrow 0
$$
So for the difference, pick $\epsilon>0$ and take $\delta$ such that $|x-y|<\delta\Rightarrow|f(x)-f(y)|<\epsilon$,
$$
|f_n(x)-f(x)|\leq E|f(S_n/n)-f(x)|\leq \epsilon+\sup_{x\in[0,1]}2\{f(x)\}P(|S_n/n-x|>\delta)\rightarrow \epsilon
$$
Since $\epsilon$ is arbitrary, the convergence is uniform.

**Example 2.2.5 A high-dimensional cube is almost the boundary of a ball**. Let $X_1,X_2,...\sim U(-1,1)$ i.i.d., and $Y_i=X_i^2$, with $EY_i<1/3$ and $var Y_i<1$, so $(X_1^2+...+X_n^2)/n\rightarrow 1/3$ in prob.

Let $A_{n,\epsilon}={(1-\epsilon)\sqrt{n/3}<|x|<(1+\epsilon)\sqrt{n/3}}$. Then the convergence indicates $|A_{n,\epsilon}\cap(-1,1)^n|/2^n\rightarrow 1$. In other words, most volume of cube $(-1,1)^n$ comes from $A_{n,\epsilon}$, the boundary of the ball raduis $\sqrt{n/3}$

#### 2.2.2 Triangular Arrays

Many classical limit theorems in probability concerns arrays $X_{n,k}, 1\leq k\leq n$ of r.v. and investigate the limiting behavior of their row sums $S_n=X_{n,1}+...+X_{n,n}$. In most cases, we assume the r.v. in each row are independent. 

**Theorem 2.2.6** Let $\mu_n=ES_n$ and $\sigma_n^2=var(S_n)$. If $\sigma_n^2/b_n^2\rightarrow0$, then$\frac{S_n-\mu_n}{b_n}\rightarrow 0$ in prob.

_Remark_ $\mu_n$ are not assumed to be bounded or convergent.

<font color='red'>_proof of Theorem 2.2.6_</font> It converges in $L^2$ trivially.

the following are examples.

_A short lemma_: $\log n\leq\sum_{m=1}^n \frac{1}{m}\leq\log n+1$.

**Example 2.2.7 Coupon collector's problem** Let $X_1,...$ be i.i.d. uniform on $\{1,2,...,n\}$. Consider this as collecting coupons. Suppose that the $i$th item we collect is chosen at random from the set of possibilities and is independent of the previous choices. Let $\tau_k^n$ be the first time that we have collected $k$ different items. In this problem we are interested in the asymptotic behavior of $T_n=\tau_n^n$, the time to collect a complete set. 

First, $\tau_1^n=1$ and we set $\tau_0^n=0$. Let $X_{n,k}=\tau_k^n-\tau_{k-1}^n$ represents the time to get a choice different from our first $k-1$ items, so it has a geometry distribution with parameter $1-(k-1)/n$ and is independent of the earlier waiting times $X_{n,j},1\leq j<k$. So
$$
ET_n=\sum_{k=1}^n[1-(k-1)/n]^{-1}=n\sum_{m=1}^nm^{-1}\approx n\ln n
\\var(T_n)\leq\sum_{k=1}^n[1-(k-1)/n]^{-2}=n^2\sum_{m=1}^n m^{-2}<Cn^2
$$
So using **Theorem 2.2.6** we have $\frac{T_n-ET_n}{n\ln n}\rightarrow 0$ in prob, so $T_n/n\ln n\rightarrow 1$ in prob.

#### 2.2.3 Truncation

To truncate a r.v. means to consider $\bar{X}=X1_{|X|\leq M}$. To extend the weak law of r.v. without a finite second moment, we will truncate and use Chebyshev's inequality. Now we introduce a very general and useful theorem, which can be directly applied to many cases.

**Theorem 2.2.11 Weak law for triangular arrays** For each n let triangular array $X_{n,k}$ be independent in each row. Let $b_n>0$ and $b_n\rightarrow\infty$, and $\bar{X}_{n,k}=X_{n,k}1_{|X_{n,k}|\leq b_n}$. Suppose that as $n\rightarrow\infty$, 

(i) $\sum_{k=1}^n P(|X_{n,k}|>b_n)\rightarrow 0$

(ii) $b_n^{-2}\sum_{k=1}^n E\bar{X}^2_{n,k}\rightarrow 0$.

let $S_n=X_{n,1}+...+X_{n,n}$ and $a_n=\sum_{k=1}^n E\bar{X}_{n,k}$ then $(S_n-a_n)/b_n\rightarrow 0$ in prob.

<font color='red'>_proof of Theorem 2.2.11_</font> Let $\bar{S_n}=\bar{X}_{n,1}+...+\bar{X}_{n,n}$. 
$$
P(|\frac{S_n-a_n}{b_n}|>\epsilon)\leq P(S_n\neq \bar{S_n})+P(|\frac{\bar S_n-a_n}{b_n}|>\epsilon)
\\P(S_n\neq \bar S_n)\leq \sum_{k=1}^nP(X_n\neq \bar X_n)=\sum_{k=1}^n P(|X_n|>b_n)\rightarrow 0
\\P(|\frac{\bar S_n-a_n}{b_n}|>\epsilon)\leq \epsilon^{-2} E(\frac{\bar S_n-a_n}{b_n})^2\leq \epsilon^{-2}b_n^{-2}\sum_{=1}^n E(\bar{X}_{n,k}^2)\rightarrow 0
$$
**Theorem 2.2.12 WLLN** Let $X_1,...,X_n$ be i.i.d. with $xP(|X_i|>x)\rightarrow 0$ as $x\rightarrow\infty$. Let $S_n=X_1+...+X_n$ and $\mu_n=E(X_11_{|X_1|\leq n})$, then $S_n/n-\mu_n\rightarrow 0$ in prob.

_Remark_ $E|X|<\infty\Rightarrow xP(|X|>x)\rightarrow 0$ but not vise versa. So in this case $L^2$ convergence is not assured, and $\mu_n$ doesn't necessarily converges to a finite limit (However they do exist in this condition). But actually $E|X|^{1-\epsilon}<\infty$ in this condition for any $\epsilon>0$.

<font color='red'>_proof of Theorem 2.2.12_</font> Verify using **Theorem 2.2.11**. A lemma is helpful.

**Lemma 2.2.13** If $Y\geq 0$ and $p>0$ then $EY^p=\int_0^\infty py^{p-1}P(Y>y)dy.$

**Theorem 2.2.14** Let $X_1,...$ be i.i.d. and $E|X_1|<\infty$. Then $S_n/n\rightarrow \mu$ in prob.

_Remark_ This is the most familiar form for us. In i.i.d. case, finite variation is not necessary for convergence in prob.

**Example 2.2.15 WLLN doesn't hold** Consider $X_1,...$ are i.i.d. with Cauchy distribution $p(x)=\frac{1}{\pi(1+x^2)}$, then $P(|X_1|>x)\sim \frac{2}{\pi}x^{-1}$, so it doesn't satisfy the condition above. Actually its expectation doesn't exist, so there isn't $\mu_n$ such that $S_n/n-\mu_n\rightarrow 0$

**Exercise 2.2.7** If $H(x)=\int_{-\infty}^x h(y)dy$, $h(y)\geq 0$, then $E\ H(x)=\int_\mathbb R h(y)P(X\geq y)dy$. This is a generalization of **Lemma 2.2.13**

<font color='red'>_proof of Exercise 2.2.7_</font> 
$$
\int_\mathbb R h(y)P(X\geq y)=\int_\mathbb R\int_\Omega h(y)1_{X\geq y}dP dy=\int_\Omega\int_\mathbb R h(y)1_{X\geq y}dydP
\\=\int_\Omega\int_{-\infty}^X h(y)dP=\int_\Omega H(y)dP=E\ H(X)
$$


### 2.3 Borel-Cantelli lemmas

Some basic concepts are skipped. We only list a piece of result from Fatou's lemma:

**Exercise 2.3.1** $P(\limsup A_n)\geq \limsup P(A_n)$ and $P(\liminf A_n)\leq \liminf P(A_n)$.

**Theorem 2.3.1 Borel-Cantelli lemma** If $\sum_{n=1}^\infty P(A_n)<\infty$, then $P(A_n\ i.o.)=0$

<font color='red'>_proof of Theorem 2.3.1_</font> Let $N=\sum_k 1_{A_k}$ be the number of events that occur. By Fubibi's theorem, $EN=\sum_k P(A_k)<\infty$, so $N<\infty$ a.s..

A typical application is,

**Theorem 2.3.2** $X_n\rightarrow X$ in prob. if and only if for any subsequence of $X_n$, say $X_{n_m}$, it has a subsequence which converges to $X$ a.s..

<font color='red'>_proof of Theorem 2.3.2_</font> 

$\Rightarrow$ Extract a subseries which converges fast: Let $\epsilon_k\downarrow 0$, and in $X_{n_m}$ pick its subseries such that $P(|X_{n_{m_k}}-X|>\epsilon_k)<2^{-k}$, so $\sum_k P(|X_{n_{m_k}}-X|>\epsilon_k)<\infty$, which implies $P(|X_{n_{m_k}}-X|>\epsilon_k\ i.o.)=0$, i.e., $X_{n_{m_k}}\rightarrow X$ a.s..

$\Leftarrow$ Use a fact for topology space:

**Theorem 2.3.3** Let $y_n$ be a sequence of elements of a topological space. If every subsequence has a further subsequence converging to y then $y_n\rightarrow y$.

<font color='red'>_proof of Theorem 2.3.3_</font> Otherwise we can find an open set G including $y$ and excluding some subseries, which cannot have a subseries converging to $y$.

So for $y_n=P(|X_n-X|>\delta)$, we know every subsequence of $y_n$ has a subsequence converging to 0 (a.s. convergence), so $y_n\rightarrow 0$. 

_Remark_ a.s. convergence is a pointwise convergence. Moreover, it's not topological: by **Theorem 2.3.3**, if a.s. convergence is induced by topology, then every sequence converges in prob. also converges a.s., which doesn't hold. Moreover convergence in prob. has a metric, under which the space of r.v. is complete.

By **Theorem 2.3.2**, we can upgrade convergence in prob. to convergence a.s.. The first example is:

**Theorem 2.3.4** If $f$ is cts and $X_n\rightarrow_p X$, then $f(X_n)\rightarrow_p f(X)$. If f is bounded, $Ef(X_n)\rightarrow Ef(X)$.

<font color='red'>_proof of Theorem 2.3.4_</font> To prove $f(X_n)\rightarrow_p f(X)$,it suffices to show every subsequence $f(X_{n_k})$ has a subsequence $f(X_{n_{k_m}})$ converging to $f(X)$ a.s.. since $X_n\rightarrow_p X$ in prob, for $X_{n_k}$, we can extract $X_{n_{k_m}}\rightarrow X$ a.s., so $f(X_{n_{k_m}})\rightarrow f(X)$ a.s..

When $f$ is bounded, by bounded convergence theorem, $Ef(X_{n_{k_m}})\rightarrow Ef(X)$, by **Theorem 2.3.3** we have $Ef(X_n)\rightarrow Ef(X)$.

The second example is the first SLLN:

**Theorem 2.3.5** Let $X_1,X_2,...$ be i.i.d., with $EX_i=\mu$ and $EX_i^4<\infty$. Then $S_n\rightarrow \mu$ a.s..

<font color='red'>_proof of Theorem 2.3.5_</font> WLOG suppose $\mu=0$. Now 
$$
ES_n^4=E(\sum_{i=1}^{n} X_i)^4=E\sum_{1\leq i,j,k,l\leq n}X_i X_j X_k X_l
$$
For $i,j,k,l$ distinct, $EX_iX_jX_kX_l, EX_i^2X_jX_k, EX_i^3X_j=0$. So we only need to consider $EX_i^4$ which has n terms and $EX_i^2X_j^2$ which have $C_n^2 C_4^2=3n(n-1)$ terms. So there is some constant C,
$$
ES_n^4= nEX_i^4+3(n^2-n)(EX_1^2)^2\leq Cn^2
$$
By Chebyshev inequality,
$$
P(|S_n|>n\epsilon)\leq ES_n^4/n^4\epsilon^4\leq C/n^2\epsilon^4
$$
So 
$$
\sum_{i=1}^{\infty}P(\frac{|S_i|}{i}>\epsilon)<\infty
$$
which implies $P(|S_n|/n>\epsilon\ i.o.)=0$. Since $\epsilon$ is arbitrary, we have completed.

_Remark_ The converse of Borel Cantelli lemma is false: $\limsup (0,1/n)=\emptyset$ where $\sum 1/n=\infty$. So actually we can't say more than **Exercise 2.3.1**.

However, for independent events, we have:

**Theorem 2.3.7 The second Borel-Cantelli lemma** If the events $A_n$ are independent then $\sum P(A_n)=\infty$ implies $P(A_n\ i.o.)=1$.

<font color='red'>_proof of Theorem 2.3.7_</font> For $M<N<\infty$, independence and $1-x\leq e^{-x}$ imply
$$
P(\cap_{n=M}^N A_n^c)=\prod_{n=M}^N (1-P(A_n))\leq\prod_{n=M}^N \exp(-P(A_n))=\exp(-\sum_{n=M}^N P(A_n))\rightarrow 0, N\rightarrow\infty
$$
So $P(\cup_{n=M}^\infty A_n)=1$ for all M. So $P(\limsup A_n)=1$.

A typical of second Borel Cantelli lemma is:

**Theorem 2.3.8** If $X_1,...$ are i.i.d. with $E|X_i|=\infty$, then $P(|X_n|>n\ i.o.)=1$. So $P(\lim S_n/n\ exists\ \in(-\infty,\infty))=0$.

_Remark_ So $E|X|<\infty$ is necessary for SLLN. Actually, it's also sufficient.

<font color='red'>_proof of Theorem 2.3.8_</font> 

First $\infty=E|X_1|<\sum_n P(|X_n|>n)$, so by Borel Cantelli lemma, $P(|X_n|>n\ i.o.)=1$.

For the second claim, observe that
$$
\frac{S_n}{n}-\frac{S_{n+1}}{n+1}=\frac{S_n}{n(n+1)}-\frac{X_{n+1}}{n+1}
$$
On $C:=\{\omega:\lim S_n/n\ exists\ \in(-\infty,\infty)\}$, we have $S_n/n(n+1)=0$. So on $C\cap \{\omega:|X_n|>n\ i.o. \}$, we have $|S_n/n-S_{n+1}/(n+1)|>2/3$ i.o., which is a contradiction. So $\{\omega: |X_n|\geq n\ i.o. \}\cap C=\emptyset$. This indicates $P(C)=0$.

The next result extends the second Borel Cantelli lemma and sharpens its conclusion. In some sense, it gives the "rate of occurrence".

**Theorem 2.3.9** If $A_1,...$ are pairwise independent and $\sum_{i=1}^{\infty}P(A_i)=\infty$ then as $n\rightarrow \infty$,
$$
\sum_{m=1}^{n}1_{A_m}\bigg /\sum_{m=1}^{n} P(A_m)\rightarrow 1\ a.s.
$$
<font color='red'>_proof of Theorem 2.3.9_</font> Let $X_m=1_{A_m}$, and $S_n=X_1+...+X_n$. 

(i) $S_n/ES_n\rightarrow_p 1$​. Estimate by Chebyshev inequality,
$$
P(|S_n-ES_n|>\delta ES_n)\leq var(S_n)/(\delta ES_n)^2
$$
Since $X_i\in\{0,1\}$ are pairwise independent, we have $var(X_m)\leq EX_m^2=EX_m$, hence $var(S_n)\leq ES_n$. Since $ES_n\rightarrow \infty$, we have
$$
P(|S_n-ES_n|>\delta ES_n)\leq 1/(\delta ^2ES_n)\rightarrow 0
$$
(ii) Pass convergence in prob. to convergence a.s.. 

Extract a subseries (Notice despite we can extract arbitrary by **Theorem 2.3.2**, in order to estimate the whole sequence, we need to be careful): Let $n_k=\inf\{n:ES_n\geq k^2\}$ and $T_k=S_{n_k}$. So $k^2\leq T_k<k^2+1$. Estimate $T_k$,
$$
P(|T_n-ET_n|>\delta ET_n)\leq1/(\delta^2k^2)
$$
Since $\sum_k 1/(\delta^2k^2)<\infty$, $P(|T_n/ET_n -1|>\delta\ i.o.)=0$, and since $\delta$ is arbitrary, we have $T_n/ET_n\rightarrow 1$ a.s..

Estimate $S_n$: pick $\omega$ s.t. $T_k(\omega)/ET_k\rightarrow 1$. For $n_k\leq n<n_{k+1}$, we have 
$$
\frac{T_k(\omega)}{ET_{k+1}}\leq \frac{S_n(\omega)}{ES_n}\leq \frac{T_{k+1}(\omega)}{ET_k}
$$
So we expect to show $ET_{k+1}/ET_k\rightarrow 1$, but this is direct from $k^2\leq T_k<k^2+1$.

_Remark_ Notice $ES_n$ is monotonically increasing. If we are proving $X_n/c_n\rightarrow 1$ where $c_n$ is increasing, it suffices to show that on a subseries the convergence holds, and pass to the whole sequence as above.

**Example 2.3.10 Record Values** Let $X_i$ i.i.d. with cts distribution function F be thought of as scores and $A_k=\{X_k>\sup_{j<k} X_j\}$ is the event of breaking record at time k. 

*Claim*: $A_k$ are independent and $P(A_k)=1/k$.

- Since F is cts, $P(X_i=X_j)=0$. Consider $X_1,...,X_n$. Let $\pi$ be the (random) permutation such that $X_{\pi(i)}$ is decreasing. Since the joint distribution is invariant under any permutation, we have $\pi$ is uniformly distributed on $S_n$.

- $P(A_n)=P(\pi(n)=1)=1/n$. This is direct from previous observation.
- $P(A_m|\pi(j)\text{ is fixed for }j>m)=1/m$. This also results from the symmetry of permutations.

So if we let $m_1<m_2<...<m_k$ then $P(A_{m_1}|A_{m_2}\cap...\cap A_{m_k})=P(A_{m_1})$ since later events doesn't disturb current events by the third observation. Now the claim is trivial.

By these observations, apply **Theorem 2.3.9** we have:

**Theorem 2.3.11** If $R_n=\sum_{m=1}^{n}1_{A_m}$ is the number of records at time n, then as $n\rightarrow \infty$, we have $R_n/\log n\rightarrow 1$ a.s..

_Remark_ This is independent with F as long as F is cts (exclude that any two scores are the same)

_Remark_ under the same hypothesis, let $Y_i=\#\{j\leq i: X_j>X_i\}$, we have $Y_i$ are independent r.v. with $P(Y_i=j)=1/i$ for $0\leq j<i-1$: $P(Y_i=j)=P(\pi(i)=j)=1/i$.

**Example 2.3.12 Head runs** Let $X_n$ i.i.d. with $P(X_n=1)=P(X_n=-1)=1/2$. Let $\mathcal l(n)=\max\{m:X_{n-m+1}=...=X_n=1 \}$ be the length of the run of +1's at time n, and $L_n=\max_{1\leq m\leq n}\mathcal l_m$ be the longest run at time n. We use a two-sided sequence so that for all n, $P(\mathcal l_n=k)=2^{-k-1}$ for $k\geq 0$. Now we want to prove
$$
L_n/\log_2 n\rightarrow 1\ a.s.
$$
Since $\mathcal l_1<\infty$, the result we are going to prove is also true for a one-sided sequence. (We can see for one-sided $\tilde L_n$, $\tilde L_n\leq L_n\leq \tilde L_n+l_1$).

<font color='red'>_proof of the proposition_</font> 

We begin by observing that $P(\mathcal l_n\geq(1+\epsilon)\log_2 n)\leq n^{-(1+\epsilon)}$. Since $\sum_n n^{-(1+\epsilon)}<\infty$ for any $\epsilon$, By Borel Cantelli lemma, we have $\mathcal l_n\leq (1+\epsilon)\log_2 n$ for $n\geq N_\epsilon$. This indicates $\limsup L_n/\log_2 n\leq 1$ a.s..

To estimate the inverse equation, notice when $L_n\leq (1-\epsilon )\log_2 n$ occurs, if we split the sequence with lengths $[(1-\epsilon)\log_2 n]+1$, any of them can't be +1's sequence. This occurs with prob. $1-2^{-[(1-\epsilon)\log_2 n]-1}\leq 1-n^{-1+\epsilon}/2$. So
$$
P(L_n\leq (1-\epsilon)\log_2 n)\leq (1-n^{-1+\epsilon}/2)^{n/(\log_2 n)}\leq \exp(-n^\epsilon/2\log_2 n)
$$
Since this is summable, we have $\liminf_{n\rightarrow\infty} L_n/\log_2 n\geq 1$ a.s..

**Exercise 2.3.4 Fatou's lemma** Suppose $X_n\geq 0$ and $X_n\rightarrow X$ in prob., then $\liminf_{n\rightarrow\infty} EX_n\geq EX$.

**Exercise 2.3.5 Dominated Convergence Theorem** Suppose $X_n\rightarrow X$ in prob. and onw of the two conditions holds:

(a) $|X_n|\leq Y$ with $EY<\infty$

(b) $\exists g\in C(\mathbb R)$, when $x$ is large $g(x)>0$ and $|x|/g(x)\rightarrow 0$ as $|x|\rightarrow\infty$, and satisfies $Eg(X_n)\leq C<\infty$ for all n.

Then $EX_n\rightarrow EX$.

_Remark_ These are primarily true for a.s. convergence. By **Theorem 2.3.2**, these results can be extended to convergence in prob..

**Exercise 2.3.6 Metric for convergence in prob. ** Define $d(X,Y)=E(|X-Y|/(1+|X-Y|))$, then this defines a metric on the space of r.v.. This is complete and its convergence is equivalent to convergence in prob. (This is standard in Real Analysis)

**Exercise 2.3.8** Let $A_n$ be a sequence of independent events with $P(A_n)<1$ for all n. Show that $P(\cup A_n)=1$ implies $\sum_n P(A_n)=\infty$ and hence $P(A_n\ i.o.)=1$.

<font color='red'>_proof of Exercise 2.3.8_</font> So $1-P(A_n)>0$ and $\prod_n(1-P(A_n))=0$. So $\sum_n P(A_n)=\infty$ (from analysis). By Borel Cantelli lemma, $P(A_n\ i.o.)=1$.

**Exercise 2.3.9** Let $A_n$ be a sequence of events with $P(A_n)\rightarrow 0$ and $\sum_{n=1}^{\infty} P(A_n^c\cap A_{n+1})<\infty$. Then $P(A_n\ i.o.)=0$.

<font color='red'>_proof of Exercise 2.3.9_</font> Let $B_n=A_n^c\cap A_{n+1}$Notice If $\omega\in A_n$i.o. but $\omega\notin B_n$i.o., then there must be some k such that $\omega\in A_n$ for all $n\geq k$. So we have $\{A_n\ i.o.\}\subset \{B_n\ i.o.\}\cup( \cup_{n\geq 1}\cap_{k\geq n} A_k)$. So
$$
P(A_n\ i.o.)\leq P(B_n\ i.o.)+\lim_{n\rightarrow\infty}P(\cap_{k\geq n}A_k)=P(B_n\ i.o.)
$$
Since $P(A_n)\rightarrow 0$. Since by Borel Catelli lemma, $P(B_n\ i.o.)=0$, we have $P(A_n\ i.o.)=0$.

_Remark_ In some cases when Borel Cantelli lemma fails, this can be applied. For example, we can construct on $((0,1),m,\mathcal B)$: Let $A_n=[a_n,a_n+1/(n+1)]$ where $a_k=\sum_{n=2}^k\frac{1}{2n^2}$. 

**Exercise 2.3.10 Kochen-Stone lemma** Suppose $\sum P(A_k)=\infty$. If 
$$
\limsup_{n\rightarrow\infty}(\sum_{i=1}^{n}P(A_i))^2\bigg /(\sum_{1\leq j,k\leq n}P(A_j\cap A_k))=\alpha>0
$$
then $P(A_n\ i.o.)\geq \alpha$.

<font color='red'>_proof_</font> Left for later completion.

