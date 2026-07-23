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

<font color='red'>_proof_</font> Let $S_n=\sum_{k=1}^n 1_{A_k}$, $ES_n=\sum_{i=1}^{n} P(A_i)^2$ and $\sum_{1\leq j,k\leq n}P(A_j\cap A_k)=ES_n^2$. Moreover, $ES_n^2\rightarrow\infty$.

Since $\limsup_{n\rightarrow\infty} (ES_n)^2/(ES_n^2)=\alpha$, choose a subseries s.t. $\lim_{m\rightarrow\infty}(ES_{n_m})^2/(ES_{n_m}^2)=\alpha$. 

Notice $P(A_n\ i.o.)\geq P(S_{n_m}\geq r)$ for all sufficient large m. And we have estimation:
$$
P(S_{n_m}\geq r)\geq \frac{(ES_{n_m}-r)^2}{ES_{n_m}^2}
$$
So $\liminf_{m\rightarrow\infty}P(S_{n_m}\geq r)\geq \alpha$ for all $r>0$. So $P(A_n\ i.o.)\geq \alpha$.

_Remark_ Such form of inequality is called **Paley-Zygumid inequality**: If $X\geq 0$ and have finite second moment,
$$
\begin{aligned}
P(X \ge \theta E[X]) &\ge (1-\theta)^2 \frac{(E[X])^2}{E[X^2]}(\text{standard form})
\\P(X\geq t)&\geq \frac{(E[X]-t)^2}{E[X^2]}(\text{threshold version})
\\P(X>0)&\geq \frac{(E[X])^2}{E[X^2]} (\text{Let }t\rightarrow 0)
\end{aligned}
$$
_Remark_ When $A_i$ are independent, notice the limit term is just 1, so $P(A_n\ i.o.)=1$. This is just the second Borel Cantelli lemma.

### 2.4 Strong Law of Large Numbers

**Theorem 2.4.1 Strong Law of Large Numbers** Let $X_1,X_2,...$ be pairwise independent identically distributed r.v. with $E|X_i|<\infty$. Let $EX_i=\mu$ and $S_n=X_1+...+X_n$. Then $S_n/n\rightarrow\mu$ a.s..

To prove this theorem, we begin from truncating. These two lemmas are standard.

**Lemma 2.4.2** Let $Y_k=X_k1_{|X_k|\leq k}$ and $T_n=Y_1+...+Y_n$. To prove $S_n/n\rightarrow \mu$ a.s., it suffices to show $T_n/n\rightarrow \mu$.

<font color='red'>_proof of Lemma 2.4.2_</font> $\sum_{k=1}^\infty P(|X_k|>k)\leq E|X_1|<\infty$. so $P(X_k\neq Y_k\ i.o.)=0$. So $|S_n(\omega)-T_n(\omega)|$ is a.s. finite, and $|S_n-T_n|/n\rightarrow 0$ a.s.

**Lemma 2.4.3** $\sum_{k=1}^\infty var(Y_k)/k^2\leq 4E|X_1|<\infty$.

First, to bound the sum, we observe
$$
var(Y_k)\leq E(Y_k^2)=\int_0^\infty 2yP(|Y_k|>y)dy\leq \int_0^k 2yP(|X_1|>y)dy
$$
So using Fubini's theorem,
$$
\begin{aligned}
\sum_{k=1}^\infty E(Y_k^2)/k^2&\leq \sum_{k=1}^\infty k^{-2}\int_0^\infty1_{y<k}2yP(|X_1|>y)dy
\\&=\int_0^\infty(\sum_{k=1}^\infty k^{-2} 1_{y<k})2yP(|X_1|>y)dy
\\&\leq \int_0^\infty 4P(|X_1|>y)dy=4E|X_1|
\end{aligned}
$$
Next, observe that $X=X_+-X_-$, and $EX_+,EX_-<\infty$, so WLOG let $X\geq 0$. Again, we use the technique from **Theorem 2.3.9**, i.e., extract a convergent subsequence, and by the monotonicity of $c_n=n$, control the values in between. 

<font color='red'>_proof of Theorem 2.4.1_</font> Let $\alpha>1$ and $k(n)=[\alpha^n]$. By Chebyshev's inequality, 
$$
\sum_{n=1}^\infty P(\frac{|T_{k(n)}-ET_{k(n)}|}{k(n)}\geq\epsilon)\leq \epsilon^{-2}\sum_{n=1}^\infty\frac{var(T_{k_n})}{k(n)^2}=\epsilon^{-2}\sum_{n=1}^\infty\sum_{k=1}^{k(n)}\frac{var(Y_k)}{k(n)^2}=\epsilon^{-2}\sum_{k=1}^\infty var(Y_k)\sum_{n:k(n)\geq k}^\infty k(n)^{-2}
$$
Actually, choose $k(n)=[\alpha^n]$ is to ensure:
$$
\sum_{n:k(n)\geq k}^\infty k(n)^{-2}=\sum_{[\alpha^n]\geq k}[\alpha^n]^{-2}\leq \sum_{\alpha^n\geq k}4\alpha^{-2n}\leq 4(1-\alpha^{-2})^{-1}k^{-2}
$$
So we can use **Lemma 2.4.3**,
$$
\sum_{n=1}^\infty P(\frac{|T_{k(n)}-ET_{k(n)}|}{k(n)}\geq\epsilon)\leq \epsilon^{-2}4(1-\alpha^{-2})^{-1}\sum_{k=1}^\infty k^{-2}var(Y_k)<\infty
$$
Since $\epsilon$ is arbitrary, $(T_{k(n)}-ET_{k(n)})/k(n)\rightarrow 0$ a.s..

- By DCT, $ET_{k(n)}\rightarrow EX_1$.

- The control argument: if $k(n)\leq m<k(n+1)$,
  $$
  \frac{T_{k(n)}}{k(n+1)}\leq \frac{T_m}{m}\leq \frac{T_{k(n+1)}}{kn}
  $$
  Since we have supposed $Y_n\geq 0$. Since $k(n+1)/k(n)\rightarrow\alpha$,
  $$
  \frac{1}{\alpha}EX_1\leq \liminf_{n\rightarrow\infty}T_n/n\leq \limsup_{n\rightarrow\infty}T_n/n\leq\alpha EX_1
  $$
  Since $\alpha$ is arbitrary, we have completed our proof.

The next result shows that SLLN holds whenever $EX_i$ exists (including infinity).

**Theorem 2.4.5** Let $X_1,...$ be i.i.d. with $EX_i^+=\infty$ and $EX_i^-<\infty$. Then $S_n/n\rightarrow\infty$.

<font color='red'>_proof of Theorem 2.4.5_</font> Let $M>0$ and $X_i^M=X_i\wedge M$. Then $X_i^M$ are i.i.d. and $E|X_i^M|<\infty$. So Let $S_n^M=X_1^M+...+X_n^M$ then $S_n^M/m\rightarrow EX_i^M$ a.s.. Since by MCT, $E(X_i^M)^+\uparrow\infty$, we have $EX_i^M\uparrow\infty$ and $\liminf_{n\rightarrow\infty} S_n/n\geq\infty$.

The next example is to show the application of SLLN.

**Example 2.4.6 Renewal theory** Let $X_1,X_2,...$ be i.i.d. with $0<X_i<\infty$. Let $T(n)=X_1+...+X_n$ and think of $T(n)$ as the time of $n$ th occurrence of some event, if we assume the waiting time is i.i.d.. Let $N_t=\sup\{n:T(n)\leq t \}$ ne the number of occurrence up to time n.

**Theorem 2.4.7** If $EX_1=\mu\leq\infty$ then as $t\rightarrow\infty$, $N_t/t\rightarrow 1/\mu\ a.s.$.

<font color='red'>_proof of Theorem 2.4.7_</font> By **Theorem 2.4.1** and **2.4.5**, $T_n/n$ a.s., and control $N_t$ by
$$
\frac{T(N_t)}{N_t}\leq \frac{t}{N_t}\leq \frac{T(N_t+1)}{N_t}=\frac{T(N_t+1)}{N_t+1}\frac{N_t+1}{N_t}
$$
by the definition of $N_t$. Since $N_t\rightarrow\infty$ as $t\rightarrow\infty$ ($X_i<\infty$), we have $T(N_t)/N_t\rightarrow \mu$ and $(N_t+1)/N_t\rightarrow 1$, which completes our proof.

_Remark_ If $X_n\rightarrow X_\infty$ a.s., and $N(n)\rightarrow\infty$ a.s., then $X_{N(n)}\rightarrow X_\infty$ a.s. by the pointwise convergence. But this can be false for convergence in prob.. If $X_n\in\{0,1 \}$ are independent r.v. s with $P(X_n=1)=a_n\rightarrow 0$ and $\sum_n a_n=\infty$, then $X_n\rightarrow 0$ in prob. and not a.s.. Let $N(n)=\inf\{m\geq n: X_m=1 \}$. First, $N(n)\neq \infty$ since $P(X_n=1\ i.o.)=1$. Next, $N(n)\uparrow\infty$ . But $X_{N(n)}=1$ a.s..

The next example shows us "frequency is approximately probability".

**Example 2.4.8 Empirical distribution functions** Let $X_1,X_2,...$ be i.i.d. with distribution $F$ and let $F_n(x)=n^{-1}\sum_{m=1}^n 1_{X_m\leq x}$, i.e., the observed frequency of values $\leq x$.

**Theorem 2.4.9 The Glivenko-Cantelli theorem** $\sup_x |F_n(x)-F(x)|\rightarrow 0$ a.s.

_Remark_ $F$ may have jumps, which makes the proof somewhat complicated. See PTE for proof.

**Example 2.4.10 Shannon's theorem** Let $X_1,X_2,...\in\{1,...,r\}$ be independent with $P(X_i=k)=p(k)>0$ for $1\leq k\leq r$. Let $\pi_n(\omega)=p(X_1(\omega))...p(X_n(\omega))$ be the probability of realization at first n trials. By SLLN, $-n^{-1}\log \pi_n(\omega)\rightarrow H:=\sum_{k=1}^r -p(k)\log p(k)$ a.s., and the constant $H$ is called the entropy of the source which measures the randomness. Asymptotic equipartition property says if $\epsilon>0$, then $P(e^{-n(H+\epsilon)}\leq \pi_n(\omega)\leq e^{-n(H-\epsilon)})\rightarrow 1$ as $n\rightarrow\infty$.

**Example 2.4.1** For the renewal process let $0<X_i<\infty$ be i.i.d. with $EX_i<\infty$ and $0<Y_i<\infty$ be i.i.d. with $EY_i<\infty$. Suppose the two process take turns beginning with $X$, and let $R_t$ be the time of waiting times for process $X_i$. Then $R_t/t\rightarrow EX_i/(EX_i+EY_i)$ a.s..

<font color='red'>_proof of Exercise 2.4.1_</font> Let $N_t$ denotes the occurrence of events for $X$, then similar argument implies $R_t/N_t\rightarrow EX_i$. and consider the process as a renewal process with waiting time $X_n+Y_n$, $t/N_t\rightarrow EX_i+EY_i$. So $R_t/t\rightarrow EX_i/(EX_i+EY_i)$.

### 2.5 Convergence of Random Series

Based on convergence of random series, we can attain SLLN in another way, estimate convergence rate and attain a negative result for infinite mean. First Let's introduce some notations.

**Definition** Let $\mathcal F_n^\prime=\sigma(X_n,X_{n+1},...)$, i.e., the future information after time n. Let $\mathcal T=\cap_n\mathcal F_n^\prime$ be the remote future, or **tail $\sigma$-field**.

**Example 2.5.1** If $B_n\in\mathcal R$ then $\{ X_n\in B_n\ i.o.\}\in\mathcal T$. If we let $X_n=1_{A_n}$, and $B_n=\{1\}$, the event is $\{A_n\ i.o.\}$.

**Example 2.5.2** Let $S_n=X_1+...+X_n$, then $\{\lim_{n\rightarrow\infty} S_n\text{ exists} \}\in\mathcal T$, $\{\limsup_{n\rightarrow\infty} S_n>0 \}\notin \mathcal T$ (since adjust $X_1$, $S_n$ can be negative), $\{\limsup_{n\rightarrow\infty} S_n/c_n>x \}\in\mathcal T$ if $c_n\rightarrow\infty$.(since adjusting finite many $X_i$ the limit will not be disturbed.)

This results shows that all examples are trivial. Actually, this is the second 0-1 law we meet. The first is Borel Cantelli lemma for independent events.

**Theorem 2.5.3 Kolmogorov's 0-1 law** If $X_1,X_2,...$ are independent and $A\in\mathcal T$, then $P(A)=0\ or\ 1$.

<font color='red'>_proof of Theorem 2.5.3_</font> We will show that $A$ is independent of itself, i.e., $P(A\cap A)=P(A)P(A)$, so $P(A)=0\ or\ 1$. We follow two steps:

- $A\in\sigma(X_1,...,X_k)$ and $B\in\sigma(X_{k+1},X_{k+2},...)$ are independent.

  proof: If $B\in\sigma(X_{k+1},...,X_{k+j})$ for some $j$, then by **Theorem 2.1.9** they are independent. Since $\sigma(X_1,...,X_k)$ and $\cup_j \sigma (X_{k+1},...,X_{k+j})$ are $\pi$-systems that contain $\Omega$, by **Theorem 2.1.7** They are independent.

- $A\in\sigma(X_1,...)$ and $B\in\mathcal T$ are independent.

  proof: If $A\in\sigma(X_1,...,X_k)$ for some k, then $A$ and $B$ are independent. Since $\cup_k\sigma(X_1,...,X_k)$ and $\mathcal T$ are $\pi$-systems that contain $\Omega$, by **Theorem 2.1.7** they are independent.

So $A$ is independent of itself.

Now let's introduce another 0-1 law.

**Definition** A **finite permutation** of $\mathbb N$ is a map $\pi: \mathbb N\rightarrow\mathbb N$ s.t. $\pi(i)\neq i$ for finitely many $i$. If $\pi$ is a finite permutation, define $(\pi\omega)_i=\omega_{\pi(i)}$ for $\omega\in S^\mathbb N$. This can be also regarded as rearranging $X_i$s. An event is **permutable** if $\pi^{-1}A:=\{ \omega:\pi\omega\in A\}$ for any finite permutation $\pi$, in other words, its occurrence is not affected by rearranging finitely many r.v. s. The collection of permutable events is a $\sigma$-field and is called the **exchangeable** $\sigma$-field, denoted by $\mathcal E$.

**Example** $\{\omega: S_n(\omega)\in B\ i.o.\}$, $\{\omega: \limsup_{n\rightarrow\infty} S_n(\omega)/c_n\geq 1 \}$, all events in $\mathcal T$ are all permutable. 

Notice actually this exchangeable $\sigma$-field may be larger than $\mathcal T$, for example, $\{\limsup_{n\rightarrow\infty} S_n>0 \}$ is in $\mathcal E$. But for i.i.d. sequence, they are identical and trivial.

**Theorem 2.5.4 Hewitt-Savage 0-1 law** If $X_1,X_2,...$ are i.i.d. and $A\in\mathcal E$ then $P(A)=0\ or\ 1$.

For proof see PTE, since this is operating on measure space.

Upon now, we know if $A_1,A_2,...$ are independent then $P(A_n\ i.o.)=0\ or\ 1$. So $P(\lim_{n\rightarrow\infty}S_n\text{ exists})=0\ or\ 1$.Now we concerns when the prob. is 1.

**Theorem 2.5.5 Kolmogorov's maximal inequality** Suppose $X_1,...,X_n$ are independent with $EX_i=0$ and $var(X_i)<\infty$. If $S_n=X_1+...+X_n$, then we have 
$$
P(\max_{1\leq k\leq n}|S_k|\geq x)\leq x^{-2}var(S_n)
$$
_Remark_ Under the same hypothesis, Chebyshev's inequality only gives $P(|S_n|\geq x)\leq x^{-2}var(S_n)$. So this inequality is much stronger.

<font color='red'>_proof of Theorem 2.5.5_</font> Actually $S_n$ is a martingale, so we are using the techniques from martingales to prove this. Actually, this is a version of Doob's maximal inequality.

let $A_k=\{|S_k|\geq x\text{ but }|S_j|<x\text{ for }j<k \}$, i.e., the event $|S_k|$ hits $x$ at k for the first time. They are disjoint, so
$$
\begin{aligned}
ES_n^2&\geq \sum_{k=1}^n ES_n^21_{A_k}=\sum_{k=1}^n E(S_k^2+2S_k(S_n-S_k)+(S_n-S_k)^2)1_{A_k}
\\&\geq\sum_{k=1}^n ES_k^21_{A_k}+\sum_{k=1}^n 2ES_k(S_n-S_k)1_{A_k}=\sum_{k=1}^nES_k^21_{A_k}+\sum_{k=1}^n2ES_k1_{A_k}E(S_n-S_k)
\\&=\sum_{k=1}^n ES_k^21_{A_k}
\\&\geq\sum_{k=1}^n x^2P(A_k)=x^2P(\max_{1\leq k\leq n}|S_k|\geq x)
\end{aligned}
$$
Now we can state the results on convergence of series. 

**Theorem 2.5.6** Suppose $X_1,X_2,...$ are independent and have $EX_n=0$. If $\sum_{n=1}^\infty var(X_n)<\infty$, then $\sum_{n=1}^\infty X_n(\omega)$ converges a.s.

<font color='red'>_proof of Theorem 2.5.6_</font> let $S_N=\sum_{n=1}^N X_n$ and by **Theorem 2.5.5**, we get
$$
P(\max_{M\leq m\leq N}|S_m-S_M|>\epsilon)\leq \epsilon^{-2}var(S_N-S_M)=\epsilon^{-2}\sum_{n=M+1}^N var(X_n)
$$
Let $N\rightarrow\infty$,
$$
P(\sup_{m\geq M}|S_m-S_M|>\epsilon)\leq \epsilon^{-2}\sum_{n=M+1}^\infty var(X_n)\to 0(M\rightarrow \infty)
$$
Let $w_M=\sup_{m,n\geq M}|S_m-S_n|$, then $w_M\downarrow$as $M\uparrow$ and 
$$
P(w_M>2\epsilon)\leq P(\sup_{m\geq M}|S_m-S_M|>\epsilon)\rightarrow 0
$$
So $w_M\downarrow 0$ a.s., $S_n(\omega)$ is Cauchy.

**Example 2.5.7** Let $X_1,...$ be independent with $P(X_n=n^{-\alpha})=P(X_n=-n^{-\alpha})=1/2$. Then $EX_n=0$ and $var(X_n)=n^{-2\alpha}$. So if $\alpha>1/2$, $\sum X_n$ converges a.s..This is actually necessary by **Theorem 2.5.8**. Notice the series is absolutely convergent iff $\alpha>1$.

**Theorem 2.5.8 Kolmogorov's three-series theorem** Let $X_1,X_2,...$ be independent, and let $A>0$, $Y_i=X_i1_{|X_i|\leq A}$. $\sum_{n=1}^\infty X_n$ converges a.s. iff

(i) $\sum_{n=1}^\infty P(|X_n|>A)<\infty$ (ii) $EY_n$ converges (iii)$\sum_{n=1}^\infty var(Y_n)<\infty$

<font color='red'>_proof of Theorem 2.5.8_</font> Necessity will be proved after CLT. Now we consider sufficiency. Let $\mu_n=EY_n$

By (iii) and **Theorem 2.5.6**, $\sum_{n=1}^\infty Y_n-\mu_n$ converges a.s.. By (ii), $\sum_{n=1}^\infty Y_n$ converges a.s.. By (i) and Borel Cantelli lemma, $\sum_{n=1}^\infty P(X_n\neq Y_n)<\infty$, whence $X_n\neq Y_n\ i.o.$, $\sum_{n=1}^\infty X_n$ converges a.s..

Now we link convergence of series and SLLN:

**Theorem 2.5.9 Kronecker's lemma** If $a_n\uparrow\infty$ and $\sum_{n=1}^\infty x_n/a_n$ converges, then $a_n^{-1}\sum_{m=1}^n x_m\to 0$. 

_Remark_ This is purely a result of analysis. For the proof refer to PTE.

**Theorem 2.5.10 SLLN** Let $X_1,...$ be i.i.d. r.v. s with $E|X_i|<\infty$, then $S_n/n\to\mu$ a.s..

_Remark_ **Theorem 2.4.1** requires $X_i$ to be pairwise independent while we require they are independent here.

<font color='red'>_proof of Theorem 2.5.10_</font> The two lemmas are still useful here. let $Y_k=X_k1_{|X_k|\leq k}$ and $T_n=Y_1+...+Y_n$, it suffices to show SLLN holds for $T_n$. Let $Z_k=Y_k-EY_k$, by the second lemma $\sum_{k=1}^\infty var(Z_k)/k^2<\infty$. Apply **Theorem 2.5.6**, $\sum_{k=1}^\infty Z_k/k$ converges a.s.. Apply **Theorem 2.5.9**, $n^{-1}\sum_{k=1}^n Z_k\to 0$, i.e., $T_n/n-n^{-1}\sum_{k=1}^n EY_k\rightarrow 0$ a.s.. By DCT, $EY_k\to\mu$, and $n^{-1}\sum_{k=1}^n EY_k\to\mu$. So $T_n/n\to\mu$ a.s..

#### 2.5.1 Rates of Convergence

**Theorem 2.5.11** Let $X_1,X_2,...$ be i.i.d. r.v. s with $EX_i=0$, $EX_i^2=\sigma^2<\infty$. Then
$$
S_n/(n^{1/2}(\log n)^{1/2+\epsilon})\rightarrow 0\ a.s.
$$
<font color='red'>_proof of Theorem 2.5.11_</font> Let $a_1>0$, $a_n=n^{1/2}(\log n)^{1/2+\epsilon}$ for $n\geq 2$,
$$
\sum_{n=1}^\infty var(X_n/a_n)=\sigma^2\sum_{n=1}^\infty 1/a_i^2<\infty
$$
By **Theorem 2.5.6** $\sum_{n=1}^\infty X_n/a_n$ converges a.s. and the result is from Kolmogorov's lemma.

**Theorem 2.5.12** Let $X_1,X_2,...$ be i.i.d. with $EX_1=0$ and $E|X_1|^p<\infty$ where $1<p<2$. Then $S_n/n^{1/p}\to 0$ a.s.

_Remark_ When the second moment is infinite this can be used for estimation the rate.

<font color='red'>_proof of Theorem 2.5.12_</font> This proof is somewhat complicated. We prove step by step.

First as before we truncate. Let $Y_k=X_k1_{|X_k|\leq k^{1/p}}$ and $T_n=Y_1+...+Y_n$.

(i) it suffices to show for $Y_n$: $\sum_{n=1}^\infty P(X_n\neq Y_n)=\sum_{n=1}^\infty P(|X_k|^p>k)\leq E|X_k|^p<\infty$. By Borel Cantelli lemma, $P(Y_k\neq X_k\ i.o.)=0$. Notice the truncation is s.t. we can estimate in (ii) better.

(ii) Estimate $var(Y_m/m^{1/p})$:
$$
\begin{aligned}
\sum_{m=1}^\infty var(Y_m/m^{1/p})&\leq \sum_{m=1}^\infty EY_m^2/m^{2/p}
\\&\leq \sum_{m=1}^\infty\sum_{n=1}^m\int_{(n-1)^{1/p}}^{n^{1/p}}\frac{2y}{m^{2/p}}P(|X_1|>y)dy
\\&=\sum_{n=1}^\infty\int_{{(n-1)}^{1/p}}^{n^{1/p}}\sum_{m=n}^\infty \frac{2y}{m^{2/p}}P(|X_1|>y)dy
\\&\leq\sum_{n=1}^\infty\int_{(n-1)^{1/p}}^{n^{1/p}}C(n-1)^{1-2/p}\ 2yP(|X_1|>y)dy
\\&\leq\sum_{n=1}^\infty\int_{(n-1)^{1/p}}^{n^{1/p}}2Cy^{p-1}P(|X_1|>y)dy
\\&=2CE|X_1|^p<\infty
\end{aligned}
$$
By **Theorem 2.5.6 2.5.12** we can show $n^{-1/p}\sum_{m=1}^n (Y_m-\mu_m)\to 0$ a.s.

(iii) Estimate $\mu_m/m^{1/p}$, where $\mu_m=EY_m$. Since $EX_m=0$, $\mu_m=-E(X_11_{|X_i|>m^{1/p}})$
$$
|\mu_m|\leq E(|X|1_{|X|>{m^{1/p}}})=m^{1/p}E(|X|/m^{1/p}1_{|X|/m^{1/p}>1})\leq m^{1/p}E(|X|^p/m1_{|X|^p>m})
$$
Since $\sum m^{1-1/p}<\infty$, $E(|X|^p1_{|X|^p>m})\to 0$, we have $\sum n^{-1/p}\mu_n\to 0$ a.s..

_Remark_ The inverse is also true:
$$
E|X_i|^p\leq \sum_{n=0}^\infty P(|X_1|^p>n)=\sum_{n=0}^\infty P(|X_i|>n^{1/p})<\infty
$$
Since to ensure $S_n/n^{1/p}\to 0$, $|X_i|>n^{1/p}\ i.o.$ is not allowed. 

#### 2.5.2 Infinite Mean

**Theorem 2.5.13** Let $X_1,X_2,...$ be i.i.d. with $E|X_1|=\infty$ and let $S_n=X_1+...+X_n$. Let $a_n$ be a sequence of positive numbers with $a_n/n$ increasing. Then $\limsup_{n\rightarrow\infty} |S_n|/a_n=0\ or\ \infty$ according as $\sum_n P(|X_1|>a_n)<\infty\ or\ =\infty$.

<font color='red'>_proof of Theorem 2.5.13_</font> 

If $\sum_n P(|X_1|>a_n)=\infty$, we can estimate
$$
\sum_{n=1}^\infty P(|X_1|/a_n\geq k)\geq \sum_{n=1}^\infty P(|X_1|/a_{kn}\geq 1)\geq \frac{1}{k}\sum_{n=k}^\infty P(|X_1|/a_n\geq 1)=\infty
$$
Since $a_n/n$ and $a_n$ are both increasing. This implies $|X_n|/a_n\geq k$ i.o.. Since $k$ is arbitrary, this implies $\limsup_{n\rightarrow\infty}|X_n|/a_n=\infty$. To pass to $S_n$, notice $\max\{|S_{n-1}|, |S_n| \}\geq |X_n|/2$. So $\limsup_{n\rightarrow\infty}|S_n|/a_n=\infty$.

If $\sum_n P(|X_1|>a_n)<\infty$, we still truncate. Define $Y_n=X_n1_{|X_n|<a_n}$ and $T_n$ are partial sums. Since the series is finite, $P(X_n\neq Y_n\ i.o.)=0$. So it suffices to study $Y_n$. 
$$
\begin{aligned}
\sum_{n=1}^\infty var(Y_n/a_n)&\leq \sum_{n=1}^\infty EY_n^2/a_n^2
\\&=\sum_{n=1}^\infty\sum_{m=1}^n EY_n^21_{a_{m-1}\leq |Y_n|\leq a_m}/a_n^2
=\sum_{m=1}^\infty\sum_{n=m}^\infty EY_n^21_{a_{m-1}\leq |Y_n|\leq a_m}/a_n^2
\\&\leq\sum_{m=1}^\infty\sum_{n=m}^\infty(a_m/a_n)^2P(a_{m-1}\leq |Y_n|\leq a_m)\leq\sum_{m=1}^\infty CmP(a_{m-1}\leq |Y_n|\leq a_m)
\\&=\sum_{m=1}^\infty\sum_{n=1}^m CP(a_{m-1}\leq |Y_n|\leq a_m)=\sum_{n=1}^\infty\sum_{m=n}^\infty CP(a_{m-1}\leq |Y_n|\leq a_m)
\\&=\sum_{n=1}^\infty CP(|Y_n|\geq a_{n-1})\leq C\sum_{n=1}^\infty P(|X_n|\geq a_{n-1})<\infty
\end{aligned}
$$
So $(T_n-ET_n)/a_n\to 0$.

And $ET_n/a_n\to 0$:
$$
\begin{aligned}
\bigg |a_n^{-1}\sum_{m=1}^n EY_m\bigg |&\leq a_n^{-1}nE(|X_n|1_{|X_n|<a_n})
\\&\leq a_n^{-1}n(a_N+E(|X_n|1_{a_N\leq |X_i|<a_n}))
\end{aligned}
$$
The first term, $a_N(n/a_n)\to 0$, since $\sum_{k=1}^\infty P(|X_i|\geq kt)\geq E|X_i|/t=\infty$. So to make $\sum_n P(|X_1|>a_n)=\infty$, $a_n/n\uparrow\infty$.

The second term, as we estimate before,
$$
a_n^{-1}nE(|X_n|1_{a_N\leq |X_n|\leq a_n})=a_n^{-1}n\sum_{k=N}^{n-1}E|X_n|1_{a_k\leq |X_n|\leq a_{k+1}}\leq \sum_{k=N}^{n-1}a_{k+1}^{-1}(k+1)E|X_n|1_{a_k\leq |X_n|\leq a_{k+1}}\leq \sum_{k=N}^{n-1}(k+1)P(a_k\leq |X_n|\leq a_{k+1})\leq \infty
$$
The last step is similar to the end of estimation of $var(Y_n)/a_n$.

**Exercise 2.5.10 by P.Levy** Let $X_1,X_2,...$ be independent and $S_n$ is the partial sum. If $\lim_{n \to \infty}S_n$ exists in prob. Then it exists a.s.

<font color='red'>_proof of Exercise 2.5.10_</font> First we need a lemma:

**Exercise 2.5.9** Let $S_{m,n}=S_n-S_m$, then
$$
P(\max_{m<j\leq n}|S_{m,j}|>2a)\min_{m<k\leq n}P(|S_{k,n}|\leq a)\leq P(|S_{m,n}|>a)
$$
<font color='red'>_proof of Excerise 2.5.9_</font>
$$
LHS\leq \sum_{j=m+1}^n P(j=\text{argmax}_{m<j\leq n}|S_{m,j}|)P(|S_{m,j}|>2a)P(|S_{j,n}|\leq a)\leq \sum_{j=m+1}^n P(j=\text{argmax}_{m<j\leq n}|S_{m,j}|)P(|S_{m,n}|>a)=RHS
$$
return to our proof. Suppose $S_n\to x$ in prob., i.e., $P(|S_n-x|>\epsilon)\to 0\forall \epsilon>0$. Then 
$$
P(|S_{m,n}|>2\epsilon)\leq P(|S_m-x|>\epsilon)+P(|S_n-x|>\epsilon)\to 0,\ m,n\to\infty
$$
Use the lemma,
$$
P(\max_{m<j\leq n}|S_{m,j}|>2\epsilon)\min_{m<k\leq n}P(|S_{k,n}|\leq \epsilon)\leq P(|S_{m,n}|>\epsilon)
$$
We can argue
$$
P(\max_{m<j\leq n}|S_{m,j}|>2\epsilon)\to 0, m,n\to\infty
$$
Let $n\to\infty$, we have $P(\sup_{j>m}|S_{m,j}|>2\epsilon)\to 0$ as $n\to\infty$. This already implies $S_n$ converges a.s..

_Remark_ This inequality seems to be useful since it can estimate the "inside" of a series using boundary. Again, this is similar with reflection principle.

### 2.6 Renewal Theory

Let $\xi_1,\xi_2,...$ be i.i.d. positive r.v.s, and define T by $T_0=0, T_k=T_{k-1}+\xi_k\ \text{for}\ k\geq 1$.$T_k$ is called **renewals** since the process starts afresh at $T_k$, i.e., $\{T_{k+j}-T_k \}=_d \{T_j \}$. Let $N_t=\inf\{k:T_k>t \}$ denotes the number of renewals in $[0,t]$.

<img src="C:\Users\m1500\Desktop\Durrent\images\renewal process.png" alt="renewal process" style="zoom:50%;" />

**Theorem 2.6.1** As $t\to\infty$, $N_t/t\to1/\mu$ a.s., where $\mu=E\xi_i\in(0,\infty]$. $1/\infty=0$ (**Theorem 2.4.7**)

Now we consider the asymptotic behavior of $U(t)=EN_t$.

**Theorem 2.6.2 Wald's equation** Let $X_1,X_2,...$ be i.i.d. with $E|X_1|<\infty$. If $N$ is a stopping time and $EN<\infty$, then $ES_N=EX_1EN$.

<font color='red'>_proof of Theorem 2.6.2_</font> First suppose $X_i\geq 0$,
$$
\begin{aligned}
ES_N&=\int S_NdP=\sum_{n=1}^\infty\int S_n1_{N=n}dP=\sum_{m=1}^\infty\sum_{m=1}^n\int X_m1_{N=n}dP
\\&=_{(\text{Fubini})}\sum_{m=1}^\infty\sum_{n=m}^\infty\int X_m1_{N=n}dP=\sum_{m=1}^\infty\int X_m1_{N\geq m}dP
\\&=\sum_{m=1}^\infty EX_m1_{N\geq m}=\sum_{m=1}^\infty EX_mP(N\geq m)=EX_1EN
\end{aligned}
$$
For the general case, since $|X_m|\geq 0$, so the above identity holds for $|X_m|$. This implies for the step using Fubini theorem, the terms are absolutely summable. This indicates that for general case, the Fubini theorem also holds. So the result is the same.

**Theorem 2.6.3** As $t\to\infty$, $U(t)/t\to1/\mu$.

<font color='red'>_proof of Theorem 2.6.3_</font> We will apply Wald's equation to the stopping time $N_t$, where $t$ is fixed.

- $EN(t)<\infty$. For $\epsilon>0$, pick $P(\xi>\delta)=\epsilon$, $K\delta>t$. So we have
  $$
  P(N_t>K)=P(T_K<t)=1-P(T_K>t)\leq1-\epsilon^K
  \\P(N_t>mK)=P(T_{mK}<t)\leq P(T_K<t)^m\leq (1-\epsilon^K)^m
  $$
  by the renewal property. Since RHS is summable, $EN_t<\infty$.

- Apply Wald's equality, $\mu EN_t=ET_{{N_t}}\geq t$ 

- For the inverse equality, if $\xi\leq c$ a.s., then $\mu EN_t=ET_{N_t}\leq t+c$. For general case, define $\bar{\xi_i}=\xi_i\wedge c$ and define $\bar T_n$, $\bar{N_t}$ in the obvious way. Then we have $EN_t\leq E\bar N_t\leq (t+c)/E(\bar \xi_i)$. This implies $\liminf_{t\rightarrow\infty}EN_t/t\leq 1/E\bar\xi_i$. Let $c\to\infty$, we can get the inverse inequality.

Generalize the definition of $U$, we can consider 
$$
U(A)=\sum_{n=1}^\infty P(T_n\in A)
$$
$U(t)=U([0,t])$ in this sense. Notice by this we define a measure called **renewal measure**. 

The asymptotic behavior of $U(t)$ depends on whether the distribution $F$ of $\xi_i$ is arithmetic, i.e., concentrated on $\{\delta,2\delta,3\delta,... \}$ for some $\delta>0$ or nonarithmetic. The first case will be treated using Markov chain, now we consider the second case.

**Theorem 2.6.4 Blackwell's renewal theorem** If $F$ is nonarithmetic then $U([t,t+h])\to h/\mu$ as $t\to\infty$.

<font color='red'>_proof of Theorem 2.6.4_</font>

First we consider the case $\mu<\infty$. Our strategy is coupling.

Now we work on some preparations. 

**Definition** In the renewal process, if $T_0\geq 0$ is independent of $\xi_1,\xi_2,...$ and has distribution $G$, then $T_{k+1}=T_k+\xi_k$ defines a **delayed renewal process**, and $G$ is the **delay distribution**. Let $N_t=\inf \{k:T_k> t \}$, $V(t)=EN_t$. So $V(t)=Y_0+U(t)$, we have $V=U*G$. 

Similarly, to attain an equation w.r.t. $F$, regard $\xi_1$ as delay and we have $U=1_{[0,\infty)}(t)+U*F$. Combine these, we have $V=G+U*G*F=G+V*F$.

If we expect $V(t)=t/\mu$, some calculations indicate $G(t)=\frac{1}{\mu}\int_0^t1-F(y)dy$. Actually, this is the distribution of the age of the last renewal $A_t=t-T_{N(t)-1}$ in the non-delay case. The magic is, if we set $Y_0$ to have this law, the delayed process is stationary, i.e., $N_t-N_s=_dN_{t-s}$.

Return to the proof. Let $T_n$ be a renewal process and $T_n'$ be an independent stationary renewal process. 

- Our first goal is to find $J,K$ s.t. $|T_J-T_K'|<\epsilon$ and increments $T_{J+i}-T_J$, $T_{K+i}'-T_K'$ are i.i.d. sequences independent of what has come before.

- Let $\eta_1,\eta_2,...$ and $\eta_1',\eta_2',...$ $\sim B(0,1/2)$ be i.i.d. independent of $T_n$ and $T_n'$, $\nu_n=\eta_1+...+\eta_n$, $\nu_n'=1+\eta_1'+...+\eta_n'$, $S_n=T_{\nu_n}$, $S_n'=T_{\nu_n'}'$.

- Notice $\Delta_{n+1}=S_{n+1}-S_{n+1}'-(S_n-S_n')$ has symmetric distribution, so it has mean 0. Moreover $P(\Delta_{n+1}=0)\geq 1/4$ (comes from $\eta_{n+1}=\eta_{n+1}'$).This random walk is actually neighborhood recurrent so if $N=\inf\{n:|S_n-S_n'|<\epsilon \}$, $P(N<\infty)=1$.

- Define $J=\nu_N$, $K=\nu_N'$, and 
  $$
  T_n''=\left\{\begin{aligned}&T_n&if\ J\geq n\\&T_J+T_{K+(n-J)}'-T_K'&if\ J<n\end{aligned}\right.
  $$
  <img src="C:\Users\m1500\Desktop\Durrent\images\coupling of renewal process.png" alt="coupling of renewal process" style="zoom:50%;" />

  i.e., $T_{J+i}''-T_J''=_dT_{K+i}'-T_K'$. Meanwhile, $T_n=_d T_n''$.

  _Remark_ We constructed a recurrent random walk to let two independent renewal process  to be close enough at some step, then consider the later increments.

- Let $N'[s,t]=|\{n:T_n'\in[s,t] \}|$ and $N''[s,t]=|\{n:T_n''\in[s,t] \}|$, on $T_J\leq t$,
  $$
  N''[t,t+h]=N'[t+T_K'-T_J,t+h+T_K'-T_J]\geq N'[t+\epsilon,t+h-\epsilon],\leq N'[t-\epsilon,t+h+\epsilon]
  $$
  So when $\epsilon<h/2$,
  $$
  U([t,t+h])=EN''[t,t+h]\geq EN'[t+\epsilon,t+h-\epsilon]1_{T_J\leq t}=\frac{h-2\epsilon}{\mu}-EN'[t+\epsilon,t+h-\epsilon]1_{T_J\geq t}\geq \frac{h-2\epsilon}{\mu}-P(T_J>t)U(h)
  $$

  $$
  U([t,t+h])\leq EN'[t-\epsilon,t+h+\epsilon]1_{T_J\leq t}+EN''[t,t+h]1_{T_J>t}\leq \frac{h+2\epsilon}{\mu}+P(T_J>t)U(h)
  $$

  Since $P(T_J>t)\to 0$ and $\epsilon$ is arbitrary, we finished our proof.

- The case $\mu=\infty$ is referred to PTE.

Now we consider **renewal equation**: $H=h+H*F$. we have seen

**Example 2.6.5** $h=1$: $U=1+U*F$

**Example 2.6.6** $h=G$: $V=G+V*F$.

**Example 2.6.7** $h=\frac{1}{\mu}\int_t^\infty 1-F(s)ds, H=U(t)-t/\mu$: $H=h+H*F$.

**Example 2.6.8** Let $x>0$ be fixed and let $H(t)=P(T_{N(t)}-t>x)$, By considering the value of $T_1$, we get $H(t)=(1-F(t+x))+\int_0^t H(t-s)dF(s)$.

These examples motivate us to consider

**Theorem 2.6.9** If $h$ is bounded then the function $H(t)=\int_0^t h(t-s)dU(s)$ is the unique solution of renewal equation that is bounded on bounded intervals. (Notice $U=\sum_{n=0}^\infty F^{n*}$)

<font color='red'>_proof of Theorem 2.6.9_</font> Let $U_n(A)=\sum_{m=0}^nP(T_m\in A)$ and $H_n(t)=\int_0^t h(t-s)dU_n(s)=\sum_{m=0}^{n}(h*F^{m*})(t)$. So we have $H_{n+1}=h+H_n*F$. 

Since $U(t)<\infty$, we have $U(t)-U_n(t)\to 0$. Since $h$ is bounded, $|H_n(t)-H(t)|\leq \|h\|_\infty|U(t)-U_n(t)|$. So on any bounded interval, $H_n\rightrightarrows H$.

Meanwhile, $|H_n*F-H*F|\leq\sup_{s\leq t}|H_n(s)-H(s)|\leq\|h\|_\infty|U_t-U_n(t)|$ since $U-U_n$ is increasing. So on any bounded interval $H_n*F\rightrightarrows H*F$. In the iteration equation let $n\to\infty$, $H$ is the solution.

For uniqueness, if $H_1$, $H_2$ are solutions then $K=H_1-H_2$ satisfies $K=K*F$. Then $K=K*F^{n*}$.Since $K$ is bounded on bounded intervals, $|K(t)|\leq \sup|K|F^{n*}(t)\to 0$. So $H_1=H_2$.

_Remark_ This proof is valid when $F(\infty)=P(\xi_i<\infty)<1$. In this case, we have a **terminating renewal process**. After a geometric number of trials with mean $1/(1-F(\infty))$, $T_n=\infty$.

**Example 2.6.10 Pedestrian delay** Let $X_t$ be a Poisson process with rate $\lambda$, and
$$
M=\inf\{ t\geq 0:\text{there are no arrivals in } (t,t+1] \}:=\inf\{T_n:T_{n+1}-T_n\geq 1 \}
$$
 Then $H(t)=P(M\leq t)$ satisfies
$$
H(t)=e^{-\lambda}+\int_0^1H(t-y)\lambda e^{-\lambda y}dy
$$
So $H(t)=e^{\lambda} \sum_{n=1}^\infty F^{n*}(t)$.

To calculate $EM$, think of this as a geometric distribution with success prob. $p=e^{-\lambda}$, and every trial has mean $\mu=\int_0^1 x\lambda e^{-\lambda x}dx=\lambda^{-1}-(1+\lambda^{-1})e^{-\lambda}$
$$
EM=\sum_{n=0}^\infty p(1-p)^nn\mu=(1/p-1)\mu
$$
**Example 2.6.11 Cramer's estimation of ruin** Consider an insurance company that collects money at rate $c$ and experience i.i.d. claims at the arrival time of a Poisson process $N_t$ with rate 1. If its initial capital is $x$, then its wealth at time $t$ is $W_x(t)=x+ct-\sum_{m=1}^{Nt} Y_i$, where $Y_i$ are i.i.d. with distribution $G$ and mean $\mu$. Let $R(x)=P(W_x(t)\geq 0\forall t>0)$ be the prob. of never going bankrupt starting from $x$. First we have
$$
R(x)=\int_0^\infty e^{-s}\int_0^{x+cs}R(x+cs-y)dG(y)ds
$$
To make it a renewal equation, we can derive by

- let $t=x+cs$
  $$
  R(x)e^{-x/c}=\int_x^\infty e^{-t/c}\int_0^tR(t-y)dG(y)\frac{dt}{c}
  $$

- differentiate,
  $$
  R'(x)e^{-x/c}-1/cR(x)e^{-x/c}=-e^{-x/c}/c\int_0^xR(x-y)dG(y)
  \\cR'(x)=(R(x)-\int_0^xR(x-y)dG(y))
  $$

- integrate back,
  $$
  \begin{aligned}
  c(R(w)-R(0))&=\int_0^wR(x)dx-\int_0^w\int_0^xR(x-y)dG(y)dx
  \\&=\int_0^w R(x)dx-\int_0^w\int_y^wR(x-y)dxdG(y)
  \\&=\int_0^w R(x)dx+\int_0^w\int_y^wR(x-y)dxd(1-G(y))
  \\&=\int_0^w R(x)dx-\int_0^wR(x)dx+\int_0^w(1-G(y))R(w-y)dy
  \end{aligned}
  $$

- Finally,
  $$
  R(w)=R(0)+\int_0^w R(w-y)\frac{1-G(y)}{c}dy
  $$

Now we analyze this renewal process. If $\mu>c$,
$$
\frac{1}{t}(ct-\sum_{m=1}^{Nt} Y_i)\to c-\mu<0\ a.s.
$$
So $R(x)\equiv 0$.

When $\mu<c$, $F(x)=\int_0^x\frac{1-G(y)}{c}dy$ is a defective prob. distribution with $F(\infty)=\mu/c$. The renewal equation can be written as $R=R(0)+R*F$. It's solution is $R(w)=R(0)U(w)$. To obtain $R(0)$, notice when $w\to\infty$, we have $R(\infty)=1$ since in this case the company will never go bankrupt and $U(\infty)=\sum_{n=0}^\infty F^{*n}(\infty)=\sum_{n=0}^\infty (1-F(\infty))^n=(1-F(\infty))^{-1}=(1-\mu/c)^{-1}$. So $R(0)=1-\mu/c$.

For nonarithmetic case, the basic fact about solutions of the renewal equation is:

**Theorem 2.6.12 The renewal theorem** If $F$ is nonarithmetic and $h$ is directly Riemann integrable then as $t\to\infty$, $H(t)\to\frac{1}{\mu}\int_0^\infty h(s)ds$.

_Remark_ Since $H(t)=\int_0^t h(t-s)dU(s)$ and $dU(s)\to ds/\mu$ by Blackwell's renewal theorem, intuitively this holds. As in PTE, we will introduce "directly Riemann integrable" in the proof.

<font color='red'>_proof of Theorem 2.6.12_</font> Start from step functions of Riemann style, suppose $h(s)=\sum_{k=0}^\infty a_k1_{[k\delta,(k+1)\delta)}(s)$, where $\sum_{k=1}^\infty |a_k|<\infty$. Since $U([t,t+\delta])\leq U(\delta)<\infty$ (since the renewal process during $[t,t+\delta]$ is indeed a delayed renewal process.) , use Blackwell's renewal process we have (estimate finite terms and tail respectively)
$$
\int_0^th(t-s)dU(s)=\sum_{k=0}^\infty a_k U((t-(k+1)\delta,t-k\delta])\to \frac{1}{\mu}\sum_{k=0}^\infty a_k\delta,\ t\to\infty
$$
If $h$ is arbitrary function on $[0,\infty)$, let
$$
I^\delta=\sum_{k=0}^\infty\delta\sup\{h(x):x\in[k\delta,(k+1)\delta) \}
\\I_\delta=\sum_{k=0}^\infty\delta\inf\{h(x):x\in[k\delta,(k+1)\delta] \}
$$
we have 
$$
\frac{I_\delta}{\mu}\leq\liminf_{t\rightarrow\infty}\int_0^th(t-s)dU(s)\leq\limsup_{t\rightarrow\infty}\int_0^th(t-s)dU(s)\leq\frac{I^\delta}{\mu}
$$
We call $h$ is **directly Riemann integrable** if $I_\delta$ and $I^\delta$ have the same limit as $\delta\to 0$.In this case, $\int_0^th(t-s)dU(s)\to I/\mu$. In common Riemann integration, $\int_0^\infty f(x)dx=\lim_{t \to \infty}\int_0^tf(x)dx$, but in this case we directly segment $[0,\infty)$. This leads us to ask what kind of functions are directly Riemann integrable.

**Lemma 2.6.13** If $h(x)\geq 0$ is decreasing with $h(0)<\infty$ and $\int_0^\infty h(x)dx<\infty$, $h$ is directly Riemann integrable.

Return to previous examples. Notice for **Example 2.6.5 2.6.6**, $h\to 1$, so it's not integrable.

**Example 2.6.14 Continuation of Example 2.6.7** $h(t)=\frac{1}{\mu}\int_{[t,\infty)}1-F(s)ds$ is decreasing and $h(0)=1<\infty$ Moreover, $\int_0^\infty h(t)=E\xi_i^2/2\mu$. So when $E\xi_i^2<\infty$, we have $U(t)-t/\mu\to E\xi_i^2/2\mu^2$ as $t\to\infty$.

When the renewal process is a rate $\lambda$ Poisson process, $U(t)=1+\lambda t$, $\mu=\frac{1}{\lambda}$ and $E\xi_i^2=\frac{2}{\lambda^2}$, the limit can be verified to be true.

**Example 2.6.15 Continuation of Example 2.6.8** $h(t)=1-F(t+x)$ is decreasing, $h(0)=1-F(x)<\infty$, and $\int_0^\infty h(t)dt$ is finite iff $\mu<\infty$. So 
$$
P(T_{N(t)}-t>x)\to\frac{1}{\mu}\int_0^\infty h(s)ds=\frac{1}{\mu}\int_x^\infty 1-F(t)dt
$$
So the distribution of **residual waiting time** converges to the delay distribution that produces the stationary renewal process. Denote $B_t=T_{N(t)}-t$.

**Exercise 2.6.4** Let $A_t=t-T_{N(t)-1}$ be the age at time t. $H(t)=P(A_t>x)$​ satisfies the renewal equation
$$
H(t)=1_{(x,\infty)}(t)(1-F(t))+\int_0^tH(t-s)dF(s)
$$
So $P(A_t>x)\to \frac{1}{\mu}\int_0^\infty (1-F(t))1_{(x,\infty)}(t)dt$. 

_Remark_ Notice this has the same law with the limit of residual lifetime. The symmetry is reasonable, since if at some time $t$ is age and $s$ is residual lifetime then at another time $t$ can be residual lifetime and $s$ can be the age. Moreover, these two are not independent in general. This can be shown in 

**Exercise 2.6.6** $P(A_t>x,B_t>y)\to\frac{1}{\mu}\int_{x+y}^\infty (1-F(t))dt$.

<font color='red'>_proof of Exercise 2.6.6_</font> Let $H(t)=P(A_t>x,B_t>y)$. $H$ satisfies renewal equation
$$
H(t)=1_{(x+y,\infty)}(t)[1-F(t)]+\int_0^t H(t-s,y)ds
$$
So $H(t)\to\frac{1}{\mu}\int_0^\infty 1_{(x+y,\infty)}(t)[1-F(t)]dt$.

From this, we can obtain the limit"lifetime" distribution $A_t+B_t$ 
$$
P(A_t+B_t>z)=\frac{1}{\mu}\int_z^\infty tdF(t)
$$
**Exercise 2.6.5** Take Poisson process with rate $\lambda$ as example. $A_t$ has distribution (Notice this is not limit distribution) by **Theorem 2.6.9**,
$$
P(A_t>x)=\left\{\begin{aligned}&0,&x>t\\&e^{-\lambda x}-e^{-\lambda t},&x\leq t\end{aligned}\right.
$$
which has the same distribution with $\xi_i\wedge t$. This results from the memoryless property. 

$B_t$ has the distribution $P(B_t>x)=e^{-\lambda x}$. So when $t\to\infty$, their distributions are the same.

$A_t+B_t$ satisfies renewal equation: set $H(t)=P(A_t+B_t\geq x)$,
$$
H(t)=(1-F(x))1_{(0,x)}(t)+\int_0^tH(t-s)dF(s)
$$
So it has distribution $H(t)=\lambda (t\wedge x)e^{-\lambda x}$.

Actually, one can verify $A_t$ and $B_t$ are independent by using the renewal equation in **Exercise 2.6.6**. This is a special case, which also results from memoryless property.

**Exercise 2.6.7 Alternating renewal process** Let $\xi_1,\xi_2,...>0$ be i.i.d. with distribution $F_1$ and $\eta_1,\eta_2,...>0$ be i.i.d. with distribution $F_2$. Let $T_0=0$ and for $k\geq 1$ let $S_k=T_{k-1}+\xi_k$, $T_k=S_k+\eta_k$. Let $F=F_1*F_2$ and $H_t=P(T_k<t<S_{k+1}\text{ for some }k\geq 0)$.If $F$ is nonarithmetic then as $t\to\infty$, $H(t)\to\mu_1/(\mu_1+\mu_2)$, where $\mu_i$ is the mean of $F_i$.

<font color='red'>_proof of Exercise 2.6.7_</font> The renewal equation for $H(t)$ is 
$$
H(t)=1-F_1(t)+\int_0^tH(t-s)dF(s)
$$
and its limit is given by
$$
H(t)\to\frac{1}{\mu_1+\mu_2}\int_0^\infty1-F_1(s)ds=\frac{\mu_1}{\mu_1+\mu_2}
$$
**Exercise 2.6.9 Renewal densities** 

- If $F(t)$ has a directly Riemann integrable density function $f(t)$, then $V=U-1_{[0,\infty)}$ has a density $v$ that satisfies $v(t)=f(t)+\int_0^t v(t-s)dF(s)$.

- <font color='red'>_proof_</font> First the density is Radon-Nikodym derivative. Since $U(t)=\sum_{n=0}^\infty F^{*n}$, $V=\sum_{n=1}^\infty F^{*n}$. If $F$ has density $f$, $V$ has density $\sum_{n=1}^\infty f^{*n}$, so
  $$
  v=f+\sum_{n=2}^\infty f^{*n}=f+\sum_{n=2}^\infty\int_0^\infty f^{*(n-1)}(t-s)dF=f+\int_0^\infty v(t-s)dF
  $$

- By renewal theorem, if f is directly Riemann integrable then $v(t)\to\frac{1}{\mu}\int_0^\infty f(t)dt=1/\mu$. This result can be seen Blackwell renewal theorem when $\delta\to 0$.

### 2.7 Large Derivations

Let $X_1,X_2,...$ be i.i.d. and let $S_n=X_1+X_2+...$. We will investigate the rate at which $P(S_n>na)\to 0$ for $a>\mu=EX_i$. 

The final result is, if the moment-generating function $\varphi(\theta)=E\exp(\theta X_i)<\infty$ for some $\theta>0$, then $P(S_n\geq na)\to 0$ exponentially rapidly and we will identify 
$$
\gamma(a)=\lim_{n \to \infty}\frac{1}{n}\log P(S_n\ge na)
$$
Our first step is to prove that the limit exists.

**Observation** let $\pi_n=P(S_n\ge na)$, since $S_m, S_{n+m}-S_m$ are independent, 
$$
\pi_{m+n}\geq P(S_m\geq ma,S_{n+m}-S_m\geq na)=\pi_m\pi_n
$$
Let $\gamma_n=\log\pi_n$ to transform multiplication into addition, then $\gamma_{m+n}\geq \gamma_m+\gamma_n$. For this property we have:

**Lemma 2.7.1** If $a_{m+n}\geq a_m+a_n$, then $a_n/n\to\sup_m a_m/m$.

<font color='red'>_proof of Lemma 2.7.1_</font> Clearly $\limsup_{n\rightarrow\infty} a_n/n\leq\sup a_m/m$. It suffices to show $\liminf_{n\rightarrow\infty} a_n/n\geq a_m/m\ \forall m$. Writing $n=km+l$ with $0\leq l<m$, we have $a_n\geq ka_m+a_l$, so
$$
a_n/n\geq \frac{km}{km+l}a_m/m+a_l/n
$$
let $n\rightarrow\infty$, $\lim RHS=a_m/m$. 

This implies $\gamma_m/m$ has a negative limit $\gamma(a)$, and
$$
P(S_n\geq n\alpha)\leq e^{n\gamma(a)}
$$
This conclusion is valid for any distribution, but it's not very useful if $\gamma(a)=0$. For the rest of this section, we will suppose:

**Hypothesis**  $\varphi(\theta)<\infty$ for some $\theta>0$. We can deduce some properties:

- Let $\theta_+=\sup\{\theta:\varphi(\theta)<\infty\}$ and $\theta_-=\{\theta:\varphi(\theta)<\infty \}$. Then we have 

  **Proposition** $\varphi(\theta)<\infty$ for all $\theta\in(\theta_-,\theta_+)$.

  <font color='red'>_proof_</font> For $\theta\in(\theta_-,\theta_+)$, pick $a<\theta<b$ s.t. $\varphi(a),\varphi(b)<\infty$. Then $\theta=ta+(1-t)b$ for some $t\in[0,1]$. Then we have
  $$
  E\exp(\theta X_i)=E\exp((ta+(1-t)b)X_i)=E\exp(taX_i)\exp((1-t)bX_i)\leq [E\exp(aX_i)]^t[E\exp(bX_i)]^{1-t}<\infty
  $$
  So $\{\theta:\varphi(\theta)<\infty \}$ is a convex set. On $\mathbb R$, it can only be an interval.
  
- **Proposition** $\varphi$ is differentiable on $[0,\theta_+)$.

  <font color='red'>_proof_</font> 

  (i) $\kappa(\theta)$ is cts on $[0,\theta_+)$: $\forall \theta'\geq 0$, pick $0<\theta'<\theta_0<\theta_+$, we have $e^{\theta x}\leq 1+e^{\theta_0 x}\ \forall x\forall\theta\in[0,\theta_0]$. Since $E[1+e^{\theta_0 x}]<\infty$, by DCT we have $Ee^{\theta X}\to Ee^{\theta_0 X}$.

  (ii) $\kappa(\theta)$ is differentiable on $[0,\theta_+)$: 

  - First, if we formally differentiate, $\varphi'(\theta)=EXe^{\theta X}$. 

    $EXe^{\theta X}<\infty$: First we have $|X|\leq (e^{\theta |X|}-1)/\theta$, so if we pick $\theta_0$ s.t. $0<\theta-\theta_0<\theta+\theta_0<\theta_+$, we have
    $$
    E|X|e^{\theta X}\leq 1/\theta_0 \ Ee^{\theta X+\theta_0 |X|}=1/\theta_0[Ee^{(\theta-\theta_0) X}+Ee^{(\theta+\theta_0)X}]<\infty
    $$

  - if $|h|<h_0$, we have $|e^{hx}-1|=|\int_0^{hx}e^y dy|\leq |hx|e^{h_0 x}$. Then by DCT, when $\theta+h_0<\theta_+$,
    $$
    \varphi'(\theta)=\lim_{h \to 0}\frac{\varphi(\theta+h)-\varphi(\theta)}{h}=\lim_{h \to 0}\int_\mathbb R \frac{e^{hx}-1}{h}e^{\theta x}dF(x)=\int_\mathbb Rxe^{\theta x}dF(x)
    $$

  _Remark_ Actually we can work on this repeatedly, i.e., $\varphi(\theta)\in C^\infty([0,\theta_+))$.

Under the hypothesis, $\theta EX_i^+\leq E\exp(\theta X_i)<\infty$. So $\mu=EX^+-EX^-\in[-\infty,\infty)$.

If $\theta>0$, Chebyshev's inequality implies $e^{\theta na}P(S_n\geq na)\leq E\exp(\theta S_n)=\varphi(\theta)^n$. Let $\kappa(\theta)=\log\varphi(\theta)$, we have $P(S_n\geq na)\leq\exp(-n(a\theta-\kappa(\theta)))$. Moreover, by the smoothness of $\varphi$, we have

**Lemma 2.7.2** If $a>\mu$ and $\theta>0$ is small then $a\theta-\kappa(\theta)>0$.

<font color='red'>_proof of Lemma 2.7.2_</font> Since $\varphi$ is differentiable, $\kappa$ is differentiable and $\kappa'=\varphi'/\varphi$, so $\kappa'(0)=EX$. If $a>EX$, then $(a\theta-\kappa(\theta))'|_{\theta=0}>0$.

Moreover, $\phi(\theta)=a\theta-\kappa(\theta)$ is concave:
$$
\phi''(\theta)=-\frac{\varphi''(\theta)\varphi(\theta)-\varphi'^2(\theta)}{\varphi(\theta)^2}=-\frac{EX^2e^{\theta X}Ee^{\theta X}-[EXe^{\theta X}]^2}{\varphi(\theta)^2}<0
$$
by Cauchy inequality, and the equality holds when $X=c$ for some $c$. 

On PTE, we define $F_\theta(x)=\frac{1}{\varphi(\theta)}\int_{-\infty}^x e^{\theta y}dF(y)$ to prove this

- This is a distribution 
- Radon-Nikodym derivative $\frac{dF_\theta}{dF}=\frac{e^{\theta x}}{\varphi(\theta)}$.
- If $X\sim F_\theta$, $EX=\varphi'(\theta)/\varphi(\theta)$.

**Hypothesis** $X$ is not a constant.

Under this hypothesis, the extremum is unique. Let's begin discussing existence by examples.

**Example 2.7.3 Normal distribution** Suppose $X\sim \mathcal N(0,1)$
$$
\varphi(\theta)=Ee^{\theta X}=\int_\mathbb R e^{\theta x}\frac{1}{\sqrt{2\pi}}e^{-\frac{x^2}{2}}dx=e^{\theta^2/2}
$$
In this case $\phi'(\theta)=a-\theta$, $F_\theta(x)=e^{-\theta^2/2}\int_{-\infty}^x e^{\theta y}\frac{1}{\sqrt{2\pi}}e^{-y^2/2}dy$, the CDF of $\mathcal N(\theta,1)$.

**Example 2.7.4 Exponential distribution with parameter $\lambda$** If $\theta<\lambda$, we have
$$
\varphi(\theta)=\int_\mathbb R e^{\theta x}\lambda e^{-\lambda x}=\lambda/(\lambda-\theta)
$$
in this case $\phi'(\theta)=a-1/(\lambda-\theta)$ and $F_\theta(x)=(\lambda-\theta)\int_0^x e^{(\theta-\lambda) y} dy$, the CDF of $Exp(\lambda-\theta)$.

**Example 2.7.5 Coin flips** $P(X_i=1)=P(X_i=-1)=1/2$,
$$
\varphi(\theta)=\frac{e^\theta+e^{-\theta}}{2}=\cosh \theta
$$
in this case $\phi'(\theta)=a-\tanh \theta$, and $F_\theta(1)=e^\theta/(e^\theta+e^{-\theta})$, $F_\theta(-1)=e^{-\theta}/(e^\theta+e^{-\theta})$.

**Example 2.7.6 Perverted exponential ** Let $g(x)=Cx^{-3}e^{-x}$ for $x\geq 1$ and $0$ otherwise, $C$ is chosen to make $g$ a density. Then 
$$
\varphi(\theta)=\int_1^\infty e^{\theta x}Cx^{-3}e^{-x}dx
$$
and $\varphi(\theta)<\infty$  iff $\theta\leq 1$. in this case $\varphi'(\theta)/\varphi(\theta)\leq \varphi'(1)/\varphi(1)=\int_1^\infty Cx^{-3}dx/\int_1^\infty Cx^{-2}dx=2$.

In **Example 2.7.3 2.7.4**, $\phi'(+\infty)=-\infty$, so we can always solve them; in **Example 2.7.5**,  $\phi'(+\infty)=1$; in **Example 2.7.6**, $\phi'\geq a-2$, so when $a>2$ we cannot solve this.

First, if we suppose the existence of root of $\phi(\theta)$, 

**Theorem 2.7.7** Suppose under above hypotheses, there is a $\theta_a\in(0,\theta_+)$ so that $a=\varphi'(\theta)/\varphi(\theta)$. Then as $n\to\infty$, we have $n^{-1}\log P(S_n\geq na)\to -a\theta_a+\log\varphi(\theta_a)$.

<font color='red'>_proof of Theorem 2.7.7_</font> 

- Since we have deduced $P(S_n\geq na)\leq \exp(-n(a\theta-\kappa(\theta)))$, and $\theta_a$ is the minimum point of $\exp(-n(a\theta-\kappa(\theta)))$, we have $\limsup_{n\rightarrow\infty} LHS\leq RHS$. 

- For the inverse inequality, pick $\lambda\in(\theta_a,\theta_+)$, and let $X_1^\lambda,X_2^\lambda,...$ be i.i.d. with distribution $F_\lambda$, and let $S_n^\lambda=X_1^\lambda+...+X_n^\lambda$. To connect this with the distribution of $S_n$, we have 

**Lemma 2.7.8** $\frac{dF^{*(n)}}{dF^{*(n)}_\lambda}=e^{-\lambda x}\varphi(\lambda)^n$.

<font color='red'>_proof of Lemma 2.7.8_</font> By induction, when $n=1$ this holds. when $n\geq 1$,
$$
\begin{aligned}
F^{*(n)}(z)&=F^{*(n-1)}*F(z)=\int_\mathbb R dF^{*(n-1)}(x)\int_{_\infty}^{z-x}dF(y)
\\&=\int_\mathbb R e^{-\lambda x}\varphi(\lambda)^{n-1} dF_\lambda^{*(n-1)}(x)\int_\mathbb R dF_\lambda(y) e^{-\lambda y}\varphi(\lambda)1_{x+y\leq z}
\\&=E(1_{S_{n-1}^\lambda+X_n^\lambda\leq z}e^{-\lambda(S_{n-1}^\lambda+X_n^\lambda)}\varphi(\lambda)^n)
\\&=\int_{-\infty}^z dF_\lambda^{*(n)}(u)e^{-\lambda u}\varphi(\lambda)^n
\end{aligned}
$$
Return to our proof. If $\nu>a$, the lemma and monotonicity imply
$$
P(S_n\geq na)\geq \int_{na}^{n\nu}e^{-\lambda x}\varphi(\lambda)^ndF_\lambda^{*(n)}(x)\geq \varphi(\lambda)^ne^{-\lambda n\nu}(F_\lambda^{*(n)}(n\nu)-F_\lambda^{*(n)}(na))
$$
$F_\lambda$ has mean $\varphi'(\lambda)/\varphi(\lambda)$, so if we have $a<\varphi'(\lambda)/\varphi(\lambda)<\nu$, by WLLN we have as $n\rightarrow\infty$, 
$$
F_\lambda^{*(n)}(n\nu)-F_\lambda^{*(n)}(na)\to 1
$$
So $\liminf_{n\rightarrow\infty} n^{-1}\log P(S_n>na)\geq -\lambda \nu+\log \varphi(\lambda)$. Since $\lambda>\theta_a$ and $\nu>a$ is arbitrary, the inverse inequality is proved. 

Let $\gamma(a)=-a\theta_a+\log \varphi(\theta_a)$,

**Example 2.7.3 Normal distribution** $\gamma(a)=-a^2/2$.

**Example 2.7.4 Exponential distribution** $\gamma(a)=-a\lambda+1+\log a\lambda$.

**Example 2.7.5 Coin flips** $\gamma(a)=-a\tanh^{-1} a-\frac{1}{2}\log (1-a^2)$.

When we cannot solve $\phi(\theta)=0$, we have 

**Theorem 2.7.9** Suppose $x_o=\sup\{x:F(x)<1 \}<\infty$ and $F$ is not a point mass at $x_o$. Then $\varphi(\theta)<\infty\forall \theta>0$ and $\varphi'(\theta)/\varphi(\theta)\to x_o$ as $\theta\uparrow\infty$.

<font color='red'>_proof of Theorem 2.7.9_</font> Since $P(X\leq x_o)=1$, $Ee^{\theta X}<e^{\theta x_o}<\infty\forall \theta>0$, and since $F_\theta$ is concentrated on $(-\infty,x_o]$, $\varphi'(\theta)/\varphi(\theta)=\mu_\theta<x_o$.

On the other hand, if $\delta>0$, then $P(X\geq x_o-\delta)=c_\delta>0$, so $Ee^{\theta X}\geq c_\delta e^{\theta(x_o-\delta)}$, and hence 
$$
F_\theta(x_0-2\delta)=\frac{1}{\varphi(\theta)}\int_{-\infty}^{x_o-2\delta}e^{\theta x}dF(x)\leq \frac{e^{\theta(x_o-2\delta)}}{c_\delta e^{\theta(x_o-\delta)}}\to 0
$$
as $\theta\to\infty$. Since $\delta>0$ is arbitrary, $\mu_\theta\to x_o$.

When $a=x_o$, $\frac{1}{n}\log P(S_n\geq nx_o)=\log P(X_i=x_o)\forall n$, which is trivial. 

Moreover, $\gamma(a)\downarrow \log P(X_i=x_o)$ as $a\uparrow x_o$: Since $a=\varphi'(\theta_a)/\varphi(\theta_a)$ and $[\varphi'/\varphi]'>0$, there is an inverse map $\theta_a=\theta(a)$ which is differentiable. Then $\gamma'(a)=-\theta(a)+a\theta'(a)+\varphi'(\theta(a))/\varphi(\theta(a))\theta'(a)=-\theta(a)<0$.

When $x_o=\infty$ and $\theta_+=\infty$, by above proof we know $\varphi'/\varphi\to\infty$ as $\theta\to\infty$. The last case is 

**Theorem 2.7.10** Suppose $x_o=\infty$, $\theta_+<\infty$, and $\varphi'(\theta)/\varphi(\theta)\to a_0<\infty$ as $\theta\to\theta_+$. If $a_0\leq a<\infty$, $n^{-1}\log P(S_n\geq na)\to-a\theta_++\log \varphi(\theta_+)$, i.e., $\gamma(a)$ is linear for $a\geq a_0$.

<font color='red'>_proof of Theorem 2.7.10_</font> 

Since $(\log\varphi(\theta))'=\varphi'(\theta)/\varphi(\theta)$, integrating from $0$ to $\theta_+$, we know $\log \varphi(\theta_+)<\infty$. 

$\limsup_{n\rightarrow\infty} LHS\leq RHS$ is already shown before, now we consider the inverse inequality by letting $\lambda=\theta_+$ in $F_\theta$.

- As $\theta\to\theta_+$, $\mu_\theta\to a_0$. Apply MCT for $X^+$ and DCT for $X^-$ we can get $a_0=\mu_{\theta_+}$.

- Use an estimation in **Theorem 2.7.7**, we have 
  $$
  P(S_n\geq na)\geq \int_{na}^{n\nu}e^{-\lambda x}\varphi(\lambda)^ndF_\lambda^{*(n)}(x)\geq \varphi(\lambda)^ne^{-\lambda n\nu}(F_\lambda^{*(n)}(n\nu)-F_\lambda^{*(n)}(na))
  $$
  for $a_0\leq a<\nu=a+3\epsilon$. So
  $$
  \frac{1}{n} \log P(S_n\geq na)\geq \log \varphi(\lambda)-\lambda\nu+\frac{1}{n}\log P(S_n^\lambda\in(na,n\nu])
  $$
  And 
  $$
  \begin{aligned}
  P(S_n^\lambda\in(na,n\nu])&\geq P(S_{n-1}^\lambda\in((a_0-\epsilon)n,(a_0+\epsilon)n])P(X_n^\lambda\in((a-a_0+\epsilon)n,(a-a_0+2\epsilon)n))
  \\&\geq \frac{1}{2}P(X_n^\lambda\in((a-a_0+\epsilon)n,(a-a_0+2\epsilon)n))
  \end{aligned}
  $$
  For large n by WLLN. 

- And $\limsup_{n\rightarrow\infty}\frac{1}{n}\log P(X_n^\lambda\in((a-a_0+\epsilon)n,(a-a_0+2\epsilon)n))=0$. Actually, it must be nonpositive; if it's negative, there must be some $\eta$ s.t. $Ee^{\eta X^\lambda}<\infty$. But $Ee^{\eta X^\lambda}=Ee^{\eta+\lambda}X$, and we have assumed $\lambda=\theta_+$. This leads to contradiction.

- Let $\epsilon\to 0$, we can conclude $\liminf_{n\rightarrow\infty} \frac{1}{n}\log P(S_n\geq na)\geq \log \varphi(\theta_+)-\theta_+ a$. This completes our proof. 

_Remark_ This implies the hypothesis $\varphi(\theta)<\infty$ for some $\theta>0$ is necessary for exponential decay. Otherwise we have:

**Exercise 2.7.5** Suppose $EX_i=0$ and $E\exp(\theta X_i)=\infty$ for all $\theta>0$. Then $\frac{1}{n}\log P(S_n\geq na)\to 0$ for all $a>0$.

<font color='red'>_proof of Excercise 2.7.5_</font> 

Otherwise there is some $a>0$ such that $\frac{1}{n}\log P(S_n\geq na)\leq c<0$ for all $n$. Notice
$$
\sum_{n=1}^\infty P(e^{\theta X_i}\geq n)=\sum_{n=1}^\infty P(X_i\geq \frac{1}{\theta}\log n)\leq \sum_{n=1}^\infty P(S_n\geq n\frac{1}{\theta}\log n)
$$
Since LHS is decreasing as $a$ increases, when $n$ is large enough, i.e., $\frac{1}{\theta}\log n>a$, $P(S_n\geq n\frac{1}{\theta}\log n)\leq e^{cn}$. RHS is summable, so $\sum_{n=1}^\infty P(e^{\theta X_i}\geq n)$ is summable. This indicates $E e^{\theta X_i}<\infty$, which is a contradiction.

