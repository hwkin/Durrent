This is a note on Lectures on the Ising and Potts models on the hypercubic lattice.

### 1.1.2 Phase transition in Ising, Potts and $O(n)$ models

_Solution to Exercise 1.1_

For Ising model on $\mathbb Z$, WLOG pick $\mathsf b=1$. For ease of notation, let $G_n=[-n,n]\cap \mathbb Z$, $\Sigma=\{\sigma:G_n\to\pm 1\mid \sigma=\mathsf b\text{ on }\partial G_n \}$, $\Sigma_1=\{\sigma:G_n\to\pm 1\mid \sigma=\mathsf b\text{ on }\partial G_n,\ \sigma_0=\mathsf b \}$, $\Sigma_2=\Sigma\backslash\Sigma_1$. 

To compute, we assign weight $\sigma_x\sigma_y$ to edge $xy$. Then $\Sigma$ consists of configurations with even number of edges carrying negative weight, $\Sigma_1$ consists of configurations with even number of edges carrying negative weight on both side of $0$, and $\Sigma_2$ consists of configurations with even number of edges carrying positive weight on both side of $0$. This yields
$$
\begin{aligned}
\mu_\beta^\mathsf b[\sigma_0\cdot \mathsf b]&=\lim_{n \to \infty}\mu_{G_n,\beta}^\mathsf b[\sigma_0\cdot\mathsf b]
\\&=\lim_{n \to \infty}\frac{\int_\Sigma\sigma_0\cdot\mathsf b\ \exp[-\beta H_{G_n}^\mathsf f(\sigma)]d\sigma}{\int_\Sigma\exp[-\beta H_{G_n}^\mathsf f(\sigma)]d\sigma}
\\&=\lim_{n \to \infty}\frac{\int_{\Sigma_1}\exp[-\beta H_{G_n}^\mathsf f(\sigma)]d\sigma-\int_{\Sigma_2}\exp[-\beta H_{G_n}^\mathsf f(\sigma)]d\sigma}{\int_\Sigma\exp[-\beta H_{G_n}^\mathsf f(\sigma)]d\sigma}
\\&=\lim_{n \to \infty}\frac{\big(\sum_{k=0}^{[n/2]}\binom{n}{2k}\exp[\beta(n-4k)]\big)^2-\big(\sum_{k=0}^{[(n-1)/2]}\binom{n}{2k+1}\exp[\beta(n-4k-2)] \big)^2}{\sum_{k=0}^n\binom{2n}{2k}\exp[\beta(2n-4k) ]}
\end{aligned}
$$
From the identity 
$$
\sum_{k=0}^n\binom{2n}{2k}p^{2k}=\frac{(1+p)^{2n}+(1-p)^{2n}}{2}
$$
The limit term is exactly
$$
\begin{aligned}
RHS&=\lim_{n \to \infty}\frac{e^{2\beta n}((1+e^{-2\beta})^n+(1-e^{-2\beta})^n)^2/4-e^{2\beta n}((1+e^{-2\beta})^n-(1-e^{-2\beta})^n)^2/4}{e^{2\beta n}((1+e^{-2\beta})^{2n}-(1-e^{-2\beta})^{2n})/2}
\\&=\lim_{n \to \infty}\frac{2(1+p)^n(1-p)^n}{(1+p)^{2n}-(1-p)^{2n}}, p=e^{-2\beta}
\\&=0
\end{aligned}
$$
So $\beta_c=+\infty$.

Again, 
$$
\begin{aligned}
\lim_{\|x\|\to\infty}\mu_\beta^\mathsf f [\sigma_0\cdot\sigma_x]&=\lim_{x \to \infty}\lim_{n \to \infty}\mu_{G_n,\beta}^\mathsf f[\sigma_0\cdot \sigma_x]
\\&=\lim_{x\to\infty}\frac{\sum_{k=0}^{x/2} \binom{x}{2k}\exp[\beta(x-4k)]-\sum_{k=0}^{(x-1)/2}\binom{x}{2k+1}\exp[\beta(x-4k-2)]}{\sum_{k=0}^{x}\binom{x}{k} \exp[\beta(x-2k)]}
\\&=\lim_{x \to \infty}\frac{e^{\beta x}((1+e^{-2\beta})^x+(1-e^{-2\beta})^x)/2-e^{\beta x}((1+e^{-2\beta})^x-(1-e^{-2\beta})^x)/2}{e^{\beta x}(1+e^{-2\beta})^x}
\\&=\lim_{x \to \infty}\frac{(1-p)^x}{(1+p)^x}, p=e^{-2\beta}
\\&=0
\end{aligned}
$$
So $\beta_c^{lro}=+\infty$.

Moreover, from the identity above, pick $c_\beta\le -\ln\frac{1-p}{1+p}$, then $\mu_\beta^\mathsf f [\sigma_0\cdot\sigma_x]$ decays exponentially. So $\beta_c^{exp}=+\infty$.

For Potts model, the technique is similar. Assign $\sigma_x\sigma_y=(q\mathbb 1_{\sigma_x=\sigma_y}-1)/(q-1)$ to $xy$. 

For ease of notation, let $\Sigma=\{\sigma:G_n\to\mathbb T_q\mid \sigma=\mathsf b\text{ on }\partial G_n \}$, $\Sigma_1=\{\sigma:G_n\to\mathbb T_q\mid \sigma=\mathsf b\text{ on }\partial G_n , \sigma_0=\mathsf b\}$ and $\Sigma_2=\{\sigma:G_n\to\mathbb T_q\mid \sigma=\mathsf b\text{ on }\partial G_n, \sigma_0=\mathsf c \}$ for some $\mathsf c\ne \mathsf b$. 

The normalization constant is 
$$
\int_\Sigma \exp[-\beta H_{G_n}^\mathsf f(\sigma)]d\sigma=\int_{\Sigma}\exp[-\beta \frac{q}{q-1}\sum_{xy\in E}\mathbb 1_{\sigma_x=\sigma_y}+\frac{2n\beta}{q-1}]d\sigma
$$
Actually we can neglect $e^\frac{2n\beta}{q-1}$ since it will be cancelled. 

For $\beta_c$, let $A=\int_{\Sigma_1}\exp[-\beta \frac{q}{q-1}\sum_{xy\in E}\mathbb 1_{\sigma_x=\sigma_y}]d\sigma$ and $B=\int_{\Sigma_2}\exp[-\beta \frac{q}{q-1}\sum_{xy\in E}\mathbb 1_{\sigma_x=\sigma_y}]d\sigma$. By the symmetry of $\mathbb T_q$, we have 
$$
\mu_{G_n,\beta}^\mathsf b[\sigma_0\cdot\mathsf b]=\frac{A-B}{A+(q-1)B}
$$
by the symmetry of $\mathbb T_q$. Now it suffices to show $A/B\to 1$. 

1. Let $T_n$ be the number of paths on $\mathbb T_q$ which have length $n$ and both endpoints $\mathsf b$. Then $T_1=0$, and $T_n=(q-1)((q-1)^{n-1}-T_{n-1})/(q-1)=(q-1)^{n-1}-T_{n-1}$. So $T_n=(q-1)^n/q+(q-1)(-1)^n/q$. This implies $T_n/(q-1)^n\to 1/q$. 

2. Now compute $\sqrt{A}$ by considering $[-n,0)\cap\mathbb Z$. Since the endpoints are identical, by selecting edges whose endpoints are identical and collapse them, we have 
   $$
   \sqrt{A}=\sum_{k=0}^n \binom{n}{k}p^k T_{n-k}=q^{-1}((p+q-1)^n+(q-1)(p-1)^n), p=e^{-\frac{\beta q}{q-1}}
   $$
   and similarly, 
   $$
   \sqrt{B}=\sum_{k=0}^n \binom{n}{k} p^k \frac{(q-1)^{n-k}-T_{n-k}}{q-1}=q^{-1}(p+q-1)^n-(p-1)^n
   $$

it's immediate to conclude $\sqrt{A}/\sqrt{B}\to 1$. This shows $\beta_c=\infty$. 

Again, (notice in the second line, $A$ and $B$ has variable $x$)
$$
\begin{aligned}
\lim_{\|x\|\to\infty}\mu_\beta^\mathsf f [\sigma_0\cdot\sigma_x]&=\lim_{x \to \infty}\lim_{n \to \infty}\mu_{G_n,\beta}^\mathsf f[\sigma_0\cdot \sigma_x]
\\&=\lim_{x \to \infty} \frac{\sqrt{A}-\sqrt{B}}{\sqrt{A}+(q-1)\sqrt{B}}=0
\end{aligned}
$$
which indicates $\beta_c^{lro}=+\infty$.

_Remark_ This implies in some cases $\beta_c=\beta_c^{lro}$.

Moreover, $\sqrt{A}-\sqrt{B}=-(p-1)^n/q$. This have already shown the decay is exponential. So $\beta_c^{exp}=+\infty$. 

_Remark_ The benefit of $\mathbb Z$ is the simple geometry, from which we can compute accurately the amount involved.

_Conjecture_ For $O(n)$ models on $\mathbb Z$ the results are identical.



#### 1.2.1 Definition of the random-cluster model

> [!Note]
>
> The graph discussed below are finite.

_Solution to exercise 2_  Just pick two opposite faces and identify them.

_Solution to exercise 3_ 

1. The spanning trees has equal measure: all spanning trees have equal $o(\omega),c(\omega)$ and $k(\omega^\xi)$.
2. Since the graph is finite, the measure on all subgraphs with more than 2 clusters is $O(q^2)$ , while that on all subgraphs with 1 cluster is $O(q)$. Since $q/p\to 0$, the limit measure will be 0 on the former. Similarly as $p\to 0$, the measure will be supported only on spanning trees.

_Check of 1.3_ 

The first identity is intuitively right.

For the second identity, notice if $x\leftrightarrow y$ in $\psi^\xi$, then  opening or closing $e$ will not change the number of cluster, so it can be seen as a Bernoulli percolation. Otherwise, opening $e$ will decrease $k$ by $1$. Let $x$ be the value, then $x/(1-x)=p/(1-p)q$. 

_Explanation of **finite-energy property**_ In models with such property, changing the state of one edge (or finite many edges) has finite energetic cost which can be uniformly bounded. 

_Solution to exercise 4_ 

For FE, pick $c_{FE}=\min\{p,1-p,\frac{p}{p+q(1-p)},1-\frac{p}{p+q(1-p)} \}$. For DMP, since the graph is finite, one can use induction on the number of edges. 



#### 1.2.2 The coupling between the random-cluster and Potts models

> [!Important]
>
> **Proposition 1.2 Coupling for free boundary conditions** Fix an integer $q\ge 2$, $p\in(0,1)$ and $G$ finite. Then 
>
> (i) Sample $\omega$ according to $\phi_{G,p,q}^0$, the RC percolation with free BC, and assign i.i.d. spins on clusters, resulting $\sigma$.
>
> (ii) Sample $\sigma$ from $\mu_{G,\beta,q}^0$, the Potts model, where $\beta=-\frac{q-1}{q}\ln(1-p)$.
>
> $\sigma$ has the same distribution.

_Solution to exercise 5_ 

Given $\sigma$, perform Bernoulli percolation of probability $p$ on $E\backslash E_\sigma$ and keep $E_\sigma$ closed. The resulting $\omega$ has desired distribution.

> [!Important]
>
> **Proposition 1.3 Coupling for monochromatic boundary conditions** Fix $q\ge 2$, $p\in(0,1)$ and $G$ finite. Then 
>
> (i) Sample $\omega$ according to $\phi_{G,p,q}^1$, the RC percolation with $\partial G$ collapsed into one point, and assign i.i.d. spins on clusters except $\mathcal C$ intersecting $\partial G$, $\mathsf b$ on $\mathcal C$, resulting $\sigma$.
>
> (ii) Sample $\sigma$ from $\mu_{G,p,q}^\mathsf b$, where $\beta=-\frac{q-1}{q}\ln(1-p)$.
>
> $\sigma$ has the same distribution.

_Solution to exercise 6, the proof of Proposition 1.3_

The technique is identical. For $\sigma$ compatible with $\omega$ and satisfy BC, 
$$
\mathbf P[(\omega,\sigma)]=\frac{1}{Z_{G,p,q}^1}p^{o(\omega)}(1-p)^{c(\omega)}q^{k(\omega^1)}q^{-k(\omega^1)+1}=\frac{q}{Z_{G,p,q}^1}p^{o(\omega)}(1-p)^{c(\omega)}
$$
Sum up w.r.t. $\omega$, we have (conditioned on BC $\mathsf b$)
$$
\mathbf P[\sigma]=\frac{q}{Z_{G,p,q}^1}(1-p)^{|E_\sigma|}=\frac{qe^{-\beta|E|}}{Z_{G,p,q}^1}\exp[-\beta H_{G}^\mathsf f(\sigma)]
$$
This have already shown the proposition. 

_Solution to exercise 7_ Let $\mathcal C$ be the collection of all clusters in $G$. Let $B$ be the event that all clusters in $\sigma$ intersect $A$ for even times, and $D$ be the event that some clusters in $\sigma$ intersect $A$ for odd times. Then
$$
\mu_{G,\beta}^\mathsf f[\sigma_A]=\mathbb E[\sigma_A\mathbb 1_{B}]+\mathbb E[\sigma_A \mathbb 1_{D}]
$$
Notice $\mathbb E[\sigma_A\mathbb 1_B]=\mathbb E[\mathbb 1_B]=\mathbb P(B)$ since if B occurs, $\sigma_A=1$. Meanwhile, $\mathbb E[\sigma_A \mathbb 1_D]=0$, since when we pick a cluster that intersects $A$ for odd times, say $c$, $P(\sigma_{A\cap c}=1)=P(\sigma_{A\cap c}=-1)=1/2$, and by independence of spins among clusters, $\mathbb E[\sigma_A \mathbb 1_D]=0$.



#### 1.3.1 Positive association and monotonicity

> [!Important]
>
> **Theorem 1.6 (Positive association)** Fix $q\ge 1$, $p\in[0,1]$, $\xi$ some boundary conditions and $G$ finite. Then
>
> - (Comparison between boundary conditions) For any increasing event $\mathcal{A}$ and $\xi' \ge \xi$ (meaning that the partition $\xi'$ is coarser than the partition $\xi$),
> $$
> \phi_{G,p,q}^{\xi'}[\mathcal{A}] \ge \phi_{G,p,q}^{\xi}[\mathcal{A}]. \tag{CBC}
> $$
>
> - (Monotonicity) For any increasing event $A$ and any $p'\ge p$,
> $$
> \phi_{G,p',q}^{\xi}[A] \ge \phi_{G,p,q}^{\xi}[A]. \tag{MON}
> $$
>
> - (Fortuin–Kasteleyn–Ginibre inequality) For any increasing events $\mathcal{A}$ and $\mathcal{B}$,
>
> $$
> \phi_{G,p,q}^{\xi}[\mathcal{A}\cap\mathcal{B}] \ge \phi_{G,p,q}^{\xi}[\mathcal{A}]\,\phi_{G,p,q}^{\xi}[\mathcal{B}]. \tag{FKG}
> $$

_Remark_ For CBC, two extreme cases are 
$$
\phi_{G,p,q}^{0}[\mathcal{A}] \le \phi_{G,p,q}^{\xi}[\mathcal{A}] \le \phi_{G,p,q}^{1}[\mathcal{A}].
$$
_Intuition_ Adding extra links (CBC) encouraging more open edges (MON), and conditioning on another increasing event (FKG) all make an increasing event more likely to happen.

_A detailed proof_ 

The main tool is 

> [!Tip]
>
> **Lemma** Consider two strictly positive measures $\mu$ and $\nu$ on $\{0,1\}^E$ s.t. for any $e\in E$ and $\psi,\psi'\in\{0,1\}^{E\backslash e}$ satisfying $\psi\le\psi'$, one has $\mu[\omega_e=1\mid \omega_{E\backslash e}=\psi]\le\nu[\omega_e=1\mid \omega_{E\backslash e}=\psi']$. Then $\mu$ is stochastically dominated by $\nu$.

And a previous result

> [!Tip]
> $$
> \phi_{G,p,q}^{\xi}\big[\omega_e=1\,\big|\,\omega_{E\setminus\{e\}}=\psi\big]=
> \begin{cases}
> p & \text{if } x \text{ and } y \text{ are connected in } \psi^{\xi},\\[6pt]
> \dfrac{p}{p+q(1-p)} & \text{otherwise.}
> \end{cases}
> $$
> when $q\ge 1$, $p\ge \frac{p}{p+q(1-p)}$.

For CBC, it suffices to show $\phi_{G,p,q}^{\xi}\big[\omega_e=1\,\big|\,\omega_{E\setminus\{e\}}=\psi\big]\le \phi_{G,p,q}^{\xi'}\big[\omega_e=1\,\big|\,\omega_{E\setminus\{e\}}=\psi'\big]$. Notice if $x$ and $y$ are connected in $\psi^\xi$, then they must be connected in $\psi'^{\xi}$, and in $\psi'^{\xi'}$. So it holds from the second result.

For MON, it suffices to show $\phi_{G,p,q}^{\xi}\big[\omega_e=1\,\big|\,\omega_{E\setminus\{e\}}=\psi\big]\le \phi_{G,p',q}^{\xi}\big[\omega_e=1\,\big|\,\omega_{E\setminus\{e\}}=\psi'\big]$.Notice if $x$ and $y$ are connected in $\psi^\xi$, then they must be connected in $\psi'^\xi$. So it holds from the second result. 

For FKG, first we show $\phi_{G,p,q}^{\xi}\big[\omega_e=1\,\big|\,\omega_{E\setminus\{e\}}=\psi\big]\le \phi_{G,p,q}^{\xi}\big[\omega_e=1\,\big|\,\omega_{E\setminus\{e\}}=\psi',\mathcal B\big]$. Write $\psi^0,\psi^1$ to be $\psi$ with $\psi_e=0,1$ respectively. For ease of notation, let $\mu=\phi_{G,p,q}^{\xi}[\cdot\mid \omega_{E\backslash\{e\}}=\psi']$. We have 
$$
RHS=\frac{\mu[\omega_e=1,\mathcal B]}{\mu[\mathcal B]}=\frac{\mu[\omega_e=1]\mathbb 1_{\psi'^1\in\mathcal B}}{\mu[\omega_e=1]\mathbb 1_{\psi'^1\in\mathcal B}+\mu[\omega_e=0]\mathbb 1_{\psi'^0\in\mathcal B}}\ge \frac{\mu[\omega_e=1]}{\mu[\omega_e=1]+\mu[\omega_e=0]}=\mu[\omega_e=1]
$$
That inequality holds, because $\mathbb 1_{\psi'^0\in\mathcal B}\le\mathbb 1_{\psi'^1\in\mathcal B}$ since $\mathcal B$ is increasing. Replacing $\psi'$ by $\psi$ will only decrease the probability by the same argument as above. 

Next, the right hang of inequality is not strictly positive but that makes no difference. 



_Solution to exercise 8_ 

By the Griffiths equality, $\mu_{G,\beta}^\mathsf f[\sigma_A]=\phi_{G,p,q}[\text{all clusters intersect A for even times}]$. Interestingly this event is increasing. By FKG inequality, we have $\mu_{G,\beta}^\mathsf f[\sigma_A\sigma_B]\ge\mu_{G,\beta}^\mathsf f[\sigma_A]\mu_{G,\beta}^\mathsf f[\sigma_B]$.

_Solution to exercise 9_ 

Notice for $\omega\in \mathcal B$
$$
\phi_{G,p,q}^\xi[\mathcal A\mid \omega_{G\backslash H}]=\phi_{H,p,q}^{\omega_{G\backslash H}^\xi}[\mathcal A]
$$
which lies in $[\phi_{H,p,q}^{0}[\mathcal{A}] , \phi_{H,p,q}^{1}[\mathcal{A}]].$ This has shown all.

_Solution to exercise 10_ 

1. _Note_ There is a typo: $\{\mathsf S=S\}$ is measurable w.r.t. ... outside $S$.

   This is immediate since one can find $\{\mathsf S=S\}$ is independent of the states of edges with two endpoints in $S$, because opening or closing such edges make no difference for $S$ to connect to $\partial G$. 

2. _Note_ There is a typo: the inequality should be an identity.

   When $\phi_{G,p,q}^\xi[\mathsf S=S\mid \partial G'\nleftrightarrow\partial G]=0$, there is nothing to prove. When it's positive, equivalently we need to show $\phi_{G,p,q}^\xi [\mathcal A\mid \mathsf S=S,\partial G'\nleftrightarrow\partial G]= \phi_{H,p,q}^0[\mathcal A]$. This follows since $\partial G'\nleftrightarrow\partial G$ and $\mathsf S=S$ indicate $F\subset H$ and edges on $\partial H$ should be closed, which put free BC on $H$. 

3. Sum w.r.t. $S$ and notice $\phi_{H,p,q}^0[\mathcal A]\le \phi_{G,p,q}^0[\mathcal A]$, since the latter put (stochastic) coarser BC.

4. This can be proven via the same process. The core is, such circuit is putting a $^1$ BC, i.e., 
   $$
   \phi_{G,p,q}^\xi[\mathcal A\mid \gamma\text{ is the circuit}]=\phi_{G_{\gamma},p,q}^1[\mathcal A]\ge \phi_{G,p,q}^1[\mathcal A]
   $$
   where $G_\gamma$ is the graph inside $\gamma$. The second inequality holds since the latter puts less coarser BC on $G_\gamma$. This has shown the result. 

_Solution to exercise 11_ 

1. $$
   \begin{aligned}
   &\mu\left[\omega_e = 1\big|\omega|_{E\setminus\{e\}} = \psi\right] \leq \nu\left[\omega_e = 1\big|\omega|_{E\setminus\{e\}} = \psi'\right].
   \\\Leftrightarrow&\frac{\mu[\psi^1]}{\mu[\psi^1]+\mu[\psi^0]}\le\frac{\nu[\psi'^1]}{\nu[\psi'^1]+\nu[\psi'^0]}
   \\\Leftrightarrow&\mu[\psi^1]\nu[\psi'^0]\le\mu[\psi^0]\nu[\psi'^1]
   \end{aligned}
   $$

   From the condition in the exercise, pick $\omega=\psi^1$ and $\omega'=\psi'^0$, and 1.9 holds.

   From 1.9, for two different configuration, this can be proved via intermediate configurations.

2. From FKG inequality, 
   $$
   \mu[\omega^{ef}]\ge \mu[\omega^e]\mu[\omega^f]=(\mu[\omega^{ef}]+\mu[\omega_f^e])(\mu[\omega^{ef}]+\mu[\omega_e^f])
   $$
   which, after simplification, is just $\mu[\omega^{ef}]\mu[\omega_{ef}]\ge \mu[\omega_f^e]\mu[\omega_e^f]$. 

   From the lattice condition, we can get Holley criterion for $\mu$ and $\mu$, i.e., 
   $$
   \mu[\omega\vee\omega']\mu[\omega\wedge\omega']\ge\mu[\omega]\mu[\omega']
   $$
   Since $\mathcal B$ is increasing, $\omega\in\mathcal B\Rightarrow\omega\vee\omega'\in\mathcal B$. So one can verify 
   $$
   \mu[\omega\vee\omega',\mathcal B]\mu[\omega\wedge\omega']\ge\mu[\omega,\mathcal B]\mu[\omega']
   $$
   and moreover,
   $$
   \mu[\omega\vee\omega'\mid\mathcal B]\mu[\omega\wedge\omega']\ge\mu[\omega\mid\mathcal B]\mu[\omega']
   $$
   which, by 1, has already shown FKG.

_Solution to exercise 12_ 

check the proof of MON, one can find when $q\ge 1$, for $q'\le q$, $\phi_{G,p,q'}^\xi[\mathcal A]\ge\phi_{G,p,q}^\xi[\mathcal A]$.

#### 1.3.2 Phase transition in the random-cluster and Potts models

_Solution to exercise 13_ 

- $\{\omega\in\{0,1\}^\mathbb E: \omega_e=\psi_e,\forall e\in E\}=A\backslash B$, where $A=\{\omega': \omega'_e=1\forall e\in E\}$ and $B=\{\omega':\omega'_e=1\forall e\in E, \omega_e=0\}$. Notice $A$ and $B$ are both increasing, and $B\subset A$
- For an event $\mathcal A$ determined on finite many of edges, say $E$, consider the partial order $\le$ on $E$. Suppose $M$ is the collection of minimal elements, then $\mathcal A=A\backslash \cup_{m\in M} B_m$. Notice $A$ and $\cup_{m\in M} B_m$ are both increasing and the latter is a subset of the former. 

_Solution to exercise 14_

1. Yes, it's just exercise 12.
2. Notice $\phi_{p,q}^1[0\leftrightarrow\infty]\le \phi_{p,1}^1[0\leftrightarrow\infty]$. when $q=1$, it's just percolation model, and $p_c>0$. The inequality tells us $p_c(q,d)\ge p_c(1,d)>0$.

_Solution to exercise 15_ 

1. When $p<p_c$, there is no infinite cluster, which indicates that for the events determined on finite many edges, the boundary condition will asymptotically have the same distribution, i.e., $\phi_{p,q}^1=\phi_{p,q}^0$ on these events. It can be easily expanded to all events.

_Solution to exercise 16_ 

For an increasing event $A$ determined by $\Lambda_n$,
$$
\phi[A]=\mathbb E\phi[A\mid \mathcal F_{\Lambda_n}]=\mathbb E\phi_{\Lambda_n,p,q}^\xi[A]\le\mathbb E\phi_{\Lambda_n,p,q}^1[A]=\phi_{\Lambda_n,p,q}^1[A]
$$
the other side also holds, i.e., $\phi_{\Lambda_n,p,q}^0[A]\le\phi[A]\le\phi_{\Lambda_n,p,q}^1[A]$. Now push $n\to\infty$. This can be expanded to the events determined by finite many edges, and all events. 

When $\phi_{p,q}^0=\phi_{p,q}^1$, the unique measure is just $\phi_{p,q}^0$. When they are not equal, two of them can be such measure.

_Solution to exercise 17_

_Recall_ FE, finite-energy property, means $\phi_{G,p,q}^\xi[\omega_e=1\mid \omega_{|E\backslash\{e\}}=\psi]\in[c_{FE},1-c_{FE}]$ for any $e$ and $\psi$, for some $c_{FE}>0$, which depends on $p,q$.

The proof is just like that of Bernoulli percolation. For ease of notation I will use $P$ in place of $\phi$.

First, by FE, for a path $e_1e_2\cdots e_n$, one can estimate
$$
P[e_1=e_2=\cdots=e_n=1]=P(e_n=1\mid e_2=\cdots=e_n=1)P(e_2=1\mid e_3=\cdots=e_n=1)\cdots P(e_n=1)\le p^n
$$
If one use FKG, 
$$
P[e_1=\cdots=e_n=1]\ge P[e_1=1]\cdots P[e_n=1]\ge c_{FE}^n>0
$$
Now by the second inequality, one can argue that $P(\text{there is an infinite cluster })=0$ $\Leftrightarrow$ $P(\text{there is an infinite cluster including 0})=0$. 

By the first inequality,
$$
\begin{aligned}
P(\text{there is an infinite cluster including 0})&\le P(\text{there is a path from 0 of length n})\\&\le 2d(2d-1)^{n-1} p^n
\end{aligned}
$$
when $p<(2d-1)^{-1}$, RHS tends to 0, which implies LHS=0. So $p_c(q,d)>0$. This gives the same estimate as Bernoulli percolation. 

_Solution to exercise 18_

For ease of notation let $\phi_{p,q}^1$ be $\mu$. Suppose $\tau_x\mathcal A=\mathcal A\forall x$. To apply mixing, pick $\mathcal B_n$ measurable w.r.t. finite many edges and $\mathcal B_n\to\mathcal A$. This gives 
$$
\mu[\mathcal A]=\lim_{\|x\|\to\infty}\mu[\mathcal A\cap\tau_x \mathcal A]=\lim_{\|x\|\to\infty}\lim_{n \to \infty}\mu[\mathcal B_n\cap \tau_x \mathcal B_n]=\lim_{n \to \infty}\lim_{\|x\|\to\infty}\mu[\mathcal B_n\cap\tau_x \mathcal B_n]=\lim_{n \to \infty} \mu[\mathcal B_n]^2=\mu[\mathcal A]^2
$$
_Solution to exercise 19_ 

Reverse every sign of inequality.

_Proof of theorem 10_

- $\phi_{p,q}^1[\mathcal E_{<\infty}]>0\Rightarrow\phi_{p,q}^1[\mathcal E_{\le 1}]>0$

  The core of proof is FE, i.e., modifying finite edges will cause controllable effect. If there are finite many infinite clusters, then "glue" them by opening all edges in $\Lambda_n$ for sufficiently large $n$ into one or zero infinite clusters, which will not make the probability vanish. 

- $\phi_{p,q}^1[\mathcal E_{=\infty}]=0$

  $K$ is chosen large enough that, whenever there are $K$ clusters intersecting $\Lambda_n$, one can find $3$ vertices $x,y,z$, satisfying that they connects to $\infty$, and the distances between any pair of them are at least 3. Notice $K$ can depend only on $d$, e.g., $K=7^d\times 2+1$. (pick a point connecting to $\infty$ and remove points connecting to $\infty$ $\le 3$ away from it, then pick another, remove, and there must be at least 1 left.)

  The first peeling procedure is to remove all cycles while remain the connectivity of points. , while the second peeling procedure leaves a tree whose leaves (nodes of degree 1) must lie in $\partial \Lambda_n$. (Notice the expression is confusing. Actually, a cluster should be a subgraph. It is saying: given the subgraph induced by $\tilde F_{j-1}$, if removing $f_j$ produces a new cluster (which may be a singleton) that isn't connecting to $\partial \Lambda_n$, then remove $f_j$ and the new cluster.) It's easy to figure out that, if $x$ is a trifurcation, then after peeling $x$ is still a trifurcation (for the furcation with at least 2 branches, this will always hold.) 

  > A lemma on tree: the number of leaves is more than the number of nodes of degree more than 3.
  >
  > _proof_ Let $n_i$ be the number of nodes of degree $i$, then we have 
  > $$
  > \begin{aligned}
  > &n_1+2n_2+3n_3+...=2\#\text{edges}\\&n_1+n_2+...=\#\text{nodes}=\#\text{edges}+1
  > \\\Rightarrow& n_1-(n_3+2n_4+...)=2
  > \\\Rightarrow&n_1\ge n_3+n_4+...
  > \end{aligned}
  > $$


_Solution to exercise 20_ 

Where the amenability is used is the argument of the existence of trifurcation, so it naturally holds. 

For those non-amenable graphs, the uniqueness may not be the case, for example, the binary tree. 

_proof of Theorem 1.12_

(1.16) follows from Markov inequality, (write P and E for ease of notation)
$$
P[o(\omega)\ge(a+\epsilon)|E_n|]\le\frac{Eo(\omega)}{(a+\epsilon)|E_n|}\le\frac{a}{a+\epsilon}\Rightarrow P[o(\omega)\le(a+\epsilon)|E_n|]\ge\frac{\epsilon}{a+\epsilon}\ge \epsilon
$$
#### 2.1 Kesten's theorems

_Remark on Proposition 2.1_ 

1. The reason to use $\Lambda_k$ instead of a single point is that, a single point is highly likely to be isolated (as long as four adjacent edges were closed). This idea motivates "coarsening".
2. Notice when passing $\mathcal H_n$ to $\mathcal A_n$, we are not modifying finitely many edges in $\Lambda_k$ (of course, for technique reason, as $k\to\infty$ the cost is unbounded) to identify two clusters, instead, by the uniqueness of infinite cluster, as long as two clusters tend to infinity, they are identified naturally.  

_Solution to exercise 22_ 

> [!Important]
>
> **Square root trick** For increasing events $\mathcal A_1,...,\mathcal A_n$, 
> $$
> \max\{\mathbb P_p[\mathcal A_i]:1\le i\le r \}\ge 1-\bigg(1-\mathbb P_p[\bigcup_{i=1}^r\mathcal A_i] \bigg)^{1/r}
> $$

Use FKG reversely: For increasing events $A$ and $B$, 
$$
(1-P(A))(1-P(B))=1-P(A)-P(B)+P(A)P(B)\le 1-P(A)-P(B)+P(AB)\le 1-P(A\cup B)
$$
Using this repeatedly and notice $A\uparrow, B\uparrow\Rightarrow A\cup B\uparrow$, and one can get the result.

_Solution to exercise 23_ 

1. The square root trick.

2. Let $\mathcal A_n$ be the event that there exist infinite paths from the left and right side to infinity, and $\mathcal C_n$ be the event that there exists infinite paths in $\omega^*$ from the left and right side to infinity. First, by symmetry and FKG inequality,
   $$
   \mathbb P_{1/2}[\mathcal A_n]\ge \mathbb P_{1/2}[\text{left of }\Lambda_n\leftrightarrow\infty]\mathbb P_{1/2}[\text{right of }\Lambda_n\leftrightarrow\infty]\ge(1-\mathbb P_{1/2}[\Lambda_n\nleftrightarrow\infty]^{1/4})^2\ge1-2\mathbb P_{1/2}[\Lambda_n\nleftrightarrow\infty]
   $$
   The same holds for $\mathcal C_n$. The subtle point is that, $\mathcal C_n$ is an decreasing event. So we have 
   $$
   \mathbb P_{1/2}[\mathcal B_n]\ge \mathbb P_{1/2}[\mathcal A_n]+\mathbb P_{1/2}[\mathcal C_n]-1\ge 1-4\mathbb P_{1/2}[\Lambda_n\nleftrightarrow\infty]^{1/4}
   $$

3. Notice 
   $$
   \mathbb P_{1/2}[\mathcal B_n\cap\{\omega_e=0\forall e\in E_n \}]\ge \mathbb P_{1/2}[\mathcal B_n]c_{FE}^{|E_n|}
   $$
   But if the event of LHS happens, then the infinite clusters intersecting the top and bottom will be separated by the edges in $\Lambda_n$ along with the paths in $\omega^*$ connecting the left/right to $\infty$, so $\mathbb P_{1/2}[\exists \ge 2 \text{clusters}]\ge LHS$. So $\mathbb P_{1/2}[\mathcal B_n]=0$. This forces that $\inf\mathbb P_{1/2}[\Lambda_n\nleftrightarrow\infty]>0$.

This indicates that there is no infinite cluster when $p=1/2$.

_Solution to exercise 24_

1. _Note_ The circuit is from the primal graph.

   When $p<p_c(\mathbb G)$, fix $v^*\in \mathbb G^*$. Let $A_x=\{x\text{ is in some open circuit surrounding }v^*\}$. This gives us
   $$
   \mathbb P_p[A_x]\le \mathbb P_p[0\leftrightarrow \partial\Lambda_{\|x-v^*\|_\infty}]\le e^{-c_p\|x-v^*\|_\infty}
   $$
   Since if the circuit passes $x$ and surrounds $v^*$, along the path $x$ can connect to a point further than $v^*$.

   Sum over all vertices of $\mathbb G$, and we have 
   $$
   \sum_{x\in \mathbb Z^2}\mathbb P_p[A_x]\le \sum_n Cne^{-c_p n}<\infty
   $$
   By Borel-Cantelli lemma, there is only finitely many $x$ s.t. $A_x$ occurs. This have shown that there cannot be finitely many open circuits.

   Intuitionally it may be true since it will be too narrow to put infinitely many open circuits. 

   When there are finitely many open circuits surrounding $v^*$, by opening finitely many edges, $v^*$ can connect to $\infty$. This implies that $\mathbb P_p[v^*\overset{\mathbb G^*}\leftrightarrow\infty]>0$. So $p_c(\mathbb G^*)\le 1-p$. By taking infimum one can get $p_c(\mathbb G^*)\le 1-p_c(\mathbb G)$.

2. Let $B(z)=\mathbb P_p[S_z\overset{R}\leftrightarrow \text{Bottom}]$, and $T(z),L(z),R(z)$ are similarly defined. Let $X=\{z: B(z)\ge T(z)\}$ and $Y(z)=\{z: L(z)\ge R(z) \}$. Notice $\text{Bottom}\subset X$ and $\text{Top}\subset X^c$. Define $\partial X=\{z: z\in X, \exists y\sim x: y\in X^c \}$. Then $\partial X$ must be from the left to the right. Similarly $\partial Y$ must be from the top to the bottom. In this case they must intersect. Then the point $x\in \partial X\cap\partial Y$ is what we seek for. 

3. Notice $\mathbb P_p[S_x\overset{\mathbb H}\leftrightarrow \mathcal l_+]$ increases as $x_2$ increases, and when $x_2=\infty$ the $\mathbb P_p[S_x\overset{\mathbb H}\leftrightarrow \mathcal l_+]\ge \mathbb P_p[S_x\overset{\mathbb H}\leftrightarrow \mathcal l_-]$, when $x_2=-\infty$ it's reversed.

4. Apply the trick to 3.

5. The corrected statement is: $\lim_{n \to \infty}\mathbb P_p[\{0\}\times[0,1]\overset{\omega^*\cap\mathbb H}\leftrightarrow\partial \Lambda_{n+1/2}]=0$. 

   Let $\mathcal C_\infty$ be the unique infinite primal cluster. Let $\rho_s=\mathbb P_p[S_0\cap \mathcal C_\infty=\emptyset]\to 0$ as $s\to\infty$. By translation invariance, $\rho_s=\mathbb P_p[S_x\cap\mathcal C_\infty=\emptyset]$. Since $\mathcal C_\infty$ is unbounded in four directions, we have $\mathbb P_p[S_x\nleftrightarrow\mathcal l]\le\rho_s$. Then by 4 we have 
   $$
   \mathbb P_p[S_x\overset{\mathbb H}\leftrightarrow\mathcal l_-]\ge 1-\sqrt{\rho_s}, \mathbb P_p[S_{x+(0,1)}\overset{\mathbb H}\leftrightarrow\mathcal l_+]\ge 1-\sqrt{\rho_s}
   $$
   Let $K_m=S_x\cup S_{x+(0,1)}$. From the inequality we know
   $$
   \mathbb P_p[K_m\leftrightarrow\mathcal l_+,K_m\leftrightarrow\mathcal l_-]\ge 1-2\sqrt{\rho_s}
   $$
   Let $m\to\infty$ and by the uniqueness of infinite cluster, those two paths are highly likely to be in the same cluster, i.e., 
   $$
   \mathbb P_p[l_-\leftrightarrow l_+]\ge 1-2\sqrt{\rho_s}-o(1)
   $$
   When there is a dual path connecting $\{0\}\times[0,1]$ to $\infty$, $l_+\nleftrightarrow l_-$, so its probability will be lower than $2\sqrt{\rho_s}+o(1)$, which tends to $0$ as $s\to\infty$.

6. Otherwise the distance is bounded for some subseries of $R$ tending to $\infty$. WLOG consider $[0,n]\times[0,k]$ and suppose $x(R)_1\le d$. First, $\mathbb P_p[S_{x''}\overset R \leftrightarrow\text{Left}]>0$ by FE, but on the other side $\mathbb P_p[S_{x''}\overset R \leftrightarrow\text{Right}]\to 0$. Otherwise, also by FE, by opening all edges in $S_{x''}$ and the edges to the left, we have $\mathbb P_p[\text{Left}\overset R \leftrightarrow \text{right}]\ge C\mathbb P_p[S_{x''}\overset R \leftrightarrow\text{Right}]>0$ for arbitrary large $R$. But from 5 we have known such infinite arm can't exist in dual graph, for the same reason it can't exist in primal graph. This leads to contradiction. But the contradiction occurs since $x''$ is not as expected. 

7. Notice for $y=x,x',x''$, one have 
   $$
   \max\{B(y),T(y),L(y),R(y) \}\ge 1-\rho_s^{1/4}
   $$
   Since $B(x)\ge T(x), L(x)\ge R(x)$, one have 
   $$
   \max\{B(x),T(x)\}\ge 1-\rho_s^{1/4}
   $$
   If $B(x)\ge 1-\rho_s^{1/4}$, then for $x'$, one have 
   $$
   \begin{aligned}
   B(x')&\ge \mathbb P_p[S_x\overset R\leftrightarrow\text{Bottom}, S_{x'}\overset R\leftrightarrow \partial R,\text{two paths is of the same cluster}]
   \\&\ge (1-\rho_s^{1/4})(1-\rho_s)-o(1)
   \\&\ge 1-\rho_s^{1/4}-\rho_s-o(1)
   \end{aligned}
   $$
   where $o(1)$ comes from the uniqueness of the cluster and the fact from 6 that the paths tend to be infinite.

   Moreover $T(x')\ge B(x')$. So for $\mathcal V(n,k)$, by FKG, uniqueness, and 6,
   $$
   \mathbb P_p[\mathcal V(n,k)]\ge B(x')^2-o(1)\ge 1-2\rho_s^{1/4}-O(\rho_s)-o(1)
   $$
   which tends to $1$ as $s\to\infty$. If $T(x)\ge 1-\rho_s^{1/4}$, the argument is the same. So we get the proof.

8. Notice $\mathbb P_p[\mathcal H(n,k)]\ge c>0$ and $\mathbb P_p[\mathcal V(n,k)]\to 0$. So such $k(n)$ exists. Moreover, from $\mathbb P_p[\mathcal V(n+1,k)]\ge \mathbb P_p[\mathcal V(n,k)]\ge \mathbb P_p[\mathcal H(n,k)]\ge \mathbb P_p[\mathcal H(n+1,k)]$, $k(n)$ is nondecreasing. And considering the case $n=\infty$, we know $k(n)\to\infty$. 

   We have 
   $$
   \mathbb P_p[\mathcal V(n,k)]\ge \mathbb P_p[\mathcal H(n,k)],\mathbb P_p[\mathcal V(n,k+1)]\le \mathbb P_p[\mathcal H(n,k+1)]
   $$
   But by 7, one of $\mathbb P_p[\mathcal V],\mathbb P_p[\mathcal H]$ tends to 0 while the other tends to 1. Each case will lead to contradiction. So $p^*\ge 1-p$, and we have $p_c(\mathbb G)+p_c(\mathbb G^*)\ge 1$.

So we have proven $p_c(\mathbb G)+p_c(\mathbb G^*)=1$.

#### 2.2 Two proofs of sharpness for Bernoulli percolation

_Differentiate the expectation_
$$
\begin{aligned}
\frac{d\mathbb E_p[X]}{dp}&=\frac{d}{dp}\sum_{\omega}X(\omega)p^{\sum_e \omega_e}(1-p)^{\sum_e 1-\omega_e}\\&=\sum_\omega X(\omega)[(\sum_e\omega_e)p^{\sum_e\omega_e -1}(1-p)^{\sum_e 1-\omega_e}-p^{\sum_e \omega_e}(\sum_e1-\omega_e)\ (1-p)^{\sum_e 1-\omega_e-1}]\\&=\sum_\omega X(\omega)\frac{1}{p(1-p)}p^{\sum_e \omega_e}(1-p)^{\sum_e 1-\omega_e}[(1-p)\sum_e \omega_e-p\sum_e 1-\omega_e]\\&=\sum_\omega X(\omega)\frac{1}{p(1-p)}p^{\sum_e \omega_e}(1-p)^{\sum_e 1-\omega_e}[\sum_e \omega_e -\sum_e p]\\&=\frac{1}{p(1-p)}[\mathbb E_p[X\sum_e \omega_e]-\mathbb E_p[X]\mathbb E_p[\sum_e \omega_e]]
\end{aligned}
$$
_Solution to exercise 25_ 

Notice: The graph may have much more edges than $\mathbb Z^2$ lattice.

1. Define $\varphi_\beta(S):=\sum_{xy\in\Delta S}\mathbb P_\beta[0\overset S\leftrightarrow x](1-e^{-\beta J_{xy}})$, and $\beta_c=\sup\{\beta:\exists S\ni0, |S|<\infty,\varphi_\beta(S)<1 \}$. 

2. _Note_ The result should be $\mathbb P_\beta[0\leftrightarrow\infty]\ge \frac{\beta-\beta_c}{\beta}$.

   Mimic the proof of **Lemma 2.5**. By computation, Let $f(e)=J_e\frac{\omega_e}{1-e^{-\beta J_{e}}}$, and $Ef(e)=J_e$, and this gives $\frac{d}{d\beta}\mathbb E_\beta X=\sum_{e}Cov(X, f(e))$. Now let $\theta_n(\beta)=\mathbb P_\beta[0\leftrightarrow \partial \Lambda_n]$, and let $X=-1_{0\nleftrightarrow\partial\Lambda_n}$, we have 
   $$
   \theta_n'(\beta)=\sum_e \mathbb E_\beta [1_{0\nleftrightarrow\partial\Lambda_n}(J_e-f(e))]
   $$
   It suffices to consider those pivotal edges for $0\nleftrightarrow \Lambda_n$, that is, 
   $$
   \theta_n'(\beta)=\sum_{x,y\in\Lambda_n\\xy\in E_n}J_e\mathbb P_\beta[0\leftrightarrow x, y\leftrightarrow \partial\Lambda_n,0\nleftrightarrow \partial\Lambda_n]
   $$
   Also, consider $\mathsf S$ be the collection of points not connecting to $\partial\Lambda_n$. To make the event for RHS happen, $0,x\in \mathsf S$, $y\notin \mathsf S$, and since $x\sim y$, $xy\in \Delta \mathsf S$. This gives 
   $$
   \theta_n'(\beta)=\sum_{0\in S\subset \Lambda_n}\sum_{xy\in\Delta S}J_{xy}\mathbb P_\beta[0\overset S\leftrightarrow x,\mathsf S=S]=\sum_{0\in S\subset \Lambda_n}\sum_{xy\in\Delta S}J_{xy}\mathbb P_\beta[0\overset S\leftrightarrow x]\mathbb P_\beta[\mathsf S=S]\ge \frac{1}{\beta}\inf_{0\in S\subset\Lambda_n}\phi_\beta (S)(1-\theta_n(\beta))
   $$
   for the same reason as that in **Lemma 2.5**, with $1-e^{-\beta J_{xy}}\le \beta J_{xy}$.

   When $\beta>\beta_c$, solve ODE $\theta_n'(\beta)\ge \beta^{-1}(1-\theta_n(\beta))$ gives $\theta_n(\beta)\ge \frac{\beta-\beta_c}{\beta}$. Push $n\to\infty$.

3. Mimic that of Step 1. 

   When $\beta<\beta_c$, pick $S$ s.t. $\varphi_\beta(S)<1$. Since $S$ is finite, suppose $S\subset\Lambda_{n/2}$, and $n\ge 2R$. Let $\mathsf C=\{x: 0\overset S\leftrightarrow x\}$ be the cluster in $S$ including $0$. Then since $J_{xy}=0$ when $\|x-y\|>R$, for any path connecting $0$ to $\partial\Lambda_{kn}$, it can be split into $0\leftrightarrow x\leftrightarrow y\leftrightarrow \partial\Lambda_{kn}$, where $x$ is in $\mathsf C$ (maybe $0=x$) and $xy\in\Delta S$, and $\|y-0\|\le 2R<n$, whence any path connecting $y$ to $\partial\Lambda_{kn}$ can be translated into a path connecting $0$ to $\partial\Lambda_{(k-1)n}$. 
   $$
   \begin{aligned}
   \mathbb P_\beta[0\leftrightarrow\partial\Lambda_{kn}]&\le \sum_{xy\in\Delta S}\sum_{C\subset S}\mathbb P_\beta[0\overset S\leftrightarrow x, \mathsf C=C, \omega_{xy}=1, y\overset{C^c}\leftrightarrow\partial\Lambda_{kn}]\\&\le\sum_{xy\in\Delta S}\sum_{C\subset S}\mathbb P_\beta[0\overset S\leftrightarrow x, \mathsf C=C](1-e^{-\beta J_{xy}})\mathbb P_\beta[y\overset{C^c}\leftrightarrow \partial\Lambda_{kn}]\\&\le\sum_{xy\in\Delta S}\sum_{C\subset S}\mathbb P_\beta[0\overset S\leftrightarrow x, \mathsf C=C](1-e^{-\beta J_{xy}})\mathbb P_\beta[0\leftrightarrow \partial\Lambda_{(k-1)n}]
   \\&\le\varphi_\beta(S)\mathbb P_\beta[0\leftrightarrow\partial\Lambda_{(k-1)n}]
   \end{aligned}
   $$
   This gives exponential decay. Notice for $(k-1)n\le m\le kn$, $\mathbb P_\beta[0\leftrightarrow \partial\Lambda_{m}]\le\mathbb P_\beta[0\leftrightarrow\partial\Lambda_{kn}]/\min_{1\le j\le n-1}\mathbb P_\beta[0\leftrightarrow\Lambda_j]$.

4. In this case maybe long-range interactions matter, so it may not exponentially decay.

   When $\beta<\tilde\beta_c$, pick $\varphi_\beta(S)<1$. For $n\ge 1$, $x\in\Lambda_n$​, consider all paths $\gamma=x\leftrightarrow x_1\leftrightarrow y_1\leftrightarrow x_2\leftrightarrow y_2\cdots\leftrightarrow x_n\leftrightarrow y_n$ (we call it of length $n$), where ($y_0=x$) $x_i\in \tau_{y_{i-1}} S$ and $x_i,y_i\in \Delta \tau_{y_{i-1}}S$. All paths of length $n$ has probability less than $|S|\varphi_\beta(S)^n$. The sum of probabilities of all possible paths will be greater than the sum in question, since any path can be decomposed into that form; that is, 
   $$
   \sum_{y\in\Lambda_n}\mathbb P_\beta[x\overset{\Lambda_n}\leftrightarrow y]\le |S|+|S|\varphi_\beta (S)+|S|\varphi_\beta(S)^2+...=\frac{|S|}{1-\varphi_\beta(S)}
   $$

_Explanation to Remark 2.7_

1. The set is open since for a finite $S$, $\varphi_p(S)$ is just a polynomial of $p$, which is a continuous function. By previous result, this set is $[0,p_c]$ or $[0,p_c)$, so it can only be $[0,p_c)$, i.e., for $p=p_c$, there is no $|S|<\infty$ with $\varphi_p(S)<1$, especially $\varphi_{p_c}(\Lambda_n)\ge 1$. And we have
   $$
   \frac{1}{dp_c}\sum_{n\ge 0}\varphi_{p_c}(\Lambda_n)=\sum_{n\ge 0}\sum_{xy\in \partial\Lambda_n}\frac{1}{d}\mathbb P_{p_c}[0\overset{\Lambda_n}\leftrightarrow x]\le\sum_{n\ge 0}\sum_{x\in\partial\Lambda_n}\mathbb P_{p_c}[0\overset{\Lambda_n}\leftrightarrow x]\le \sum_{x}\mathbb P_{p_c}[0\leftrightarrow x]
   $$
   The inequality cancels $d$ follows from the fact that any point $x\in\partial\Lambda_n$ has at most $d$ edges connecting to the outside. 

_Solution to exercise 26_ 

1. _Note_ $x_0$ should be $0$. 
   $$
   \mathbb P_p[0\leftrightarrow(m+n)e_1]\ge\mathbb P_p[0\leftrightarrow me_1,me_1\leftrightarrow(m+n)e_1]\ge ^{\text{FKG}}\mathbb P_p[0\leftrightarrow me_1]\mathbb P_p[0\leftrightarrow ne_1]
   $$

2. Since $a_n:=-\log \mathbb P_p[0\leftrightarrow ne_1]$ satisfies $a_m+a_n\ge a_{m+n}$, by an analysis argument we know $\lim_{n \to \infty} a_n/n=\inf_n a_n/n$. 

3. Otherwise suppose $\xi(p)<c^{-1}$ for $p<p_c$, i.e., $a_n/n>c$, $\mathbb P_p[0\leftrightarrow ne_1]< e^{-cn}$. This shows $\mathbb P_p[0\overset {\Lambda_k}\leftrightarrow ne_1]<e^{-cn}$ for $k>n$. Since LHS is a polynomial of $p$, it's cts and we have $\mathbb P_{p_c}[0\overset{\Lambda_k}\leftrightarrow ne_1]\le e^{-cn}$. Push $k\to\infty$, we have $\mathbb P_{p_c}[0\leftrightarrow ne_1]\le e^{-cn}$. By argument as in 5, we have $\mathbb P_{p_c}[0\leftrightarrow x]\le e^{-cd\|x\|_\infty}$. This is enough to contradict to Remark 2.7.

4. By symmetry.

5. That is, $\sum_{xy\in\Delta\Lambda_n}\mathbb P_{p_c}[0\overset{\Lambda_n}\leftrightarrow x]\ge 1/p$. By Cauchy inequality and 4,
   $$
   |\Delta \Lambda_n|\mathbb P_{p_c}[0\leftrightarrow 2ne_1]\ge\sum_{xy\in \Delta \Lambda_n}\mathbb P_{p_c}[0\overset{\Lambda_n}\leftrightarrow x]^2\ge(p_c^2|\Delta\Lambda_n|)^{-1}
   $$
   that is, $\mathbb P_{p_c}[0\leftrightarrow 2ne_1]\ge (p_c|\Delta\Lambda_n|)^{-2}=Cn^{-2(d-1)}$ for some $C=C(d)>0$

   For $x=(x_1,...,x_d)$, Notice $0\leftrightarrow (x_1,0,...,0)\leftrightarrow(x_1,x_2,0,...,0)\leftrightarrow...\leftrightarrow (x_1,x_2,...,x_d)$ is an available path for $0\leftrightarrow x$. This gives us 
   $$
   \mathbb P_{p_c}[0\leftrightarrow x]\ge\prod_i \mathbb P_{p_c}[0\leftrightarrow x_ie_i]\ge\prod_i C(x_i/2)^{-2(d-1)}\ge C'\|x\|_\infty^{-2d(d-1)} 
   $$
   For finite-dim space, norms are equivalent. 

_Remark_ On the critical point, $\mathbb P_{p_c}[0\leftrightarrow x]$ decays more slowly than algebraically from 5. 

_proof of Lemma 2.11_

The proof looks confusing. Now I will clarify that. 

1. The decision tree

   We are discovering for $\mathbb 1(0\leftrightarrow \partial\Lambda_n)$ from the clusters intersecting $\partial\Lambda_k$, $k\le n$. Let the decision tree be as the following: Starting from $V_0=\partial\Lambda_k$ be the set of vertices explored and $F_0=\emptyset$ be the set of edges explored. Give an ordering for edges in $\Lambda_n$ for convenience. At time $t$, 

   - If there exists an edge $e=xy\in F\backslash F_t$, with $x\in V_t$ and $y\notin V_t$ (if more than one, pick the edge with smallest number), then if the edge is open, add $y$ to $V_t$ and $e$ to $F_t$, otherwise only add $e$ to $F_t$
   - If there isn't such an edge, then pick the smallest edge in $F\backslash F_t$ and add into $F_t$.

   Since the exploration in the first step will explore all clusters intersecting $\partial\Lambda_k$, it is sufficient to determine whether $0\leftrightarrow \partial\Lambda_n$, the tree will stop before entering the second step. This gives $\delta_e(\mathbb 1(0\leftrightarrow \Lambda_n), T_k)\le \mathbb P_p[u\leftrightarrow \partial\Lambda_k]+\mathbb P_p[v\leftrightarrow \partial\Lambda_k]$.

2. The family of decision trees provides a good estimation since it treats every layer of edges precisely. First, we have, by the continuity of path, 
   $$
   \sum_{k=1}^{n}\mathbb P_p[u\leftrightarrow \partial\Lambda_k]\le\sum_{k=1}^{n}\mathbb P_p[u\leftrightarrow\partial\Lambda_{|k-d(u,0)|}(u)]\le 2S_n
   $$
   Next, apply Theorem 2.9, 
   $$
   \begin{aligned}  
   \text{Var}_p(\mathbb 1(0\leftrightarrow\Lambda_n))&\le 2\sum_{e\in E}\delta_e(\mathbb 1(0\leftrightarrow\Lambda_n), T_k)\text{Cov}_p[\mathbb 1(0\leftrightarrow\Lambda_n),\omega_e]
   \\n\text{Var}_p(\mathbb 1(0\leftrightarrow\Lambda_n))&\le \sum_{k=1}^{n} 2\sum_{e\in E}\delta_e(\mathbb 1(0\leftrightarrow\Lambda_n), T_k)\text{Cov}_p[\mathbb 1(0\leftrightarrow\Lambda_n),\omega_e]\\&\le 2\sum_{k=1}^{n}\sum_{e\in E}(\mathbb P_p[u\leftrightarrow \partial\Lambda_k]+\mathbb P_p[v\leftrightarrow \partial\Lambda_k])\text{Cov}_p[\mathbb 1(0\leftrightarrow\Lambda_n),\omega_e]\\&\le4\sum_{e\in E}2S_n\text{Cov}_p[\mathbb 1(0\leftrightarrow\Lambda_n),\omega_e]
   \\\text{Var}_p(\mathbb 1(0\leftrightarrow\Lambda_n))&=\theta_n(1-\theta_n)
   \\\Rightarrow\sum_{e\in E}\text{Cov}_p[\mathbb 1(0\leftrightarrow\Lambda_n),\omega_e]&\ge\frac{n\theta_n(1-\theta_n)}{8S_n} 
   \end{aligned}
   $$

_Solution to exercise 27_ 

_Note_ The corrected model should be: $\eta_x\sim B(1-p)$ close all edges inside $B(x,R)$ (i.e., two vertices are inside it) for any $\eta_x=1$ and open the remain.

1. The model is constructed as follows: Assign i.i.d. $Bernoulli(1-p)$ on each vertex of $\mathbb Z^d$ and open all edges in $\bigcup_{x\in\mathbb Z^d} B(x,R)$. So for this model, edges are not independently open or closed, whence **Theorem 2.9** cannot be applied to edges. Instead, it should be applied to vertices, i.e.

   **Theorem** Consider $p\in[0,1]$ and a finite set of vertices $V$. For an increasing function $f:\{0,1 \}^V\to[0,1]$ and an algorithm $T$, we have 
   $$
   \text{Var}_p(f)\le 2\sum_{v\in V}\delta_v(f,T)\text{Cov}_p[f,\eta_e]
   $$

2. For **Lemma 2.11**, the decision tree should be constructed as follows

   - Let $f=\mathbb 1(0\nleftrightarrow\partial\Lambda_n)$. Fix $k\in[1,n]$. Order the points in $\partial\Lambda_n$. Start the decision tree at $\partial\Lambda_k$, to be more precise, let $V_0=\partial\Lambda_k$ and $F_0=\emptyset$.
   - If there exists an edge $e=xy\in F\backslash F_t$, with $x\in V_t$ and $y\notin V_t$ (if more than one, pick the edge with smallest number), then if $\eta_z=0\forall z\in B(x,R)\cup B(y,R)$, i.e., $e$ is open, add $y$ to $V_t$ and $e$ to $F_t$, otherwise only add $e$ to $F_t$.
   - If there isn't such an edge, then pick the smallest edge in $F\backslash F_t$ and add into $F_t$.

   Notice this algorithm determines $0\leftrightarrow \partial\Lambda_n$ before entering the second step. 

   For this algorithm, we have 
   $$
   \delta_v(T_k)\le \mathbb P[\exists z\in B(v,R+1): z\leftrightarrow \partial\Lambda_k]\le\sum_{z\in B(v,R+1)}\mathbb P[z\leftrightarrow\partial\Lambda_k]
   $$
   since if $v$ is checked, there must be $w\in B(v,R)$ waiting for entering $V_t$, and for $w$ be checked there must be one of its neighbors in $V_t$, i.e., connecting to $\partial\Lambda_k$. So we have 
   $$
   \sum_{k=1}^{n} \delta_v(T_k)\le 2CS_n
   $$
   where $C$ is the number of vertices in $B(0,R+1)$. This gives 
   $$
   \sum_{v\in V}\text{Cov}[\mathbb 1(0\leftrightarrow\Lambda_n),\delta_v]\ge\frac{n\theta_n(1-\theta_n)}{8CS_n} 
   $$

3. Now we consider $\theta_n'$. Similarly we have 
   $$
   \theta_n'(p)=\frac{1}{p(1-p)}\sum_{v\in V}\text{Cov}[\mathbb 1(0\leftrightarrow\partial\Lambda_n),\delta_v]\ge\frac{n}{8Cp(1-p)S_n}\theta_n(1-\theta_n)\ge\frac{n}{2CS_n}\theta_n(1-\theta_n)
   $$
   Fix $p_0\in (p_c,1)$ and $1-\theta_n(p)\ge 1-\theta_1(p_0)>0$. So one can apply **Lemma 2.10**. 

_Conclusion_ The main work is to convert the results on Bernoulli percolations (of edges) to that on vertices, and design an exploration algorithm. 

_Remark_ Why do we need OSSS? In some sense, the inequality naturally occurs the structure of the derivative of the expectation. 

_proof of theorem 2.12_ 

From 
$$
\text{Var}_{G,p,q}(f)\le \frac{\sum_{e\in E}\delta_e(f,T)\text{Cov}_{G,p,q}[f,\omega_e]}{\inf_{e\in E}\text{Var}_{G,p,q}(\omega_e)}
$$
Let $G=\Lambda_{2n}$, and sum over $T_k$, 
$$
n\text{Var}_{\Lambda_{2n},p,q}(\mathbb 1_{0\leftrightarrow\partial\Lambda_n})\le\frac{\sum_{k=1}^{n}\sum_{e\in E}\delta_e(\mathbb1_{0\leftrightarrow\partial\Lambda_n},T_k)\text{Cov}_{\Lambda_{2n},p,q}[\mathbb1_{0\leftrightarrow\partial\Lambda_n},\omega_e]}{\inf_{e\in E}\text{Var}_{G,p,q}(\omega_e)}
$$
and $\sum_{k=1}^n \delta_e(\mathbb 1_{0\leftrightarrow \partial\Lambda_n},T_k)\le \sum_{k=1}^n \phi[x\leftrightarrow\partial\Lambda_k]+\phi[y\leftrightarrow\partial\Lambda_k]$, we have 
$$
\sum_{e\in E_{2n}} \operatorname{Cov}_{\Lambda_{2n},p,q}\big(\mathbb{1}_{0\leftrightarrow \partial\Lambda_n},\omega_e\big) \ge\inf_e \operatorname{Var}_{\Lambda_{2n},p,q}(\omega_e)\frac{n\theta_n(1-\theta_n)}{2\max\limits_{x\in\Lambda_n}\sum\limits_{k=0}^{n-1}\phi^1_{\Lambda_{2n},p,q}\big[x\leftrightarrow \partial\Lambda_k(x)\big]}
$$
_Solution to exercise 28_ 

1. I can only argue this intuitively. If $\omega$ is a net, then 

2. We have $k(\omega)=k(\omega^*)+o(\omega^*)-2s(\omega^*)-|V|$, since $f(\omega^*)=k(\omega)+1$. This gives  
   $$
   \begin{aligned}
   \tilde\phi_{\mathbb T_n,p,q}(\omega)&=\sqrt{q}^{2s(w)}\frac{p^{o(\omega)}(1-p)^{c(\omega)}q^{k(\omega)}}{\tilde Z_{\mathbb T_n,p,q}^{per}}
   \\&=\frac{\sqrt{q}^{2s(\omega)}p^{|E|}}{\tilde Z_{\mathbb T_n,p,q}^{per}}(\frac{1-p}{p})^{c(\omega)}q^{k(\omega)}
   \\&=\frac{\sqrt{q}^{2s(\omega^*)}p^{|E|}}{\tilde Z_{\mathbb T_n,p,q}^{per}}(\frac{1-p}{p})^{o(\omega^*)}q^{k(\omega^*)+o(\omega^*)-2s(\omega^*)-|V|}
   \\&=\frac{\sqrt{q}^{2s(\omega^*)}p^{|E|}}{\tilde Z_{\mathbb T_n,p,q}^{per}}(\frac{p^*}{q(1-p)^*})^{o(\omega^*)}q^{k(\omega^*)+o(\omega^*)-2s(\omega^*)-|V|}
   \\&=\frac{\sqrt{q}^{2s(\omega^*)}p^{|E|}}{\tilde Z_{\mathbb T_n,p,q}^{per}q^{|V|}}(\frac{p^*}{(1-p)^*})^{o(\omega^*)}q^{k(\omega^*)-2s(\omega^*)}
   \end{aligned}
   $$

3. ==TBC==

_Solution to exercise 29_ 

1. Coupling by $uv$ open $\Leftrightarrow$ $xu,xv$ open. One can verify this coupling works in a triangle since $p^3+1=3p$. Notice that only one triangle is modified.

2. Recall exercise 24.1. Notice the dual graph of triangle lattice with $p$ is the hexagonal lattice with $1-p$. 

   When $p<p_c$, for a fixed point $x$ in the dual graph, there are only finitely many circuits surrounding it: The probability of $v$ a vertex in primal graph lies in some open circuits implies there is an open path of length at least $[\|v-x\|]+1$, which has probability no more than $\exp[-c \|v-x\|-1]$. The graph has $O(n)$ vertices that are in distance $n$ from $x$. So the probabilities are summable, by Borel Cantelli lemma there are only finite points that can lie in some open circuits surrounding $x$, i.e., such loops are finite. Then for a path in a dual graph from $x$ to connect to $\infty$, it needs only to modify finitely many edges, so the dual graph has a infinite cluster with positive probability, and by ergodicity it should be $1$. 

   On the other hand, by modifying the primal graph in the way that only one of two adjacent triangle is transformed as in 1, one can get a hexagonal lattice with parameter $1-p$ and connections are all remained. So in such graph, there isn't an infinite cluster almost surely. This leads to contradiction. 

3. The argument are nearly the same. 

   _Remark_ This has shown that the critical point of triangle lattice is $p$. 

4. $(1-p)^3+1=3(1-p)$.

5. Such argument still holds. 

   - If the measure on primal configuration is $\phi_{G,p,q}^0$, then for the dual configuration, it is $\phi_{G,p',q}^1$, where $\frac{pp'}{(1-p)(1-p')}=q$. One can go through the proof on $\mathbb Z^2$ to verify. 

   - To construct the same coupling as in 1, we consider one triangle, and compute the ratio of configuration weight ($p^{o(\omega)}(1-p)^{c(\omega)}q^{k(\omega)}$ or $p'^{o(\omega)}(1-p')^{c(\omega)}q^{k(\omega)}$) for different connection situations. For ease of notation let $s=p/(1-p)$ and $t=p'/(1-p')$, where $st=q$.

     | Case                  | left (compared with $(1-p)^3$) | right (compared with $(1-p')^3$)                             |
     | --------------------- | ------------------------------ | ------------------------------------------------------------ |
     | 3 vertices disconnect | $q^3$                          | $q^4$(u,v,w,x disconnect)+$3q^3t$ (one of w,x,v connects to x) |
     | two of them connect   | $3sq^2$                        | $3q^2t^2$ (two of u,v,w connect to x)                        |
     | all of them connect   | $(3s^2+s^3)q$                  | $qt^3$                                                       |

     To make it work, the ratio of each line should correspond (which liberate us from calculating $Z$), i.e., 
     $$
     q+3t=t^2/s=t^3/(3s^2+s^3)
     $$
     It's surprising to find that when $3s^2+s^3=q$, the identity holds. So such coupling exist. Moreover, such coupling keeps connection inside a triangle, so any outer BC doesn't affect its correctness. 

   - Now suppose the primal graph has wired BC. Then if $p<p_c$, as in the argument in 2, in the dual configuration $\sim\phi^0_{p',q}$ there is an infinite cluster. But in the coupling configuration $\sim \phi_{p',q}^1$ there is no infinite cluster. Since $\phi_{p',q}^1$ and $\phi_{p',q}^0$ has the same critical point, it is impossible. The same holds for $p>p_c$. So $p=p_c$. The same works for free BC.

   - As a conclusion, $s=p_c/(1-p_c)$ satisfies $3s^2+s^3=q$. 

_Solution to exercise 30_ 

_Note_ $\Lambda_n=\{x\in \mathbb G: \|x\|_\mathbb G\le n \}$.

1. _Recall_ For an amenable infinite locally-finite transitive graph, there is a unique infinite cluster a.s. or there isn't any infinite cluster a.s.. 

   Notice $\mathbb P_{p_c}[0\leftrightarrow\infty]>0\Rightarrow \mathbb P_c[\exists\text{unique infinite cluster}]=1$. And, $\mathbb P_{p_c}[x\leftrightarrow y]\ge \mathbb P_{p_c}[x\leftrightarrow\infty]\mathbb P_{p_c}[y\leftrightarrow\infty]\ge \mathbb P_{p_c}[0\leftrightarrow\infty]^2$ by transitivity. So it's bounded. 

2. A path connecting $0$ and $x\in\partial\Lambda_{m+n}$ must pass some $y\in\partial\Lambda_{m}$, and the path from $y$ to $x$ is sufficient for $x$ to connect to some point of $\partial\Lambda_{n}(x)$. The inequality follows from this fact and FKG inequality.  

3. Since the graph is locally finite, the first argument of two cases in theorem 2.4 also holds in this setting. This ensures $p_c=\tilde p_c$. For $p<\tilde p_c$, as in the argument of exercise 25.4, $\sum_{x\in\mathbb G}\mathbb P[0\leftrightarrow x]<\infty$. Notice the first step alone is not sufficient for this since we do not know the order of $|\partial\Lambda_n|$. 

4. If $u_n(p)>e^{-c_{vg} n}$ for some $n$, first pick $\alpha<c_{vg}$ s.t. $u_n(p)\ge e^{-\alpha n}$. Next,  $\exists c=c(p,n)>0: u_k(p)\ge c>0\forall k\le n$. By 2, $u_{ln}(p)\ge u_n(p)^l>e^{-\alpha nl}$ for all $l\ge 0$. This gives 
   $$
   \sum_{x\in\mathbb G}\mathbb P_p[0\leftrightarrow x]\ge \sum_{k=0}^\infty (|\Lambda_{n(k+1)}|-|\Lambda_{nk}|)cu_{kn}(p)\ge \sum_{k=0}^\infty |\Lambda_{n(k+1)}|cu_{kn}(p)-|\Lambda_{nk}|cu_{k(n-1)}(p)=\lim_{k \to \infty}|\Lambda_{n(k+1)}|cu_{kn}(p)-C_0
   $$
   Notice $|\Lambda_{n(k+1)}|u_{kn}(p)\ge e^{c_{vg}nk-\alpha nk}\to\infty$. This contradicts 3. 

5. From 4 one can conclude that $u_n(p_c)\le e^{-c_{vg}n}$ by arguing on $\Lambda_{k},k\ge n$. So $\inf_x\{\mathbb P_{p_c}[0\leftrightarrow x]\}=0$. By 1 we know this implies that there is no infinite cluster for $p=p_c$. 
