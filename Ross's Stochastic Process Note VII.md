## Chapter 8 Brownian Motion and other Markov Processes

### 8.1 Introduction and preliminaries

_Origin_ Consider a 1-d SRW. Now we speed up this by taking smaller steps in smaller time intervals, i.e., in $\Delta t$ the walker moves $\Delta x$. Let $X(t)$ be the position of the walker, $X(t)=\Delta x(\sum_{i=1}^{[t/\Delta t]}X_i)$.

In this case, $EX(t)=0$ and $var(X(t))=(\Delta x)^2[t/\Delta t]$. So to make the limit nontrivial, let $\Delta x=c\sqrt{\Delta t}$. As $\Delta t\to 0$

- $EX(t)=0$ and $var (X(t))\to c^2 t$. By CLT, $X(t)\to_d \mathcal N(0,c^2 t)$.
- $X(t)$ has independent and stationary increments.

This leads to the formal definition of Brownian motion.

**Definition** A stochastic process $(X(t))$ is a **Brownian motion** if (i) $X(0)=0$ (ii) $X(t)$ has stationary and independent increments (iii) For $t>0$, $X(t)\sim \mathcal N(0,c^2 t)$. When $c=1$, the process is called **standard Brownian motion**. 

_Remark_ Since when $X(t)\sim \mathcal N (0,c^2 t)$, $X(t)/c\sim\mathcal N(0,t)$, we will assume $c=1$.

1. **Continuity property**

   We will list some continuity properties without proof.

   - The path of BM is cts.
   - For $0<\alpha<1/2$, BM paths are a.s. $\alpha$-Holder cts on $[0,T],T>0$. But BM is not $1/2$-Holder cts on compact intervals.
   - As a corollary, BM paths are nowhere differentiable a.s..

2. **distribution**

   From independent increments, we know
   $$
   P(X(t+s)\le \alpha\mid X(s)=x,X(u),0\le u<s)=P(X(t+s)-X(s)\le a-x\mid X(s)=x,X(u),0\le u<s)=P(X(t+s)-X(s)\le a-x)=P(X(t+s)\le a\mid X(s)=x)
   $$
   i.e., the process is Markov.

   From stationary increments we have $X(t+s)-X(t)=_d X(t-s)\sim \mathcal N(0,s)$.

   So the density is given by ($t_1<...<t_n$)
   $$
   \begin{aligned}
   f_t(x)&=\frac{1}{\sqrt{2\pi t}}e^{-x^2/2t}\\
   f_{t_1,...,t_n}(x_1,...,x_n)&=f_{t_1}(x_1)f_{t_2-t_1}(x_2-x_1)...f_{t_n-t_{n-1}}(x_n-x_{n-1})
   \end{aligned}
   $$
   Moreover we have 

   - $EX(t)=0\forall t$, $var X(t)=t\forall t$

   - For $s<t$, 
     $$
     cov(X(s),X(t))=cov(X(s),X(t)-X(s)+X(s))=cov(X(s),X(t)-X(s))+cov(X(s),X(s))=var(X(s))=s
     $$
     i.e. $cov(X(s),X(t))=s\wedge t$.

   From the form of $f_{t_1,...,t_n}(x_1,...,x_n)$ we know $X(t_1),...,X(t_n)$ is multivariate normal. This leads to another definition:

   **Definition** A stochastic process $X(t)$ is called a **Gaussian process** if for all $k$, $t_1<...<t_k$, $X(t_1),...,X(t_k)$ has a multivariate normal distribution.

   **Another definition of Brownian motion** Since a multivariate normal distribution is completely determined by the marginal means and covariances, a BM can also be defined as a Gaussian process with $EX(t)=0$ and $cov(X(s),X(t))=s\wedge t$.

3. **conditional distribution** 

   When we look backward along timeline, we have, for $s<t$, 
   $$
   f_{s\mid X(t)=y}(x)=\frac{f_s(x)f_{t-s}(y-x)}{f_t(y)}=K\exp(-\frac{t(x-ys/t)^2}{2s(t-s)})
   $$
   Let $\alpha=s/t<1$. Given $X(t)$, $X(s)\sim\mathcal N(\alpha X(s),\alpha(1-\alpha)t)$. Interestingly the variance doesn't depend on $X(t)$.

   Moreover, conditioned that $X(t)=y$, the process on $[0,t]$ has density ($s_1<...<s_n<t$)
   $$
   f_{s_1,...,s_n\mid X(t)=y}(x_1,...,x_n)=\frac{f_{s_1}(x_1)f_{s_2-s_1}(x_2-x_1)...f_{t-s_n}(y-x_n)}{f_t(y)}
   $$
   From the form of the density we know $X(s),0\le s\le t\mid X(t)$ is a Gaussian process.

   For a special case, consider a **Brownian bridge** $X(t)$ which is a BM on $[0,1]$ conditioned that $X(1)=0$. we have 

   - $EX(t)=0\forall t$, $var(X(t))=t(1-t)$.

   - For $s<t$,
     $$
     cov(X(s),X(t))=EX(s)X(t)=E[E[X(s)X(t)\mid X(t)]]=E[[\frac{s}{t}X(t)^2\mid X(t)]]=s(1-t)
     $$
     So $cov(X(s),X(t))=s\wedge t-st$. One can find this is just the Green function of $\begin{cases}\Delta u=0,x\in[0,1] \\u(0)=u(1)=0\end{cases}$. 

   This leads to 

   **Another definition of Brownian bridge** A Brownian bridge is a Gaussian process on $[0,1]$ where $EX(s)=0$ and $cov(X(s),X(t))=s\wedge t-st$.

   **Another definition of Brownian bridge** If $X(t)$ is a BM, then $Z(t):=X(t)-tX(1)$ is a Brownian bridge on $[0,1]$.

   _proof_ For $s_1<...<s_n<t$, since $X(s_1),X(s_2)-X(s_1),...,X(1)-X(s_n),X(1)$ are independent normal r.v.'s, by linear transformation we know $Z(s_1),...,Z(s_n)$ are Gaussian. So the process is Gaussian.

   Moreover, one can compute $EZ(t)=0$ and $cov(Z(s),Z(t))=s\wedge t-st$. So the proof is complete.

4. **Scaling** 

   - Let $W(t)=X(a^2t)/a$. $W(t)$ is also a BM.

     _proof_ First $W(t)$ is a Gaussian process. Moreover,
     $$
     \begin{aligned}
     EW(t)&=EX(a^2 t)/a=0\\
     cov(W(t),W(s))&=cov(X(a^2 t),X(a^2 s))/a^2=s\wedge t
     \end{aligned}
     $$
     So $W(t)$ is a BM.

   - Let $Y(t)=tX(1/t)$. $Y(t)$ is also a BM.

     _proof_ First $Y(t)$ is a Gaussian process. Moreover,
     $$
     \begin{aligned}
     EY(t)&=EtX(1/t)=0\\
     cov(Y(t),Y(s))&=ts\ cov(X(1/t),X(1/s))=ts(1/t\wedge 1/s)=s\wedge t
     \end{aligned}
     $$
     So $Y(t)$ is also a BM.

   - Let $Y(t)=X(t-s)-X(t),0\le s\le t$ be the time-reversed process. $Y(t)$ is also a BM.

     _proof_  It's of course Gaussian, and
     $$
     \begin{aligned}
     EX(t-s)-X(t)&=EX(t-s)-EX(t)=0\\
     cov(X(t-s)-X(t),X(t-r)-X(t))&=cov(X(t-s),X(t-r))-cov(X(t-s),X(t))\\
     &\ \ \ -cov(X(t),X(t-r))+cov(X(t),X(t))\\
     &=(t-s)\wedge (t-r)-(t-s)-(t-r)+t\\
     &=s\wedge r
     \end{aligned}
     $$
     Or recall SRW is also time-reversible. 

**Application of Brownian bridge** 

**Definition** Let $X_i$ i.i.d. $\sim U(0,1)$ and $N_n(s)=\sum_{i=1}^{n} 1_{X_i\le s}$. Then $F_n(s)=N_n(s)/n$ is called the **empirical distribution function**. 

Now we investigate its limit behavior.

- By SLLN, $\lim_{n \to \infty} F_n(s)=s$ a.s.. Moreover $\sup_{0<s<1} |F_n(s)-s|\to 0$.
- By CLT, $\alpha_n(s):=\sqrt{n}(F_n(s)-s)\to_d \mathcal N(0, s(1-s))$.
- For $s<t$, let $Y_i=(1_{X_i\le s},1_{X_i\le t})$, then $Y_i$ are i.i.d. with $EY_i=(0,0)$ and $\Sigma:=cov(Y_i)=\begin{pmatrix} s(1-s)& s(1-t)\\s(1-t)&t(1-t)\end{pmatrix}$. so $\frac{1}{\sqrt{n}}\sum_{i=1}^{n} Y_i=(\alpha_n(s),\alpha_n(t))\to_d \mathcal N(\vec 0,\Sigma)$.

So the limit is a Brownian bridge.

Moreover, if $X_i$ are i.i.d. $\sim F$ which is cts, $F(X_i)$ are i.i.d. $\sim U(0,1)$. So we can also construct this.

### 8.2 Hitting times, maximum variable and arc sine laws

1. **Hitting times** 

   We care about the distribution of the hitting time of $a$, i.e., $T_a:=\inf\{t: X(t)\ge a\}$ for $a>0$. To compute $P(T_a\le t)$, consider $X(t)\ge a$,
   $$
   \underbrace{P(X(t)\ge a)}_{X(t)\sim \mathcal N(0,t)}=P(X(t)\ge a\mid T_a\le t)P(T_a\le t)+\underbrace{P(X(t)\ge a\mid T_a>t)}_{=0}P(T_a>t)
   $$
   Conditioned that $T_a\le t$, starting from $T_a$, by symmetry we have $P(X(t)\ge a\mid T_a\le t)=1/2$. Together we have 
   $$
   P(T_a\le t)=2\int_a^\infty\frac{1}{\sqrt{2\pi t}}e^{-x^2/2t}dx=\frac{2}{\sqrt{2\pi}}\int_{a/\sqrt{t}}^\infty e^{-y^2/2}dy
   $$
   By computation we have $P(T_a<\infty)=1$ but $ET_a=\infty$. This is exactly the case for SRW.

2. **Maximum value** 

   The distribution of maximum value attained in $[0,t]$ is given by 
   $$
   P(\max_{0\le s\le t}X(s)\ge a)=P(T_a\le t)=2P(X(t)\ge a)
   $$
   since the path of BM is cts a.s..

3. **Zero times** 

   For the probability that $X(t)$ ever hits $0$ during $[t_1,t_2]$, one can consider $X(t_1)$,
   $$
   P(X(t)=0\exists t_1\le t\le t_2)=\frac{1}{\sqrt{2\pi t_1}}\int_\mathbb R P(X(t)=0\exists t_1\le t\le t_2\mid X(t_1)=x)e^{-x^2/2t_1}dx
   $$
   We have 
   $$
   P(X(t)=0\exists t_1\le t\le t_2\mid X(t_1)=x)=P(X(t)=-x\exists 0\le t\le t_2-t_1)=P(T_{|x|}\le t_2-t_1)
   $$
   which yields (by symmetry)
   $$
   \begin{aligned}
   P(X(t)=0\exists t_1\le t\le t_2)&=2\frac{1}{\sqrt{2\pi t_1}}\int_0^{\infty}\int_x^\infty \frac{1}{\sqrt{2\pi(t_2-t_1)}}e^{-y^2/2(t_2-t_1)}dye^{-x^2/2t_1}dx\\&=1-\frac{2}{\pi}\arcsin\sqrt{t_1/t_2}\end{aligned}
   $$
   Push $t_2\to\infty$, we have $P(X(t)=0\exists t\ge t_1)=1$.

   _Remark_ Recall $tX(1/t)$ is also a BM, then by this, let $T=\inf\{t>0 X(t)=0 \}$, then $T=0$ a.s..

4. **Positive time** 

   Let $A(t)=|\{s\in [0,t]: X(t)>0 \}|$. Then $P(A(t)/t\le x)=\frac{2}{\pi}\arcsin \sqrt{x}$.

_Remark_ For SRW we have established the distribution of zero times and positive time, whose limit is exactly arc sine laws.

### 8.3 Variations on Brownian Motion

#### 8.3.1 BM absorbed at a value

Consider a BM absorbed at $x>0$: $Z(t):=X(t\wedge T_x)$ where $T_x=\inf\{t: X(t)=x \}$ is the hitting time. First, we introduce a proposition which is quite useful.

**Proposition reflection principle** Let $X(t)$ be a BM and $T_x$ is hitting time of $x$. Consider the process which is reflected when it hits $x$ for the first time, i.e., $Z(t)=\begin{cases} X(t)&t<T_x\\2x-X(t)&t\ge T_x\end{cases}$. Then $Z(t)=_d X(t)$.

<font color='red'>_proof_</font> If $t<T_x$, it holds; if $t\ge T_x$, conditioned on $T_x$, since $-Y(t)=_d Y(t)$ for any BM $Y(t)$, we have $x-X(t-T_x)=_d x+X(t-T_x)$, i.e., $Z(t)=_d X(t)$. 

By this, for $y<x$, conditioned on $T_x$,
$$
\begin{aligned}
P(Z(t)\le y)&=P(X(t)\le y, T_x>t)\\
&=P(X(t)\le y)-P(X(t)\le y,T_x\le t)\\
&=P(X(t)\le y)-P(X(t)\ge 2x-y, T_x\le t)\text{ (reflection principle) }\\
&=P(X(t)\le y)-P(X(t)\ge 2x-y)\text{ since }2x-y>x\\
&=P(2x-y\le X(t)\le y)
\end{aligned}
$$

#### 8.3.2 BM reflected at the origin

Consider $|X(t)|$, which can be seen as reflected as it touches the origin. The distribution is 
$$
P(Z(t)\le y)=P(-y\le X(t)\le y)
$$
with $EZ(t)=\sqrt{2t/\pi}$ and $var Z(t)=(1-2/\pi)t$.

#### 8.3.3 Geometric BM

Consider $Y(t):=\exp(X(t))$ which is called **geometric Brownian motion**. This can be applied in the cases when the percentage of changes is a BM,e.g., if $X_i>0$ are i.i.d., $Y_n=\prod_{i=1}^{n} X_i$ may have a limit as a geometric BM under appropriate normalization.

Since we have already known $E\exp(sX(t))=\exp(ts^2/2)$ (moment generating function), we have $EY(t)=\exp(t/2)$ and $var(Y(t))=e^{2t}-e^t$.

**Example 8.3(A)** 

_Setting_ Suppose one has the option 期权 of purchasing, after a fixed time $T$, one unit of clock at a fixed price $K$. Suppose now the price is $y$ and the price is a geometric BM. Define the worth of the strategy to be $Y(T)-K\vee 0$. Then the mean is given by
$$
E[\max\{Y(T)-K,0 \}]=\int_0^\infty P(Y(T)-K>a)da=\int_0^\infty P(ye^{X(t)}>a+K)da=\int_0^\infty P(X(T)>\log \frac{K+a}{y})da
$$

#### 8.3.4 Integrated BM

Consider $Z(t)=\int_0^t X(s)ds$. This can be applied in the cases when the rate of change is a BM.

- $Z(t)$ is a Gaussian process: One can approximate the integral by sum of independent normal r.v.'s.

- $$
  \begin{aligned}
  EZ(t)&=E\int_0^t X(s)ds=_\text{Fubini}\int_0^t EX(s)ds=0\\
  cov(Z(s),Z(t))&=EZ(s)Z(t)=E\int_0^s X(y)dy\int_0^t X(u)du=_\text{Fubini}\int_0^s\int_0^t EX(y)X(u)dydu\\=&\int_0^s\int_0^t \min(y,u)dydu=s^2(t/2-s/6), s\le t
  \end{aligned}
  $$

- Notice $Z(t)$ is not Markov since one needs $X(t)$ for future increments. So $(Z(t),X(t))$ is Markov. Interestingly, we can determine the distribution of $Z(t),X(t)$. First, $(Z(t),X(t))$ are normal; next, $EZ(t)=EX(t)=0$; moreover,
  $$
  \begin{aligned}
  cov(Z(t),X(t))&=\lim_{h \to 0}cov(Z(t),\frac{Z(t)-Z(t-h)}{h})\\&=\lim_{h \to 0} \frac{1}{h}(cov(Z(t),Z(t))-cov(Z(t),Z(t-h)))\\&=\lim_{h \to 0}\frac{1}{h}(t^3/3-(t-h)^2(t/3+h/6))=t^2/2
  \end{aligned}
  $$

Consider $\frac{d}{dt}W(t)=X(t)W(t)$, which yields $W(t)=\exp(Z(t))$, which can be applied in the cases when the percent rate of change is a BM. We have $EW(t)=\exp(t^6/6)$.

### 8.4 BM with drift

**Definition** A stochastic process $X(t)$ is a BM with drift $\mu$ if (i) $X(0)=0$ (ii) $X(t)$ has stationary and independent increments (iii) $X(t)\sim \mathcal N(\mu t,t)$. Actually, $X(t)=B(t)+\mu(t)$ where $B(t)$ is a SBM.

_Origin_ Consider a 1-d simple random walk with $EX_i=\mu$. If one speed up the process by moving $\Delta x$ in $\Delta t$ for a step, then when he takes the limit as $\Delta x=\sqrt{\Delta t}\to 0$, he can attain $X(t)$.

**hitting probability** 

Fix $A$ and $B$, for $-B<x<A$, we wonder $P(x)=P(T_A<T_{-B}\mid X(0)=x)$. 

Consider the first small step, let $Y=X(h)-X(0)$. We have $P(x)=EP(x+Y)+o(h)$ where $o(h)$ represents the probability that $T_A\wedge T_{-B}<h$. 

One can derive an ODE from this. Assume $P(x)$ is analytic, we have 
$$
P(x)=P(x)+P'(x)EY+\frac{P''(x)}{2}EY^2+o(h)\Rightarrow P'(x)\mu+\frac{P''(x)}{2}=0
$$
> $Y=\mu h+X$, where $X\sim \mathcal N(0,h)$. For $X$, $EX=0, EX^2=h,EX^k=o(h),k\ge 3$ from the ch.f.. For $Y$, $EY=\mu h, EY^2=\mu^2h^2+h$, $EY^k=o(h),k\ge 3$ by expanding.

along with BC $P(A)=1$, $P(-B)=0$, the solution is given by 
$$
P(x)=\frac{e^{2\mu B}-e^{-2\mu x}}{e^{2\mu B}-e^{-2\mu A}}
$$
_Remark_ When $\mu<0$, push $B\to\infty$ we have $P(X(t)=A\exists t)=e^{2\mu A}$. So $\sup_t X(t)\sim Exp(-2\mu)$.

_Remark_ When $\mu=0$, we have for a SBM, $P(T_A<T_{-B})=B/(A+B)$.

> [!Tip]
>
> Recall the gambler's ruin problem: If $P(X_i=1)=1-P(X_i=-1)=p$, then for $S_n$, let $T_x=\min\{n: S_n=x\}$, we have for $A,B\in\mathbb Z_+$,
> $$
> P(T_A\le T_{-B})=\frac{1-(q/p)^B}{1-(q/p)^{A+B}}
> $$
> When taking limit, since $\mu=\Delta x(2p-1)$, we have for $A,B\in\mathbb R_+$,
> $$
> P(T_A\le T_{-B})=\lim_{\Delta x\to 0}\frac{1-(q/p)^{B/\Delta x}}{1-(q/p)^{(A+B)/\Delta x}}
> $$
> Since 
> $$
> \lim_{\Delta x\to 0}(q/p)^{1/\Delta x}=\lim_{\Delta x\to 0}(\frac{1-\mu\Delta x}{1+\mu\Delta x})^{1/\Delta x}=e^{-2\mu}
> $$
> we have 
> $$
> P(T_A\le T_{-B})=\frac{1-e^{-2\mu B}}{1-e^{-2\mu(A+B)}}
> $$
> which agrees our result.

**Example 8.4(A)** _Setting_ Suppose one have the option of buying, at some time in the future, one unit of a stock at a fixed price $A$. Suppose the market price is $X(t)$, a BM with drift $-d$ where $d>0$. The question is: when should we exercise our option?

Consider the policy that exercises the option when the market price is $x$. Then the expected gain is $P(T_x<\infty)(x-A)=e^{-2dx}(x-A)$. When $x=A+(2d)^{-1}$, the mean takes the maximum.

**Example 8.4(B)** 

_Setting_ Suppose two individuals that for a stake 筹码 are playing some game that eventually ends with one of the players declared the winner. Initially one of the players is designated as the "doubling player", i.e., at any time he has the option of doubling the stakes. When he exercises this option, the other player can (i) quit and pay the present stake to him (ii) continue to play with doubled stake, and become the doubling player, i.e., they switched the option. 

The game is to watch a BM with $X(0)=1/2$. If $T_1<T_0$, player 1 wins, vice versa. The objective of each player is to maximize his expected return. Suppose each player plays optimally, i.e., a player can announce his strategy and another player can't do better even knowing this.

_Optimal strategy_ When player 1 is the doubled player, he should double iff $X(t)\ge p^*$ and player 2 should accept the double iff $X(t)\le p^{**}$.

_Lemma 1_ $p^*\le p^{**}$.

_proof_ For any $p>p^{**}$, player 2 will quit immediately $X(t)=p$ and player 1 doubles. Since player 1 can guarantee himself an expected gain of the present stake by doubling, and player 2 can guarantee himself that player 1 will not gain more by quitting, it follows that player 1 must double. So $p>p^{*}$, and $p^*\le p^{**}$. 

_Lemma 2_ $p^*=p^{**}$.

_proof_ Suppose $p^*<p^{**}$. It turns out that player 1 had better wait until it hits $0$ or $p^{**}$. If it hits $p^{**}$ first, he can double and player 2 will accept, so the result will be the same as original strategy. If it hits $0$ first, if he didn't wait he loses doubled stake while otherwise he only loses original stake.

So when player 1 has the option, his optimal strategy is to double at t iff $X(t)\le p^*$ and player 2's optimal strategy is to accept double at $t$ iff $X(t)\ge p^*$. To pick appropriate $p^*$, notice at $p^*$ if player 1 doubles, whether player 2 choose to accept shouldn't make any difference by continuity.

Suppose now the stake is $1$ unit, $X(t)=p^*$, and player 1 doubles.

- If player 2 quit, player 1 will gain $1$.

- If player 2 accept, he will have the double option and will double when $X(t)$ hits $1-p^*$. If it hits $1$ first, he will lose $2$ and player 1 will gain 2; if it hits $1-p^*$ first, player 2 will double the stakes to $4$. Since it's indifferent for player $1$ to quit or accept, suppose he quits and player $1$ loses 2. 

- Together we have 
  $$
  1=2\times\frac{p^*-(1-p^*)}{1-(1-p^*)}+(-2)\times\frac{1-p^*}{1-(1-p^*)}
  $$
  which gives $p^*=4/5$.

**Example 8.4(C)**

_Setting_ Suppose the production process changes its state in accordance with a BM with drift $\mu>0$. When it hits $B$, the process breaks down and a cost $R$ must be paid to return the process back to state $0$. Before it hits $B$, a cost $C$ can be paid to repair the process, whose result is that, if the state is $x$, the process goes to $0$ with probability $\alpha_x$ (i.e., succeed) and goes to $B$ with probability $1-\alpha_x$ (i.e., fail).

_Optimal policy_ We only consider the strategy to fix when $0<x<B$, and pick appropriate $x$ to minimize the long-run cost rate. For these policies, the returns to $0$ constitute renewals. By reward renewal theorem, it's just 
$$
\frac{E[\text{cost of a cycle}]}{E[\text{length of a cycle}]}=\frac{C+R(1-\alpha_x)}{E[\text{time to reach }x]}
$$
Let $f(x)=E[\text{time to reach }x]$. By taking a small step we have, suppose $Y=X(h)-X(0)$,
$$
f(x)=h+E[f(x-Y)]+o(h)
$$
Though we can expand $f$ and get an ODE with BC, it's better to notice $f$ satisfies $f(x+y)=f(x)+f(y)$, since to hit $x+y$ it must hits $x$ before hitting $y$ starting from $x$. By Cauchy's equation, along with the equation and $f(0)=0$, we know $f(x)=x/\mu$. 

So the rate is $\frac{\mu(C+R(1-\alpha_x))}{x}$. Meanwhile, the policy of never repairing has cost $R\mu/B$.

**hitting time**

Now we consider the distribution of $T_x,x>0$ for a BM with drift $\mu>0$ by computing $Ee^{-\theta T_x}$.

**Proposition 8.4.1** $Ee^{-\theta T_x}=\exp(-x(\sqrt{\mu^2+2\theta}-\mu))$ when $\mu>0$.

<font color='red'>_proof of Proposition 8.4.1_</font> Let $f(x)=Ee^{-\theta T_x}$.

- As that in **Example 8.4(c)**, $f(x+y)=f(x)f(y)$. By Cauchy equation, $f(x)=e^{-cx}$.

- To determine $c$, we need an ODE. Conditioned on $Y=X(h)-X(0)$ when $h\ll 1$, 
  $$
  f(x)=Ee^{-\theta(h+T_{x-Y})}+o(h)=e^{-\theta h}Ef(x-Y)+o(h)=e^{-\theta h}E[f(x)-Yf'(x)+\frac{Y^2}{2}f''(x)+o(h)]+o(h)=(1-\theta h+o(h))(f(x)-\mu h f'(x)+\frac{h}{2} f''(x))+o(h)
  $$
  which yields $\theta f(x)=-\mu f'(x)+\frac{1}{2}f''(x)$. This gives $c=\sqrt{\mu^2+2\theta}-\mu$.

**limit average value of maximum variable** 

**Proposition 8.4.2** $\lim_{t \to \infty}\frac{\max_{s\in [0,t]}X(s)}{t}=\mu$.

<font color='red'>_proof of Proposition 8.4.2_</font> By stationary and independent increments, we can consider the first hit of $n$ as $n$th renewal. Let $N(t)$ be the number of renewals by $t$, we have 
$$
N(t)\le \max_{s\in[0,t]}X(s)\le N(t)+1
$$
Notice the interarrivals $T_n-T_{n-1}=_d T_1$ has mean $1/\mu$. By SLLN of renewal, $N(t)/t\to\mu$.

#### 8.4.1 Using martingales to analyze BM

**Proposition 8.4.3** Let $B(t)$ be a SBM. Then $Y(t)$ is a martingale with 

(a) $Y(t)=B(t)$ (b) $Y(t)=B^2(t)-t$ (c) $Y(t)=\exp(cB(t)-c^2t/2)$.

**hitting probability** 

For $X(t)$ a BM with drift $\mu$, to compute $P(T_A<T_{-B})$, use the martingale $Y(t)=\exp(cX(t)-c\mu t-c^2 t/2)$. Pick $c=-2\mu$, $Y(t)=\exp(-2\mu X(t))$ is a martingale.

Use optional stopping theorem on $Y(t)$ and $T_A\wedge T_{-B}$,
$$
\begin{aligned}
1=EY(0)=EY(T_A\wedge T_{-B})=\exp(-2\mu A)P(T_A<T_{-B})+\exp(2\mu B)(1-P(T_A<T_{-B}))
\end{aligned}
$$
which yields $P_A=\frac{e^{2\mu B}-1}{e^{2\mu B}-e^{-2\mu A}}$.

**hitting time** 

Use the martingale $Y(t)=X(t)-\mu t$, 
$$
0=EY(0)=EY(t)=EX(T)-\mu T=AP_A-B(1-P_A)-\mu ET
$$
which yields $ET=\frac{Ae^{2\mu B}+Be^{-2\mu A}-A-B}{\mu[e^{2\mu B}-e^{-2\mu A}]}$.

### 8.5 Backward and forward diffusion equations

_Recall_ The derivation of Kolmogorov's forward and backward is to condition on $X(t-h)$ and $X(h)$ respectively when $h=o(1)$.

Now use the same technique for BM with drift to derivate differential equations about the density. Let $p(x,t,y)=f_{X(t)\mid X(0)=y}(x)$, for backward, 
$$
\begin{aligned}
p(x,t,y)&=Ep_{X(t)\mid X(0)=y,X(h)}(x)=Ep(x,t-h,X(h))\\
&=Ep(x,t,y)-h\partial_tp(x,t,y)+(X(h)-y)\partial_y p(x,t,y)+\frac{(X(h)-y)^2}{2}\partial_{yy} p(x,t,y)+o(h)\\
&=p(x,t,y)-h\partial_t p(x,t,y)+\mu h \partial_y p(x,t,y)+\frac{h}{2}\partial_{yy} p(x,t,y)+o(h)\\
\Rightarrow \partial_t p(x,t,y)&=\mu \partial_y p(x,t,y)+\frac{1}{2}\partial_{yy} p(x,t,y)
\end{aligned}
$$
for forward, 
$$
\begin{aligned}
p(x,t,y)&=Ep_{X(t)\mid X(0)=y,X(t-h)}(x)=Ef_W(x-X(t-h)),W\sim \mathcal N(\mu h,h)\\
&=\int f_W(x-a)p(a,t-h,y)da\\
&=\int f_W(x-a)[p(x,t,y)+(a-x)\partial_x p(x,t,y)-h\partial_t p(x,t,y)+\frac{(a-x)^2}{2}\partial_{xx}p(x,t,y)+...]da\\
&=p(x,t,y)-\mu h\partial_x p(x,t,y)-h\partial_t p(x,t,y)+\frac{h}{2}\partial_{xx}p(x,t,y)+o(h)\\
\Rightarrow \frac{1}{2}\partial_{xx}p(x,t,y)&=\mu \partial_x p(x,t,y)+\partial_t p(x,t,y)
\end{aligned}
$$

***

Exercises

8.4 Let $Z(t)$ be a BM bridge, the $X(t)=(t+1)Z(t/(t+1))$ is a BM.

_proof_ $X(t)$ is Gaussian. Then 
$$
\begin{aligned}
EX(t)&=0\\
cov(X(t),X(s))&=(t+1)(s+1)cov(Z(t/(t+1)),Z(s/(s+1)))=(t+1)(s+1)[t/(t+1)\wedge s/(s+1)-ts/(t+1)(s+1)]=s\wedge t-st
\end{aligned}
$$
So $X(t)$ is a BM.

8.7 Find the distribution of $\max_{0\le s\le t}X(s)-X(t)$.

_Solution_ Consider the reversed process $X(t)-X(s)=_d X(s),0\le s\le t$.

By this, $\max_{0\le s\le t}X(s)-X(t)=_d \max_{0\le s\le t}X(s)$.

8.9 Let $M(t)=\max_{0\le s\le t}X(s)$, then $P(M(t)>a\mid M(t)=X(t))=e^{-a^2/2t}$.

_Solution_ Also consider the reversed process $X(t)-X(s):=Y(s)$. Then $M(t)=X(t)$ corresponds to the event that $Y(s)\ge 0$, and the probability should be $\lim_{b \uparrow 0} P(X(t)\ge a\mid T_b>t)$.

We have known $P(T_b>t)=1-2P(X(t)>|b|)$. For $P(X(t)\ge a, T_b>t)$, we have 
$$
P(X(t)\ge a,T_b>t)=P(X(t)\ge a)-P(X(t)\ge a,T_b\le t)=P(X(t)\ge a)-P(X(t)\le 2b-a)
$$
Which yields
$$
\lim_{b \uparrow 0} P(X(t)\ge a\mid T_b>t)=\lim_{b\uparrow 0}\frac{P(X(t)\ge a)-P(X(t)\le 2b-a)}{1-2P(X(t)\ge |b|)}=_\text{L'Hospital}\lim_{b\uparrow 0}\frac{(2\pi t)^{-1/2}e^{-(2b-a)^2/2t}}{(2\pi t)^{-1/2}e^{-b^2/2t}}=e^{-a^2/2t}
$$
8.14 Compute $P(T_1<T_{-1}<T_2)$ for a BM.

_Solution_ Since $T_1<T_2$, we know $P(T_1<T_{-1},T_2)=P(T_1<T_{-1})=1/2$. As it reaches $1$, $P(T_{-1}<T_2)=1/3$. So the probability is $1/6$.

