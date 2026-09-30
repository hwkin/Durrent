#### 4.1 An elementary argument in dimension $d=2$

_Solution to exercise 31_ 

First, we have concluded that for random-cluster model on $\mathbb Z^2$, there isn't an infinite cluster at critical point. Consider the coupling random-cluster model. For $A$, $B$ which depend on finitely many edges, as $\|x\|\to\infty$, $A,\tau_x B$ will depend on different clusters, and since the spins are i.i.d. uniform on each cluster, they will finally be independent. 

Rigorously, the argument is as following: 

For ease of notation, let $\mu:=\mu_{\beta_c}^\mathsf f$ and $\Phi=\phi_{p_c,2}^0$. Pick $S,T\subset \mathbb Z^2$ finite, and $A\in(\sigma_v)_{v\in S}, B\in(\sigma_v)_{v\in T}$. Let the coupling be $\mathbb P$. Define $f(\omega)=\mathbb P(A\mid\omega)$, $g(\omega)=\mathbb P(B\mid\omega)$, and $g_x(\omega)=\mathbb P(\tau_x B\mid\omega)$. We have $E_\Phi f(\omega)=\mu(A)$ and $E_\Phi g(\omega)=E_\Phi g_x(\omega)=\mu(B)$.

Now introduce $D_x=\{S\leftrightarrow x+T\}$ defined on the random-cluster. $\mathbb P(A\cap\tau_x B\mid \omega)\mathbb 1_{D_x^c}=f(\omega)g_x(\omega)1_{D_x^c}$ by the independence of spins on clusters. Take expectation, we have 
$$
|\mu(A\cap\tau_x B)-\mathbb E_\Phi[fg_x]|=|\mathbb P[A\cap\tau_x B]-\mathbb E_\Phi[fg_x]|=|\mathbb E_\Phi [\mathbb P(A\cap\tau_x B\mid\omega)-f(\omega)g_x(\omega)]\mathbb 1_{D_x}|\le 2\Phi(D_x)
$$
as $\|x\|\to\infty$, $\Phi(D_x)\to 0$ since there isn't an infinite cluster. 

Now it suffices to show $\mathbb E_\Phi[fg_x]\to \mathbb E_\Phi[f]\mathbb E_\Phi[g]$. Notice $f$ and $g$ are not local functions since $\sigma_i$'s are not independent. So one should approximate it by $f_n=\mathbb E_\Phi[f\mid \mathcal F_n]$ and $g_n=\mathbb E_\Phi[g\mid\mathcal F_n]$, where $\mathcal F_n=\sigma(\omega_e,e\in \Lambda_n)$. We have $f_n\xrightarrow{L^1} f$ and $g_n\xrightarrow{L^1}g$. By mixing we have $E\Phi[f_n (g_n)_x]\xrightarrow{\|x\|\to\infty}\mathbb E_\Phi f_n\mathbb E_\Phi g_n$. Moreover, $f_n(g_n)_x\xrightarrow{L^1}fg_x$ uniformly on $x$. This implies the expected result. 

_Solution to exercise 32_ 

First it's necessary to formalize those concepts, which will be quite different from random-cluster model. An event $A$ is increasing if $\delta\in A, \delta\le \delta'\Rightarrow\delta'\in A$. For BC $\xi,\xi'$, $\xi\le\xi'$ iff $\xi_x\le \xi'_x\forall x\in\partial G$. 

For the proof of CBC, mimic that of random-cluster model. Pick $v\in V\backslash\partial G$, let $S_v=\sum_{w\sim v}\sigma_w$, we have 
$$
\mu[\sigma_v=1\mid \sigma_x,x\ne v]=\frac{e^{\beta S_v}}{e^{\beta S_v}+e^{-\beta S_v}}=\frac{1}{1+e^{-2\beta S_v}}
$$
which is increasing as $S_v$ increases. Now take expectations on $V\backslash\partial G$, we have 
$$
\mu[\sigma_v=1\mid \sigma_x,x\in \partial G]=\mu[\frac{1}{1+e^{-2\beta S_v}}\mid \sigma_x,x\in \partial G]
$$
By repeatedly taking expectation on suitable spins, one can conclude that increasing $\sigma_x,x\in\partial G$ leads to the increase of $\mu[\sigma_v=1\mid \sigma_x,x\in \partial G]$. This concludes CBC. 

FKG follows similarly as in the argument before. 

_Explanation to proof of proposition 4.1_ 

**Proposition** On $\mathbb Z^2$, $\mu_{\beta_c}^+[\sigma_0]=0$.

1. From exercise 32 we know $\mu_{\beta_c}^\mathsf f$ is mixing. A mixing measure must be ergodic. From ergodicity, we know the events $\mathcal E_{\le 1}$, $\mathcal E_{<\infty}$, $\mathcal E_{=\infty}$, which represent that there is $\le 1$, $<\infty$, $=\infty$ infinite clusters, are all ergodic, so they have probability $0$ or $1$. Recall the coupling, we know the corresponding random-cluster configuration has more infinite clusters since it is attained by splitting the clusters of configuration in Ising model. This implies $\mu_{\beta_c}^\mathsf f(\mathcal E_{\le 1})=1$ in Ising model. _Remark_ This argument works also for $\beta<\beta_c$, but when $\beta>\beta_c$ the mixing property may fail.

2. Now instead of using edges to construct clusters, we use minuses. Let $\tilde{\mathcal H}_n$ be the event that there exists a path of minuses crossing from left to right. Notice $\tilde{\mathcal H}_n^c$ (maybe strictly) contains the event that there exists a path of pluses crossing from top to bottom, which has the same probability with $\tilde{\mathcal H}_n$, so $\mu_{\beta_c}^\mathsf f [\tilde{\mathcal H}_n]\le\frac12$. 

   Recall proposition 2.1. If there is an infinite cluster of minuses at $\beta_c$, consider $\Lambda_k$ and $\Lambda_n,n\ge k$. Since by exercise 32 FKG inequality holds, by square root trick we have $\mu_{\beta_c}^\mathsf f[\Lambda_k\leftrightarrow\text{Top of }\Lambda_n]\ge 1-(\mu_{\beta_c}^\mathsf f[\Lambda_k\nleftrightarrow\infty])^{1/4}$, moreover $\mu_{\beta_c}^\mathsf f[\Lambda_k\leftrightarrow\text{Top of }\Lambda_n,\Lambda_k\leftrightarrow\text{Bottom of }\Lambda_n]\ge 1-2(\mu_{\beta_c}^\mathsf f[\Lambda_k\nleftrightarrow\infty])^{1/4}$.(Notice $\leftrightarrow$ means connection by minuses.) Now pushes $n\to\infty$, the uniqueness of infinite cluster forces LHS tends to $\mu_{\beta_c}^\mathsf f[\tilde{\mathcal H}_n]$. Again, pushes $k\to\infty$, the existence of infinite cluster forces $RHS\to 1$. But we have claimed that $\mu_{\beta_c}^\mathsf f[\tilde{\mathcal H}_n]\le 1/2$, which is a contradiction. So at $\beta_c$ there isn't an infinite cluster. _Remark_ for any $\beta<\beta_c$, the argument also holds.

3. Now the goal is $\mu_{\beta_c}^+[\sigma_0]\le 0$. Below we only consider the clusters made up of minuses.

   Introduce $\mathsf C$ the collection of vertices in $\Lambda_n$ which are **not** connected to $\partial\Lambda_n$ by minuses. Conditioning on $\mathsf C=C$, which is measurable w.r.t. the spins outside $C$, the law of configuration is $\mu_{C,\beta_c}^+$ since the spins on $\partial C$ are all pluses. 

   > The Gibbs property (similar to DMP) comes from the form of Gibbs measure. For a term in numerator, $\exp[\beta\sum_{x\sim y}\sigma_x\sigma_y]$, it can be spilt into $\exp[\beta\sum_{x\sim y,\\ x,y\in C}\sigma_x\sigma_y]\exp[\beta\sum_{x\sim y,\\ x,y\in C^c\cup\partial C}\sigma_x\sigma_y]$, and the latter can be combined and cancelled by conditioning. So it can be reduced into a boundary condition.

   Now use the coupling, 
   $$
   \mu_{C,\beta_c}^+[\sigma_0]=\phi_{C,p_c,2}^1[0\leftrightarrow\partial C]\ge \phi_{p_c,2}^1[0\leftrightarrow\infty]=\mu_{\beta_c}^+[\sigma_0]
   $$
   Now sum up w.r.t. $\mathsf C$,
   $$
   \begin{aligned}
   0 = \mu^\mathsf f_{\beta_c}[\sigma_0] &= \mu^\mathsf f_{\beta_c}\big[\sigma_0 \mathbb{1}_{0 \notin \mathsf C}\big] + \sum_{0 \in C \subset \Lambda_n} \mu^+_{C,\beta_c}[\sigma_0] \mu^\mathsf f_{\beta_c}[\mathsf C=C] \\&\ge^1 -\mu^\mathsf f_{\beta_c}[0 \notin C] + \mu^+_{\beta_c}[\sigma_0] \sum_{0 \in C \subset \Lambda_n} \mu^\mathsf f_{\beta_c}[\mathsf C=C] \\&= -\mu^\mathsf f_{\beta_c}[0 \notin \mathsf C] + \mu^+_{\beta_c}[\sigma_0] \mu^\mathsf f_{\beta_c}[0 \in \mathsf C].
   
   \end{aligned}
   $$
   1: if $0\notin C$, $\sigma_0=-1$. The inequation comes from the above inequality.

   Now pushes $n\to\infty$. Since there isn't an infinite cluster, $\mu_{\beta_c}^\mathsf f[0\in \mathsf C]\to 1$. This shows $\mu_{\beta_c}^+[\sigma_0]\le 0$. 

4. In conclusion, $\mu_{\beta_c}^+[\sigma_0]= 0$. In other words, the phase transition is cts. 

_Solution to exercise 33_ 

1. For a Ising model configuration on $G^*$ with monochromatic BC $+$, open the edge in $G$ if its two nearest spins are opposite. One can verify that on the resulting subgraph every vertex has even degree (just check its nearest 4 spins). 

   For an even subgraph of $G$, set all spins on $\partial G^*$ to be $+$ and assign spins from outer to interior in the way that two spins divided by an open edge must be opposite, which is achievable. More formally, for $v\in V^*$, pick a path $\gamma$ in $E^*$ connecting $v$ to $\partial G^*$ and passes $N(\gamma)$ open edges in $G$, and assign $(-1)^{N(\gamma)}$ to $v$. $N(\gamma)$ is independent of choice since _an even graph can be decomposed into loops_, so pick $\gamma,\gamma'$ connecting $v$ to $\partial G^*$, $\gamma+\gamma'$ forms a loop (notice $\partial G^*$ can be seen as a point), which must cross any loop twice, giving $(-1)^{N(\gamma)+N(\gamma')}=1$. 

   This gives a correspondence. 

2. By the correspondence
   $$
   Z_\text{Ising}=\sum_\sigma \exp[\beta^*\sum_{xy}\sigma_x\sigma_y]=\sum_\eta\exp[\beta^*(|E|-o(\eta)-o(\eta))]=\exp[\beta^*|E|]\sum_\eta \exp[-2\beta^*o(\eta)]
   $$
   where $\eta$ is any even graph.

3. It happens when $\tanh(\beta)=\exp[-2\beta^*]$.

_Derivation of (4.4)_ 
$$
\begin{aligned}
\sum_{\sigma\in\{\pm 1\}^V}\sigma_A\exp[-\beta H_G^f(\sigma)]&=\sum_{\sigma\in\{\pm 1\}^V}\sigma_A\prod_{x\sim y}\sum_{\mathbf n_{xy}=0}^\infty\frac{(\beta \sigma_x\sigma_y)^{\mathbf n_{xy}}}{\mathbf n_{xy}!}
\\&=\sum_{\sigma\in\{\pm 1\}^V}\sigma_A\sum_{\mathbf n}\prod_{x\sim y}\frac{(\beta \sigma_x\sigma_y)^{\mathbf n_{xy}}}{\mathbf n_{xy}!}
\\&=\sum_{\sigma\in\{\pm 1\}^V}\sigma_A\sum_\mathbf n w_\beta(\mathbf n)\prod_{x\sim y}(\sigma_x\sigma_y)^{\mathbf n_{xy}}
\end{aligned}
$$
Also $\sigma_A\prod_{x\sim y}(\sigma_x\sigma_y)^{\mathbf n_{xy}}=\prod_x \sigma_x^{\sum_{y\sim x}\mathbf n_{xy}+\mathbb 1(x\in A)}$. When summing w.r.t. $\sigma$, only when $\sum_{y\sim x}\mathbf n_{xy}+\mathbb 1(x\in A)$ is even can $\mathbf n$​ survive, so 
$$
RHS=\sum_{\partial \mathbf n=A}w_\beta(\mathbf n) 2^{|V|}
$$
_Remark on identity 4.6_ we have shown $\mu_{G,\beta}^{f}[\sigma_A] = \phi_{G,p,2}^{0}[\mathcal{F}_A]$.

_Solution to exercise 34_ 

WLOG let them be distinct. By the switching lemma, we have 
$$
\mu[\sigma_1\sigma_2]\mu[\sigma_3\sigma_4]=\mu[\sigma_1\sigma_2\sigma_3\sigma_4]\mathbf P_{G,\beta}^{\{x_1,x_2\}\Delta \{x_3,x_4\}}[\mathcal F_{x_3,x_4}]=\mu[\sigma_1\sigma_2\sigma_3\sigma_4]\mathbf P_{G,\beta}^{\{x_1,x_2,x_3,x_4\}}[x_3\leftrightarrow x_4]
$$
So 
$$
U_4(x_1,x_2,x_3,x_4)=\mu[\sigma_1\sigma_2\sigma_3\sigma_4](1-\mathbf P_{G,\beta}^{\{x_1,x_2,x_3,x_4\}}[x_1\leftrightarrow x_2]-\mathbf P_{G,\beta}^{\{x_1,x_2,x_3,x_4\}}[x_1\leftrightarrow x_3]-\mathbf P_{G,\beta}^{\{x_1,x_2,x_3,x_4\}}[x_2\leftrightarrow x_3])
$$
Now notice that, the sum of degrees of vertices (i.e., $\sum_{x\sim y} \mathbf n_{xy}$ for $x$) on a connected component must be even since every unit current offers two degree. Since for any configuration with positive measure under $\mathbf P_{G,\beta}^A$, the set of vertices with odd degree is exactly $A$, so every connected component must intersect $A$ with even vertices. This forces that only these even can happen: 12 and 34 are in different clusters; 13 and 24 are in different clusters; 14 and 23 are in different clusters; 1234 are in the same clusters. So 
$$
\begin{aligned}
&\mathbf P_{G,\beta}^{\{x_1,x_2,x_3,x_4\}}[x_1\leftrightarrow x_2]+\mathbf P_{G,\beta}^{\{x_1,x_2,x_3,x_4\}}[x_1\leftrightarrow x_3]+\mathbf P_{G,\beta}^{\{x_1,x_2,x_3,x_4\}}[x_2\leftrightarrow x_3]
\\=&\mathbb E_\mathbf P \mathbb 1_{x_1\leftrightarrow x_2}+\mathbb 1_{x_1\leftrightarrow x_3}+\mathbb 1_{x_2\leftrightarrow x_3}
\\=&\mathbb E_\mathbf P 1+2\mathbb 1_{x_1\leftrightarrow x_2\leftrightarrow x_3\leftrightarrow x_4}
\\=&1+2\mathbf P_{G,\beta}^{\{x_1,x_2,x_3,x_4 \}}[x_i\text{ all connected}]
\end{aligned}
$$
which completes our proof. 

_Remark_ To make $\mathbf P_{G,\beta}^A$ a well-defined measure, $A$ must consists of even number of vertices (otherwise the denominator is 0) and every configuration with positive measure must satisfy that every cluster intersect $A$ for even times. 

_Solution to exercise 35_ 

Also, a current $\mathbf n$ on $G$ is a function from $E:=\{\{x,y\}: x,y\in V, J_{xy}\ne 0 \}$ to $\mathbb N$. The source of $\mathbf n$ is $\{x: \sum_{xy\in E}n_{xy}\text{ is odd} \}$, denoted by $\partial \mathbf n$. $w(\mathbf n)=\prod_{xy\in E}\frac{J_{xy}^{\mathbf n_{xy}}}{\mathbf n_{xy}!}$. In this case, $\exp(J_{xy} \sigma_x\sigma_y)=\sum_{\mathbf n_{xy}=0}^\infty \frac{(J_{xy}\sigma_x\sigma_y)^{\mathbf n_{xy}}}{\mathbf n_{xy}!}$ and $\sum_\sigma \sigma_A\exp(-H(\sigma))=2^{|V|}\sum_{\partial n=A} w(\mathbf n)$. The proof of the switching lemma goes well under this setting.

_Explanation to the paragraph after exercise 35_

It's saying that, the currents enter the definition of $\mathbf P_{G,\beta}^B$ only through their sources (which vertex has odd degree) and their traces (which edge has positive current), so it's sufficient to denote the currents by $0,1,2$, representing no current/ odd current/ positive and even current. But high-temperature expansion is not enough since it only involves the source and the number of open edges, which cannot distinguish whether the current is zero or positive even.

_Solution to exercise 36_ 

_Note_ The second measure should be proportional to $\sum_{\mathbf n\in\mathbb N^E,\partial\mathbf n=\emptyset}w_\beta(\mathbf n)\mathbb 1_{\hat{\mathbf n}=n}$.

1. According to the second distribution,
   $$
   \begin{aligned}
   P(n)&\propto\sum_{\eta\le n}\tanh(\beta)^{o(\eta)}\mathbb 1_{\partial\eta=\emptyset}(1-\frac{1}{\cosh \beta})^{o(n)-o(\eta)}(\frac{1}{\cosh\beta})^{|E|-o(n)}\\&\propto\sum_{\eta\le n}\mathbb 1_{\partial\eta=\emptyset}(\sinh\beta)^{o(\eta)}(\cosh\beta-1)^{o(n)-o(\eta)}
   \end{aligned}
   $$
   Notice every $\eta\le n$ with $\partial\eta=\emptyset$ corresponds to a collection of $\mathbf n$ where $n_e=0\Rightarrow \mathbf n_e=0$, $\eta_e=0,e\in n\Rightarrow \mathbf n_e\text{ is even}$ and $\eta_e=1,e\in n\Rightarrow \mathbf n_e\text{ is odd}$. So we have 
   $$
   \mathbb P_{G,\beta}^\emptyset[n]\propto\sum_{\mathbf n\in\mathbb N^E,\partial\mathbf n=\emptyset}w_\beta(\mathbf n)\mathbb 1_{\hat{\mathbf n}=n}=\sum_{\eta\le n}\prod_{\eta_e=0,e\in n}\sum_{\mathbf n_e\ge 2,\text{even}}\frac{\beta^{\mathbf n_e}}{\mathbf n_e!}\prod_{\eta_e=1,e\in n}\sum_{\mathbf n_e\text{ odd}}\frac{\beta^{\mathbf n_e}}{\mathbf n_e!}\prod_{e\notin n}1=\sum_{\eta\le n}(\cosh\beta -1)^{o(n)-o(\eta)}(\sinh\beta)^{o(\eta)}
   $$
   So they correspond.

2. This is a graph theory result. 

   > [!Note]
   >
   > A graph $\omega$ has $2^{|E|-|V|+k(\omega)}$ even subgraphs.
   >
   > _proof_ Pick a fixed spanning tree/forest $T$, which has $|V|-k(\omega)$ edges. Notice any subgraph on $E\backslash T$ corresponds to an even subgraph on $E$ : when the edges on $E\backslash T$ is determined, to make the degree on every vertex even, from leaf nodes one checks whether the edge connecting to father should be open. Then the edges on $T$ to be kept is uniquely determined. So there are $2^{|E\backslash T|}=2^{|E|-|V|+k(\omega)}$. 

   The distribution of $\eta$ can be obtained from
   $$
   \begin{aligned}
   P(\eta)&\propto\sum_{\omega\ge \eta}p^{o(\omega)}(1-p)^{|E|-o(\omega)}2^{k(\omega)}2^{-o(\omega)+|V|-k(\omega)}\\&\propto\sum_{\omega\ge\eta}(\frac{p}{2(1-p)})^{o(\omega)}
   =(\frac{p}{2(1-p)})^{o(\eta)}(1+\frac{p}{2(1-p)})^{|E|-o(\eta)}
   \\&\propto(\frac{p}{2-p})^{o(\eta)}=(\tanh\beta)^{o(\eta)}
   \end{aligned}
   $$
   

3. From the description, along with 2,
   $$
   \begin{aligned}
   P(n)&\propto\sum_{\eta\le n}\tanh(\beta)^{o(\eta)}\mathbb 1_{\partial\eta=\emptyset}(\tanh(\beta))^{o(n)-o(\eta)}(1-\tanh\beta)^{|E|-o(n)}
   \\&\propto\sum_{\eta\le n}(\frac{\tanh\beta}{1-\tanh\beta})^{o(n)}\mathbb 1_{\partial\eta=\emptyset}=\sum_{\eta\le n}\mathbb 1_{\partial\eta=\emptyset}(\frac{p}{2(1-p)})^{o(n)}=2^{o(n)-|V|+k(n)}(\frac{p}{2(1-p)})^{o(n)}
   \\&\propto (\frac{p}{1-p})^{o(n)} 2^{k(n)}
   \end{aligned}
   $$
   which is exactly $\phi_{G,\beta}^0$.

4. sample $n\sim \mathbb P_{G,\beta}^\emptyset$, independently open the additional edges with $p_1=1-\frac{1}{\cosh \beta}$, open the additional edges with $p_2=\tanh(\beta)$, and then the subgraph follows $\phi_{G,\beta}^0$.

5. By Kramers-Wannier duality, that law of interfaces is exactly the law of even subgraphs in the primal graph, which assign a subgraph $n$ with probability proportional to $\exp[-2\beta^* o(n)]$. pick $\beta$ s.t. $\tanh(\beta)=e^{-2\beta^*}$, that is exactly $\mathbf P_{G,\beta}^\emptyset$.
