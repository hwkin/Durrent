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

**Example 2.2.7 Coupon collector's problem** Let $X_1,...$ be i.i.d. uniform on ${1,2,...,n}$. 

 
