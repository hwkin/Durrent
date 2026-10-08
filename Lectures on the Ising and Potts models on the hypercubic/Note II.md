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

_Solution to exercise 37_

_Note_ The inequality should be $\mu_\beta^\mathsf f[\sigma_0\sigma_x]\ge\mu_\beta^\mathsf f[\sigma_0\sigma_y]$.

1. The resulting $\mathbb L$ is a multigraph. If $xy\in E, xy\in \mathbb E$, then set $J_{xy}=\beta/2$ and if $xy\notin E, xy\in \mathbb E$, set $J_{xy}=\beta$.

   To make it easier, let $E'$ be the edges which are copied. 

2. Trivial.

3. ==TBC==

4. When $y=x+e_1$
   $$
   \begin{aligned}
   \mu_{G,\beta}^\mathsf f[\sigma_0\sigma_x]&=\frac{\sum_{\partial\mathbf n=\{0,x\}} w_\beta(\mathbf n)}{\sum_{\partial\mathbf n=\emptyset} w_\beta(\mathbf n)}\ge\frac{\sum_{\partial\mathbf n=\{0,y\}} w_\beta(\mathbf n)}{\sum_{\partial\mathbf n=\emptyset} w_\beta(\mathbf n)}=\mu_{G,\beta}^\mathsf f[\sigma_0\sigma_y]
   \end{aligned}
   $$
   By induction, C1 works. ==TBC==

5. Just by 4. 

_Derivation of 4.15_ 

_Note_ To make $P_{G,\beta}^\mathsf f[\eta]$ a probability measure, 
$$
P_{G,\beta}^\mathsf f[\eta]=\frac{\tanh(\beta)^{o(\eta)}\mathbb 1_{\partial\eta=\emptyset}}{\sum_{\partial\eta=\emptyset}\tanh(\beta)^{o(\eta)}}
$$
4.15 comes from 
$$
\begin{aligned}  
\mu_{G,\beta}^\mathsf f\big[e^{-\beta K_F}\big]&=\frac{\sum_{\sigma\in\{\pm 1\}^V}\exp[-\beta\sum_{xy\in F}\sigma_x\sigma_y]\exp[\beta\sum_{xy\in E}\sigma_x\sigma_y]}{\sum_{\sigma\in \{\pm 1\}^V}\exp[\beta\sum_{x\sim y}\sigma_x\sigma_y]}
\\&=\frac{\sum_{\sigma\in\{\pm 1\}^V}\exp[\beta\sum_{xy\in E\backslash F}\sigma_x\sigma_y]}{\sum_{\sigma\in \{\pm 1\}^V}\exp[\beta\sum_{x\sim y}\sigma_x\sigma_y]}
\\&=\frac{2^{|V|-|V_{E\backslash F}|}\sum_{\sigma\in\{\pm 1\}^{V_{E\backslash F}}}\exp[\beta\sum_{xy\in E\backslash F}\sigma_x\sigma_y]}{\sum_{\sigma\in \{\pm 1\}^V}\exp[\beta\sum_{x\sim y}\sigma_x\sigma_y]}
\\&=^\text{Prop.4.2}\frac{2^{|V|-|V_{E\backslash F}|}2^{|V_{E\backslash F}|}(\cosh\beta)^{|E|-|F|}\sum_{\partial\eta=\emptyset,\eta| F\equiv 0}(\tanh\beta)^{o(\eta)}}{2^{|V|}(\cosh\beta)^{|E|}\sum_{\partial\eta=\emptyset}(\tanh\beta)^{o(\eta)}}
\\&=\frac{\sum_{\partial\eta=\emptyset,\eta| F\equiv 0}(\tanh\beta)^{o(\eta)}}{(\cosh\beta)^{|F|}\sum_{\partial\eta=\emptyset}(\tanh\beta)^{o(\eta)}}
\\P_{G,\beta}^\mathsf f[\mathcal C_F]
&=\frac{\sum_{\partial\eta=\emptyset,\eta_{|F}\equiv 0}(\tanh\beta)^{o(\eta)}}{\sum_{\partial\eta=\emptyset}\tanh(\beta)^{o(\eta)}}
\end{aligned}
$$
_Remark on lemma 4.6_ $P_{G,\beta}^\mathsf f$ is the law of parity (with 1 odd and 0 even) of the random current on $G$.

_Remark on lemma 4.7_ The construction of trifurcations need to open and close edges, which is controllable by FE. But here only opening edges is controllable. So coarse trifurcations are considered, which only involves opening edges in $\Lambda_N$. Actually, we can go through the proof of theorem 1.10 since in that setting, if $a$ is a coarse trifurcation, one can construct a trifurcation of $a$ so the number of trifurcation in $\Lambda_n$, $n\gg N$ is less than $|\partial\Lambda_n|$, the upper bound for trifurcations, multiply $|\Lambda_N|$, since $a$ can be included in at most $\Lambda_N$ boxes of edge length $N$. 

_Solution to exercise 38_

To prove $\mathbb P_\beta^+[\omega_{xy}=1\mid \mathcal A]\ge c$ for some $c>0$, notice 
$$
\begin{aligned}
\frac{\mathbb P_\beta^+[\omega_{xy}=1\mid \mathcal A]}{\mathbb P_\beta^+[\omega_{xy}=0\mid \mathcal A]}
&=\frac{\displaystyle\sum_{\omega_{xy}=1, \omega\in \mathcal A}\displaystyle\sum_{\substack{\partial \mathbf{n}_1 \cap \mathrm{int}(V)=\emptyset \\ \partial \mathbf{n}_2=\emptyset}} w_\beta(\mathbf{n}_1) w_\beta(\mathbf{n}_2)\mathbb{1}_{\widehat{\mathbf{n}_1+\mathbf{n}_2}=\omega}}{\displaystyle\sum_{\omega_{xy}=0,\omega\in \mathcal A}\displaystyle\sum_{\substack{\partial \mathbf{n}_1 \cap \mathrm{int}(V)=\emptyset \\ \partial \mathbf{n}_2=\emptyset}} w_\beta(\mathbf{n}_1) w_\beta(\mathbf{n}_2) \mathbb{1}_{\widehat{\mathbf{n}_1+\mathbf{n}_2}=\omega}}
\end{aligned}
$$
Notice
$$
\begin{aligned}
&(\cosh\beta-1)^2\displaystyle\sum_{\omega_{xy}=0,\omega\in \mathcal A}\displaystyle\sum_{\substack{\partial \mathbf{n}_1 \cap \mathrm{int}(V)=\emptyset \\ \partial \mathbf{n}_2=\emptyset}} w_\beta(\mathbf{n}_1) w_\beta(\mathbf{n}_2) \mathbb{1}_{\widehat{\mathbf{n}_1+\mathbf{n}_2}=\omega}
\\\le&\displaystyle\sum_{\omega_{xy}=0,\omega\in \mathcal A}\displaystyle\sum_{\substack{\partial \mathbf{n}_1 \cap \mathrm{int}(V)=\emptyset \\ \partial \mathbf{n}_2=\emptyset}} w_\beta(\mathbf{n}_1)(\cosh\beta-1)\  w_\beta(\mathbf{n}_2) \mathbb{1}_{\widehat{\mathbf{n}_1+\mathbf{n}_2}=\omega}(\cosh\beta-1)
\\=&\displaystyle\sum_{\omega_{xy}=0,\omega\in \mathcal A}\displaystyle\sum_{\substack{\partial \mathbf{n}_1 \cap \mathrm{int}(V)=\emptyset \\ \partial \mathbf{n}_2=\emptyset}} w_\beta(\mathbf{n}_1)\sum_{\mathbf n_{1xy}>0\text{ is even}}\frac{\beta^{\mathbf n_{1xy}}}{\mathbf n_{1xy}!} w_\beta(\mathbf{n}_2) \mathbb{1}_{\widehat{\mathbf{n}_1+\mathbf{n}_2}=\omega}\sum_{\mathbf n_{2xy}>0\text{ is even}}\frac{\beta^{\mathbf n_{2xy}}}{\mathbf n_{2xy}!}
\\\le&\displaystyle\sum_{\omega_{xy}=1,\omega\in \mathcal A}\displaystyle\sum_{\substack{\partial \mathbf{n}_1 \cap \mathrm{int}(V)=\emptyset \\ \partial \mathbf{n}_2=\emptyset}} w_\beta(\mathbf{n}_1) w_\beta(\mathbf{n}_2) \mathbb{1}_{\widehat{\mathbf{n}_1+\mathbf{n}_2}=\omega}
\end{aligned}
$$
So the ratio is greater than $(\cosh\beta-1)^2$, which indicates IT.

_Solution to exercise 39_ 

1. Set $w_{\beta,h}(\mathbf n)=\prod_{xy\in E}\frac{\beta^{\mathbf n_{xy}}}{\mathbf n_{xy}!}\prod_{x\mathfrak g}\frac{h^{\mathbf n_{x\mathfrak g}}}{\mathbf n_{x\mathfrak g}!}$. One have 
   $$
   \begin{aligned}  
   \sum_{\sigma}\sigma_A\exp[-H_{G,h}(\sigma)]&=\sum_\sigma\sigma_A\prod_{xy}\exp[\beta\sigma_x\sigma_y]\prod_{x\mathfrak g}\exp[h\sigma_x]
   \\&=\sum_\sigma\sigma_A\prod_{xy}\sum_{\mathbf n_{xy}=0}^\infty\frac{(\beta\sigma_x\sigma_y)^{\mathbf n_{xy}}}{\mathbf n_{xy}!}\prod_{x\mathfrak g}\sum_{\mathbf n_{x\mathfrak g}=0}^\infty\frac{(h\sigma_x)^{\mathbf n_{x\mathfrak g}}}{\mathbf n_{x\mathfrak g}!}
   \\&=\sum_\mathbf n \sigma_A\prod_{xy}\frac{(\beta\sigma_x\sigma_y)^{\mathbf n_{xy}}}{\mathbf n_{xy}!}\prod_{x\mathfrak g}\frac{(h\sigma_x)^{\mathbf n_{x\mathfrak g}}}{\mathbf n_{x\mathfrak g}!}
   \\&=2^{|V|}\sum_{\partial\mathbf n=A}w_{\beta,h}(\mathbf n)
   \end{aligned}
   $$
   Note that, the degree of $x$ is $\sum_{x\sim y}\mathbf n_{xy}+\mathbf n_{x\mathfrak g}$. Notice the source can contain odd number of vertices (in this case, $\mathfrak g$ is a source.)

2. First use the representation expressed in 1,
   $$
   \begin{aligned}
   \mu_{\beta,h}^\mathsf f[\sigma_x\sigma_0]-\mu_{\beta,h}^\mathsf f[\sigma_x]\mu_{\beta,h}^\mathsf f[\sigma_0]&=\frac{\displaystyle\sum_{\partial\mathbf n=\{0,x\}}w_{\beta,h}[\mathbf n]}{\displaystyle\sum_{\partial\mathbf n=\emptyset}w_{\beta,h}[\mathbf n]}-\frac{\displaystyle\sum_{\partial\mathbf n=\{x\}}w_{\beta,h}[\mathbf n]}{\displaystyle\sum_{\partial\mathbf n=\emptyset}w_{\beta,h}[\mathbf n]}\frac{\displaystyle\sum_{\partial\mathbf n=\{0\}}w_{\beta,h}[\mathbf n]}{\displaystyle\sum_{\partial\mathbf n=\emptyset}w_{\beta,h}[\mathbf n]}
   \\&=\frac{\displaystyle\sum_{\partial\mathbf n_1=\{0,x\}\\\partial\mathbf n_2=\emptyset}w_{\beta,h}[\mathbf n_1]w_{\beta,h}[\mathbf n_2]}{\displaystyle\sum_{\partial\mathbf n_1=\emptyset\\\partial\mathbf n_2=\emptyset}w_{\beta,h}[\mathbf n_1]w_{\beta,h}[\mathbf n_2]}-\frac{\displaystyle\sum_{\partial\mathbf n_1=\{x\}\\\partial\mathbf n_2=\{0\}}w_{\beta,h}[\mathbf n_1]w_{\beta,h}[\mathbf n_2]}{\displaystyle\sum_{\partial\mathbf n_1=\emptyset\\\partial\mathbf n_2=\emptyset}w_{\beta,h}[\mathbf n_1]w_{\beta,h}[\mathbf n_2]}
   \\&=^\text{switching}\frac{\displaystyle\sum_{\partial\mathbf n_1=\{0,x\}\\\partial\mathbf n_2=\emptyset}w_{\beta,h}[\mathbf n_1]w_{\beta,h}[\mathbf n_2]\mathbb 1_{\widehat {\mathbf n_1+\mathbf n_2}\notin\mathcal F_{x,\mathfrak g}}}{\displaystyle\sum_{\partial\mathbf n_1=\emptyset\\\partial\mathbf n_2=\emptyset}w_{\beta,h}[\mathbf n_1]w_{\beta,h}[\mathbf n_2]}
   \end{aligned}
   $$
   So the measure is 
   $$
   P[\eta]=\frac{\displaystyle\sum_{\partial\mathbf n_1=\{0,x\}\\\partial\mathbf n_2=\emptyset}w_{\beta,h}[\mathbf n_1]w_{\beta,h}[\mathbf n_2]\mathbb 1_{\widehat {\mathbf n_1+\mathbf n_2}=\eta}}{\displaystyle\sum_{\partial\mathbf n_1=\emptyset\\\partial\mathbf n_2=\emptyset}w_{\beta,h}[\mathbf n_1]w_{\beta,h}[\mathbf n_2]}
   $$
   And under this measure, $\widehat{\mathbf n_1+\mathbf n_2}\notin \mathcal F_{x,\mathfrak g}$ is the event that $x$ connects to $0$ but not connecting to $\mathfrak g$. 

3. If $x\leftrightarrow 0$ but $x\nleftrightarrow \mathfrak g$, then the cluster $\mathcal C$ intersecting $0$ and $x$ (in $G$) has every edge connecting to $\mathfrak g$ closed, which by IT happens with probability less than $(1-c_{IT})^{|\mathcal C|}$, decays exponentially fast as $|x|\to\infty$.

_Solution to exercise 40_ 

_Note_ it should be that $S$ disconnecting $x$ from $z$. 

For the first inequality,
$$
\begin{aligned}
\sum_{y\in S}\mu_{G,\beta}^\mathsf f[\sigma_x\sigma_y]\mu_{G,\beta}^\mathsf f[\sigma_y\sigma_z]&=\sum_{y\in S}\frac{\sum_{\partial\mathbf n=\{x,y\}}w_\beta(\mathbf n)}{\sum_{\partial\mathbf n=\emptyset}w_\beta(\mathbf n)}\frac{\sum_{\partial\mathbf n=\{y,z\}}w_\beta(\mathbf n)}{\sum_{\partial\mathbf n=\emptyset}w_\beta(\mathbf n)}
\\&=^\text{switching}\sum_{y\in S}\frac{\sum_{\partial\mathbf n_1=\{x,z\}\\\partial\mathbf n_2=\emptyset}w_\beta(\mathbf n_1)w_\beta(\mathbf n_2)\mathbb 1_{\mathcal F_{xy}}}{\sum_{\partial\mathbf n_1=\emptyset\\\partial\mathbf n_2=\emptyset}w_\beta(\mathbf n_1)w_\beta(\mathbf n_2)}
\\&\ge\frac{\sum_{\partial\mathbf n_1=\{x,z\}\\\partial\mathbf n_2=\emptyset}w_\beta(\mathbf n_1)w_\beta(\mathbf n_2)}{\sum_{\partial\mathbf n_1=\emptyset\\\partial\mathbf n_2=\emptyset}w_\beta(\mathbf n_1)w_\beta(\mathbf n_2)}=\mu_{G,\beta}^\mathsf f[\sigma_z\sigma_z]
\end{aligned}
$$
where the last line comes from the fact that when $\partial\mathbf n_1=\{x,z\}$ and $\partial\mathbf n_2=\emptyset$, $\widehat{\mathbf n_1+\mathbf n_2}$ connects $x$ and $z$, which must meet some $y\in S$. 

_Note_ The right form of Lieb's inequality is: Let $D\subset V(G)$, $x\in D$, $y\notin D$. Define $S:=\partial_{in}D=\{y\in D:\exists v\notin D,yv\in E(G)\}$. Then the Lieb's inequality says
$$
\mu_{G,\beta}^\mathsf f[\sigma_x\sigma_z]\le\sum_{y\in S}\mu_{D,\beta}^\mathsf f[\sigma_x\sigma_y]\mu_{G,\beta}^\mathsf f[\sigma_y\sigma_z]
$$
Let $\mathbf n_1$ be supported on $E_D$. First we have
$$
\sum_{y\in S}\mu_{D,\beta}^\mathsf f[\sigma_x\sigma_y]\mu_{G,\beta}^\mathsf f[\sigma_y\sigma_z]=\sum_{y\in S}\frac{\sum_{\partial\mathbf n_1=\{x,y\}}w_\beta(\mathbf n_1)}{\sum_{\partial\mathbf n_1=\emptyset}w_\beta(\mathbf n_1)}\frac{\sum_{\partial\mathbf n=\{y,z\}}w_\beta(\mathbf n)}{\sum_{\partial\mathbf n=\emptyset}w_\beta(\mathbf n)}
$$
And decompose the second, where $\mathbf n_1$ is supported on $E_D$, and $\mathbf n_2$ is supported on $E\backslash E_D$.
$$
\frac{\sum_{\partial\mathbf n=\{y,z\}}w_\beta(\mathbf n)}{\sum_{\partial\mathbf n=\emptyset}w_\beta(\mathbf n)}=\frac{\sum_{T\subset D}\sum_{\partial\mathbf n_1=\{y\}\Delta T\\\partial\mathbf n_2=\{z\}\Delta T}w_\beta(\mathbf n_1)w_\beta(\mathbf n_2)}{\sum_{T\subset D}\sum_{\partial\mathbf n_1=T\\\partial\mathbf n_2=T}w_\beta(\mathbf n_1)w_\beta(\mathbf n_2)}
$$
Then use the switching lemma, notice $\mathbf n_1,\mathbf n_2$ are supported on $E_D$ and $\mathbf n_3$ is supported on $E\backslash E_D$.
$$
\begin{aligned}  
\sum_{y\in S}\mu_{D,\beta}^\mathsf f[\sigma_x\sigma_y]\mu_{G,\beta}^\mathsf f[\sigma_y\sigma_z]&=\sum_{y\in S}\frac{\sum_{T\subset D}\sum_{\mathbf \partial \mathbf n_1=\{x\}\Delta T\\\partial\mathbf n_2=\emptyset\\\partial\mathbf n_3=\{z\}\Delta T}w_\beta(\mathbf n_1)w_\beta(\mathbf n_2)w_\beta(\mathbf n_3)\mathbb 1_{\widehat{\mathbf n_1+\mathbf n_2}\in\mathcal F_{xy}}}{\sum_{T\subset D}\sum_{\mathbf \partial \mathbf n_1=T\\\partial\mathbf n_2=\emptyset\\\partial\mathbf n_3=T}w_\beta(\mathbf n_1)w_\beta(\mathbf n_2)w_\beta(\mathbf n_3)}
\\&\ge \frac{\sum_{T\subset D}\sum_{\mathbf \partial \mathbf n_1=\{x\}\Delta T\\\partial\mathbf n_2=\emptyset\\\partial\mathbf n_3=\{z\}\Delta T}w_\beta(\mathbf n_1)w_\beta(\mathbf n_2)w_\beta(\mathbf n_3)}{\sum_{T\subset D}\sum_{\mathbf \partial \mathbf n_1=T\\\partial\mathbf n_2=\emptyset\\\partial\mathbf n_3=T}w_\beta(\mathbf n_1)w_\beta(\mathbf n_2)w_\beta(\mathbf n_3)}
\\&= \frac{\sum_{T\subset D}\sum_{\mathbf \partial \mathbf n_1=\{x\}\Delta T\\\partial\mathbf n_3=\{z\}\Delta T}w_\beta(\mathbf n_1)w_\beta(\mathbf n_3)}{\sum_{T\subset D}\sum_{\mathbf \partial \mathbf n_1=T\\\partial\mathbf n_3=T}w_\beta(\mathbf n_1)w_\beta(\mathbf n_3)}
\\&=\frac{\sum_{\partial\mathbf n=\{x,z\}}w_\beta(\mathbf n)}{\sum_{\partial\mathbf n=\emptyset}w_\beta(\mathbf n)}=\mu_{G,\beta}^\mathsf f[\sigma_z\sigma_x]
\end{aligned}
$$
The first inequality goes as above: When $\partial\mathbf n_1=\{x\}\Delta T,\partial\mathbf n_2=\emptyset,\partial\mathbf n_3=\{z\}\Delta T$,$\partial\mathbf n_1+\mathbf n_2+\mathbf n_3=\{x,z\}$, indicating that there must be a path from $x$ to $z$, which must wind through some vertex in $S$ through $E_D$. So the sum of indicators must be no less than 1.

_Explanation to the proof of Theorem 4.8_ 

1. The infrared bound says, $\mu_{\beta_c}^\mathsf f[\sigma_x\sigma_y]\le\frac{C}{\beta_c}G(x,y)$. When $d\ge 3$, $G(x,y)\sim \|x-y\|^{2-d}$.

2. The Simon's inequality proven above (replace $S$ by $\partial\Lambda_n$) gives us that, when $x\notin \Lambda_n$, 
   $$
   \mu_{\beta}^{\mathbf f}[\sigma_{0}\sigma_{x}]\leq\sum_{y\in\partial\Lambda_{n}}\mu_{\beta}^{\mathbf f}[\sigma_{0}\sigma_{y}]\,\mu_{\beta}^{\mathbf f}[\sigma_{y}\sigma_{x}]
   $$
   Assume that $\varphi_\beta(\Lambda_n):=\sum_{y\in\partial\Lambda_n}\mu_\beta^\mathsf f[\sigma_0\sigma_y]<1$ for some $n$ at a fixed $\beta$. Recall the proof of exponential decay at subcritical $p$ in Bernoulli percolation using $\varphi_p(S)$, for $x\in\partial\Lambda_{kn}$, use above inequality, and notice
   $$
   \mu_\beta^\mathsf f[\sigma_y\sigma_x]=\phi_p^0[y\leftrightarrow x]\le\max_{z\in \partial\Lambda_{(k-1)n}} \phi_p^0[0\leftrightarrow z]=\max_{z\in\partial\Lambda_{(k-1)n}}\mu_{\beta}^\mathsf f[\sigma_0\sigma_z]
   $$
   So $\mu_\beta^\mathsf f[\sigma_0\sigma_x]\le\varphi_\beta(\Lambda_n)^k$. 

3. $\beta\to\mu_\beta^+[\sigma_0\sigma_x]$ is right-cts, so
   $$
   \operatorname*{lim}_{\beta\searrow\beta_{c}}\varphi_\beta(\Lambda_{n})\leq\operatorname*{lim}_{\beta\searrow\beta_{c}}\sum_{y\in\partial\Lambda_{n}}\mu_{\beta}^{+}[\sigma_{0}\sigma_{y}]=\sum_{y\in\partial\Lambda_{n}}\mu_{\beta_{c}}^{+}[\sigma_{0}\sigma_{y}]=\varphi_{\beta_{c}}(\Lambda_{n})
   $$
   the inequality comes from $\mu_\beta^\mathsf f\le\mu_\beta^+$. The last inequality comes from $\mu_{\beta_c}^\mathsf f=\mu_{\beta_c}^\mathsf f$, since at $\beta_c$, when $d\ge 3$, the infrared bound indicates that $\operatorname{LRO}_\beta$ doesn't hold, which, by the proof of **Theorem 4.4**, indicates that $\mu_{\beta_c}^\mathsf f[\sigma_x\sigma_y]=\mu_{\beta_c}^\mathsf f[\sigma_x\sigma_y]$ for any $x,y$.

   So if $\varphi_{\beta_c}(\Lambda_n)<1$, then by right-cts, for some $\beta>\beta_c$, $\varphi_\beta(\Lambda_n)<1$, i.e., at $\beta$ the correlation is decaying exponentially, but at supercritical case the correlations have a positive lower bound, so there is a contradiction. So $\varphi_{\beta_c}(\Lambda_n)\ge 1$. 

4. The Mes-Mir gives that, when $y\in\partial\Lambda_n$, $\mu_{\beta_c}^\mathsf f[\sigma_0\sigma_{ne_1}]\ge\mu_{\beta_c}^\mathsf f[\sigma_0\sigma_y]$, which indicates $\mu_{\beta_c}^\mathsf f[\sigma_0\sigma_{ne_1}]\ge \frac{1}{|\partial\Lambda_n|}$ for every $n$, which gives the left side. 

### 5 Continuity/Discontinuity of the phase transition for the planar random-cluster model

_Remark_ We've proven that $\phi_{p_c,q}^0[0\leftrightarrow\infty]=0$ for $q\ge 1$. 

_Solution to exercise 41_

1. Draw it and conclude.

2. By independence and 1,
   $$
   \mathbb P_p[\mathcal H(2n,4n)]\le\mathbb P_p[\mathcal H(n,4n)]^2\le 25\mathbb P_p[\mathcal H(n,2n)]^2
   $$

3. If for some $n$, $u_n<1/25$, then by 2, $u_{2^k n}\to 0$ as $k\to\infty$, and since $u_n$ is decreasing, $u_n\to 0$. Then for $y\in\partial\Lambda_{2n}$, $\mathbb P_p[0\leftrightarrow y]\le 8u_n\to 0$. This is EXP.

_Remark for the inequality at the end of Page 51_ $\mathcal V(S_i)$ is introduced to make the paths invoking $\mathcal H(R_i),i\le \rho$ join into a path connecting the very left and very right sides.

_Solution to exercise 42_ Consider $\Omega/\delta\cap\mathbb Z^2$, as $\delta$ decreases the graph is larger and larger. Pick $\delta$ small enough, then cover it with a rectangle of edge length $n$, $\rho n$, such that the rectangle intersects $(a_\delta b_\delta)$ and $(c_\delta d_\delta)$ but not intersecting $(b_\delta c_\delta)$ and $(a_\delta d_\delta)$. Then the lower bound is controlled by that of the rectangle.

_Illustration to the dual boundary condition in Prop.5.4_ ![](C:\Users\m1500\Desktop\Durrent\images\prop54-boundary-wiring.png)

_Solution to exercise 43_ 

1. By symmetry and FKG,
   $$
   \mu[\mathcal H(6n,2n)]\ge\mu[\{-n\}\times[-n,n]\leftrightarrow(n,n)\cap (n,n)\leftrightarrow\{3n\}\times[-n,n]\cap\{n\}\times[-n,n]\leftrightarrow(n,3n)\cap(n,3n)\leftrightarrow\{5n\}\times[-n,n]]\ge \mu[\mathcal E_n]^4
   $$

2. $h_n$ is trivially increasing. $h_n(n)=\mu[\mathcal F_n(0,n)]-\mu[\mathcal F_n(n,n)]$. By symmetry, $2\mu[\mathcal F_n(0,n)]\ge\mu[\mathcal H(2n)]\ge c>0$. Moreover, $\mu[\mathcal F_n(n,n)]\to 0$ by assumption. So it has a uniform lower bound. 

3. First, we have $\mu[\mathcal F(n/2,n)]\ge c_0/4$. Consider the picture. In 1, $\mu[a\leftrightarrow b]\ge(c_0/4)^2$; In 2, $\mu[a\leftrightarrow b]\ge (c_0/4)^3$; In 3, $\mu[\mathcal H(6n,2n)]\ge (c_0/4)^2(c_0/4)^3(c_0/4)^3(c_0/4)^3(c_0/4)^2$. _remark_ Such argument fails for $\mathcal F(0,n/2)$, since one can find it hard for paths to move towards right. ![](C:\Users\m1500\Desktop\Durrent\images\exercise 43.png)

4. In this case, $\mu[\mathcal F_n(\alpha_n,n)]\ge c_0/4$. Pick the paths connecting left edge to the right upper 1/4 edge, connecting left edge to the right lower 1/4 edge, connecting right edge and left upper 1/4 edge, connecting right edge and left lower 1/4 edge, and connecting top edge and bottom edge, they can make $\mathcal X_n$ happen. So $\mu[\mathcal X(n)]\ge (c_0/4)^4c_0$.

5. Otherwise $\alpha_n\ge 2\alpha_{2n/3}$, which finally leads to $\alpha_n\gg n$, but $\alpha_n\le n$.

6. ==TBC==

_Explanation to the proof of Proposition 5.6_ 

$\mathbf {P3}\Rightarrow\mathbf {P4a}$ First, notice $\phi_{p_c,q}^0[0\leftrightarrow \partial\Lambda_n]$ is sub-mulplicative, so $\lim_{n \to \infty}\frac{1}{n^{1/3}}\log\phi_{p_c,q}^0[0\leftrightarrow\partial\Lambda_n]$ exists. If the limit is nonzero, there is some $c>0$ such that $\phi_{p_c,q}^0[0\leftrightarrow\partial\Lambda_n]\le \exp[-c n^{1/3}]$. Then 
$$
\sum_{x\in\mathbb Z^2}\phi_{p_c,q}^0[0\leftrightarrow x]\le C\sum_n n\phi_{p_c,q}^0[0\leftrightarrow\Lambda_n]\le C\sum_n ne^{-cn^{1/3}}<\infty
$$
which contradicts the divergence. 

_Remark_ The power $1/3$ is chosen for later equivalence, here it's not critical.

$\mathbf {P4a}\Rightarrow\mathbf {P4b}$ Trivial

$\mathbf {P1}\Rightarrow\mathbf {P2}$ Use Exercise 16. Fix an infinite-volume random-cluster measure $\phi$. For any event $A$ determined on finite many edges, WLOG $\Lambda_n$, pick $\mathcal C$ be the union of all finite clusters intersecting $\Lambda_n$. then $\phi[\mathcal C=C]$, $|C|<\infty$ is determined by the edges in $C$ and around $C$, by the property of $\phi$, $\phi[A,\mathcal C=C]=\phi_{C,p_c,q}^0[A,\mathcal C=C]$, which is unique. Sum over $C$, $\phi[A]$ is unique (Notice $\phi^0\le\phi\le\phi^1$ implies $\phi[0\leftrightarrow\infty]=0$, so summing over $C$ results on $\phi[A]$). This implies the uniqueness of $\phi$, which, by exercise 16, implies $\phi_{p_c,q}^0=\phi_{p_c,q}^1$. 

_Solution to exercise 44_ 

1. Contrary to the proof of $\mathbf {P5}\Rightarrow\mathbf {P1}$, which used wired BC to join $\partial\Lambda_{4n}\leftrightarrow\partial\Lambda_n$ together, here for safety we put all things together and apply FKG, and avoid using any local BC, so that the argument can hold. First, by $\mathbf {P5}$ and DMP we have $\phi_{p_c,q}^0[\mathcal H(\rho n,n)]\in[c,1-c]$.

   Now construct a circuit and a path to connect the inner path to outer. Consider $R_1=[-n,n]\times[n/2,n]$ and $R_2,R_3,R_4$ rotated by $\pi/2,\pi,3\pi/2$. Then $\mathcal H(R_1)\cap\mathcal V(R_2)\cap\mathcal H(R_3)\cap\mathcal V(R_4)$ implies that there is a circuit in $\Lambda_n\backslash\Lambda_{n/2}$. Pick $R_5=[n/3,5n/2]\times[-n/2,n/2]$, then $\{0\leftrightarrow\partial\Lambda_n\}\cap\mathcal H(R_1)\cap\mathcal V(R_2)\cap\mathcal H(R_3)\cap\mathcal V(R_4)\mathcal H(R_5)$ implies that $0$ connects to $\partial\Lambda_{2n}$. By FKG inequality, 
   $$
   \phi_{p_c,q}^0[0\leftrightarrow\partial\Lambda_{2n}]\ge \phi_{p_c,q}^0[\{0\leftrightarrow\partial\Lambda_n\}\cap\mathcal H(R_1)\cap\mathcal V(R_2)\cap\mathcal H(R_3)\cap\mathcal V(R_4)\mathcal H(R_5)]\ge \phi_{p_c,q}^0[0\leftrightarrow\partial\Lambda_n]c_1^4c_2
   $$
   where $c_1$ is for $R_1$ and $c_5$ is for $R_5$.

2. For the left side, let $\Lambda_n(x)$ be the square translated from $\Lambda_n$ by $x$. like 1, Let $C_n(x)$ be the event that there is a circuit in $\Lambda_n(x)\backslash \Lambda_{4n/5}(x)$, then $\phi_{p_c,q}^0[C_n(x)]\ge c(10)^4$. Then by FKG and translation-invariance, we have 
   $$
   \phi_{p_c,q}^0[0\leftrightarrow x]\ge \phi_{p_c,q}^0[0\leftrightarrow\partial\Lambda_n\cap x\leftrightarrow\partial\Lambda_{n}(x)\cap C_n(0)\cap C_n(x)]\ge c(10)^8\phi_{p_c,q}^0[0\leftrightarrow\partial\Lambda_n]^2
   $$
   For the right side, for ease of notation, pick $r=n/4$, and let $p(r)=\phi^0[0\leftrightarrow\partial\Lambda_r]$, $A_x=\{0\overset{\Lambda_r}\leftrightarrow\partial\Lambda_r \}$, and $\pi^1(r)=\phi_{\Lambda_r}^1[A_0]$. By DMP and CBC we have 
   $$
   \phi^0[0\leftrightarrow x]\le\phi^0[A_0\cap A_x]\le \phi_{\Lambda_r}^0[A_0]\sup_\xi \phi^\xi_{\Lambda_r(x)}[A_x]\le p(r)\pi^1(r)
   $$
   We should be precise about BC. Now consider $\pi^1(r)$. Like 1, let $C_r$ be the event that there is an open circuit in $\Lambda_{3r/4}\backslash \Lambda_{r/2}$, which is $r/4$ away from $\partial\Lambda_r$, then $\phi_{\Lambda_r}^1[C_r]\ge c_1$ by $\mathbf {P5}$. Let $\Gamma$ ne the most interior circuit (a r.v.) and $L$ be the collection of such circuit, for a circuit $\gamma$, let $D_\gamma$ be the interior domain surrounded by $\gamma$, then, we have 
   $$
   \begin{aligned}
   \phi^0[0\leftrightarrow\partial\Lambda_{r/4},C_r]&=\sum_{\gamma\in L}\phi^0[0\leftrightarrow\partial\Lambda_{r/4}\mid\Gamma=\gamma]\phi^0[\Gamma=\gamma]
   \\&=^\text{DMP} \sum_{\gamma\in L}\phi^1_{D_\gamma}[0\leftrightarrow\partial\Lambda_{r/4}]\phi^0[\Gamma=\gamma]
   \\&\ge^\text{CBC} \phi_{\Lambda_r}^1[0\leftrightarrow\partial\Lambda_{r/4}]\phi^0[C_r]
   \\&\ge \phi_{\Lambda_r}^1[0\leftrightarrow\partial\Lambda_r]\phi^0[C_r]\ge c_1\pi^1
   \end{aligned}
   $$
   So $\phi^0[0\leftrightarrow x]\le p(r)p(r/4)/c_1$. By 1, $\phi^0[0\leftrightarrow x]\le c^6/c_1\ \phi^0[0\leftrightarrow\partial\Lambda_n]^2$. 

3. _Remark_ Commonly for such sandwich-type inequality, for one side we can apply FKG, but for the other side FKG may fail, and in that time we should apply DMP and CBC.

_Solution to exercise 45_ 

1. _Note_ The right inequality is $\phi_{\Lambda_{2n},p_c,q}^\xi[\Lambda_k\nleftrightarrow\partial\Lambda_{n}\mid\mathcal A]\ge 1-(\frac kn)^c$. 

   First by DMP, $\phi_{\Lambda_{2n},p_c,q}^\xi[\Lambda_k\nleftrightarrow\partial\Lambda_n\mid\mathcal A]=\phi_{\Lambda_{2n}\backslash \Lambda_k,p_c,q}^{\xi'}[\partial\Lambda_k\nleftrightarrow\partial\Lambda_n]$. Like in the proof of $\mathbf {P5}\Rightarrow\mathbf {P1}$, pick suitable rectangles, we have $\phi_{\Lambda_{2k}\backslash\Lambda_k,p_c,q}^\xi[\partial\Lambda_k\leftrightarrow\partial\Lambda_{2k}]\le 1-c$ for any $\xi$ a BC. Then scale up proportionally, we have 
   $$
   \phi_{\Lambda_{2n}\backslash\Lambda_k,p_{c},q}^{\xi'}[\partial\Lambda_k\leftrightarrow\partial\Lambda_{n}]\leq\prod_{2^m\le n/k}\phi_{\Lambda_{2^m k}\backslash\Lambda_{2^{m-1}k},p_c,q}^1\left[\partial\Lambda_{2^{m-1}k}\leftrightarrow\partial\Lambda_{2^m k}\right]\leq (1-c)^{[\log_2 n/k]}\le (\frac kn)^{c'}
   $$
   which is required.

2. For $\tilde\omega$, start exploration from $\partial\Lambda_{2n}$ until all clusters intersecting $\partial\Lambda_{2n}$ are revealed. Then by the construction used in the proof of positive association, since $\xi\le 1$, one can construct $\omega_e\le\tilde\omega_e$ for every edge $e$ explored with corresponding BC (on $\partial\Lambda_{2n}$, they are $\xi$ and 1 respectively, and in the interior they are both free). For the edges connecting the explored and unexplored regions, in $\tilde\omega$ they are closed, then set $\omega$ closed on them. For the remaining edges, by DMP $\tilde\omega$ on them has free BC, then let $\tilde\omega=\omega$ on them. Under this coupling, $\omega\sim\phi_{\Lambda_{2n},p_c,q}^\xi$ and when in $\tilde\omega$, $\Lambda_k\nleftrightarrow\partial\Lambda_{n}$, or rather $\Lambda_k\nleftrightarrow\partial\Lambda_{2n}$, on $\Lambda_k$ they coincide. By coupling and conditioning one can get the inequality.

   _Note_ The right inequality should be 
   $$
   \phi_{\Lambda_{2n},p_{c},q}^{\xi}[\mathcal{A}]\geq(1-(\frac{k}{n})^{c})\phi_{\Lambda_{2n},p_{c},q}^{1}[\mathcal{A}].
   $$
   

3. For $\omega$, start exploration from $\partial\Lambda_{2n}$ until it finds an (outmost) open circuit around $\partial\Lambda_k$ (otherwise it explores all clusters and stop). For the edges outside of the open circuit, since $\xi\le 1$, one can construct $\omega_e\le\tilde\omega_e$ with corresponding BC (on $\partial\Lambda_{2n}$ they are $\xi$ and 1 respectively, and on the circuit they are all wired). After that, open all edges on the open circuit for $\tilde\omega$. By DMP, inside that circuit the law is under wired BC. Let $\omega=\tilde\omega$ inside the circuit. Then by DMP, $\tilde\omega\sim\phi_{\Lambda_{2n},p_c,q}^1$, and when there is an open circuit around $\Lambda_k$ in $\omega$, $\omega$ and $\tilde\omega$ coincide. 

   By duality, since in dual graph $\partial\Lambda_k\overset{\Lambda_{2n}\backslash\Lambda_k}\nleftrightarrow\partial\Lambda_{n}$ implies there is an open circuit in the primal graph $\Lambda_{2n}\backslash\Lambda_k$, and in 1 the lower bound holds for all $\xi$, one can conclude the open circuit surrounding $\Lambda_k$ exits with probability $\ge 1-(\frac kn)^c$. Then the inequality is trivial.

   _Note_ The right inequality should be 
   $$
   \phi_{\Lambda_{2n},p_{c},q}^{1}[\mathcal{A}]\geq(1-(\frac{k}{n})^{c})\phi_{\Lambda_{2n},p_{c},q}^{\xi}[\mathcal{A}].
   $$

4. Suppose $A$ depends on edges in $\Lambda_k$ and $B$ depends on edges outside $\Lambda_{2n}$, by DMP
   $$
   \begin{aligned}
   \left|\phi_{p_{c},q}^{1}[A\cap B]-\phi_{p_{c},q}^{1}[A]\phi_{p_{c},q}^{1}[B]\right|&=\phi_{p_c,q}^1[B]|\phi_{\Lambda_{2n},p_c,q}^\xi[A]-\phi_{p_c,q}^1[A]|
   \end{aligned}
   $$
   By 2 and 3, for any BC $\xi$,
   $$
   |\phi_{\Lambda_{2n},p_{c},q}^{1}[\mathcal{A}]-\phi_{\Lambda_{2n},p_{c},q}^{\xi}[\mathcal{A}]|\le (\frac kn)^c \phi_{\Lambda_{2n},p_{c},q}^{1}[\mathcal{A}]
   $$
   Then we have 
   $$
   |\phi_{\Lambda_{2n},p_c,q}^\xi[A]-\phi_{p_c,q}^1[A]|\le |\phi_{\Lambda_{2n},p_c,q}^\xi[A]-\phi_{\Lambda_{2n},p_c,q}^1[A]|+|\phi_{\Lambda_{2n},p_c,q}^1[A]-\phi_{p_c,q}^1[A]|\le 2(\frac kn)^c \phi_{\Lambda_{2n},p_{c},q}^{1}[\mathcal{A}]
   $$
   which concludes the proof.

_Solution to exercise 46_ 

1. Pick $r= (\epsilon\wedge 1)n/16$. consider $S_i=[-\epsilon n+r/8\ i,-\epsilon n+r/8\ i+2r]\times[n/2-r,n/2+r]$, where $1\le i< 8(1+2\epsilon)n/r$. Let $T_i$ be the event that there is an open circuit in the middle $r/8\sim r/4$ layer, whose probability is at least $u_r$. Then $\cap_i T_i$ offers loops to connect the left to the right.  Notice the BC 0 on $\partial R$ is stronger than 0 on $\partial S_i$.
   $$
   \phi_R^0[\mathcal H(\rho n, n)]\ge \phi_R^0[\bigcap_i T_i]\ge^\text{FKG} \prod_i \phi_R^0[T_i]\ge ^\text{CBC}u_r^{8(1+2\epsilon)n/r}
   $$
   RHS is uniformly bounded.

2. In the proof of 1, the choice of $S_i$ already avoids any BC.

3. $\mathcal H(\rho n,n)$ in the primal graph is equivalent to $\mathcal V(\rho n,n)^c$ in the dual graph.

_Solution to exercise 47_

1. _Note_ The right inequality is $\phi^{0}\big[0\leftrightarrow\partial\Lambda_{n}\big]\leq\sum_{k\geq n}\sum_{x\in\partial\Lambda_{k}}\phi_{\Lambda_{k}}^{0}\big[0\leftrightarrow\mathcal{x}\big]$.

   Let $\mathcal C$ be the cluster intersecting $0$. At $p_c$ and free BC, $|\mathcal C|<\infty$ a.s.. Let $\mathbf C$ be the collection of such finite clusters, and for $C\in \mathbf C$, Let $x_C$ be the farthest point under $\|\cdot\|_\infty$, for uniqueness pick the rightmost and upmost point. Then 
   $$
   \begin{aligned}
   \phi^0[0\leftrightarrow\partial\Lambda_n]&= \sum_{C\cap\partial\Lambda_n\neq\emptyset}\phi^0[\mathcal C=C]=\sum_{k=n}^\infty\sum_{x\in\partial\Lambda_k}\sum_{x_C=x}\phi^0[\mathcal C=C]
   \\&=^\text{DMP}\sum_{k=n}^\infty\sum_{x\in\partial\Lambda_k}\sum_{x_C=x}\phi^0_{C}[\mathcal C=C]\le ^\text{CBC}\sum_{k=n}^\infty\sum_{x\in\partial\Lambda_k}\sum_{x_C=x}\phi^0_{\Lambda_k}[\mathcal C=C]
   \\&\le\sum_{k=n}^\infty\sum_{x\in\partial\Lambda_k}\phi_{\Lambda_k}^0[0\leftrightarrow x]
   \end{aligned}
   $$

2. The supremum limit must be nonpositive. If it's negative, we have $\phi_{\Lambda_k}^0[0\leftrightarrow x]\le \exp[-c k^\alpha]$. In this case, $\sum_{k\ge n}\sum_{x\in\partial\Lambda_k}\phi_{\Lambda_k}^0[0\leftrightarrow x]\le C\exp[-c' n^\alpha]$. So $\phi^0[0\leftrightarrow\partial\Lambda_n]\le C\exp[-c'n^\alpha]$, i.e., $\limsup_{n\rightarrow\infty}\frac{1}{n^\alpha}\log\phi^0[0\leftrightarrow\partial\Lambda_n]\le -c'$, which is a contradiction.

3. Notice by reflection, $\phi_{\Lambda_k}^0[0\leftrightarrow x]^2\le \phi_{\Lambda_{3k}}^0[0\leftrightarrow 2ke_1]$. Now use 2.

4. _Note_ The right limit is $\limsup_{k\rightarrow\infty}(7^kn)^{-\alpha}\log u_{7^k n}=0$, if $\alpha$ is arbitrary.

   _Sketch of proof_ Let $R=7^k n$ and pick $7^k n/700\le m\le 7^kn/100$. Apply 3 to construct a circuit surrounding $\Lambda_{7^k n/4}\backslash\Lambda_{7^k n/8}$, which needs a fixed number $C$ of boxes of size $m$. Let $w_l=\phi_{\Lambda_{3l}}^0[0\leftrightarrow 2le_1]$. we have $u_{7^k n}\ge w_m^C$. Now pick a subseries $m_l$, such that $\log w_{m_l}/m_l^\alpha\to 0$. Pick $k_l$ to be the smallest such that $7^{k_l}n\ge 100 m_l$, and $7^{k_l}n\le 700 m_l$. So we have $u_{7^{k_l}n}\ge w_{m_l}^C$, i.e., $\log u_{7^{k_l}n}/(7^{k_l}n)^\alpha\ge C\log w_{m_l}/(700 m_l)^\alpha\to 0$.

   If $\alpha$ is precisely chosen, for example, $0<\alpha<\log 2/\log 7$, the limit in the lecture note is true. Choose $C\ge 2$ s.t. $u_{7r}\le Cu_r^2$. If $Cu_n\le 1$, we have $Cu_{7^j n}\le (Cu_n)^{2^j}$. Take logarithm, $\log u_{7^j n}\le 2^j\log Cu_n-\log C$, consequently we have 
   $$
   \frac{\log u_{7^j n}}{(7^{j}n)^{\alpha}}\leq\frac{\log Cu_n}{n^{\alpha}}\left(\frac{2}{7^{\alpha}}\right)^{j}-\frac{\log C}{(7^{j}n)^{\alpha}}
   $$
   Then the chosen of $\alpha$ forces RHS tends to $-\infty$, which leads to contradiction. So $Cu_n>1$. Since $u_n$ is uniformly bounded away from 0, $\lim_{j \to \infty} \log u_{7^j n}/j^\alpha=0$. 

_Explanation to Lemma 5.9_ Use CBC.

- First, the case $\mathcal l=2$ follows from Lemma 5.9, since the BC free on $\mathbb Z\times\{-n\}$ and wired otherwise is weaker than free on $[0,\rho n]\times\{-n\}$ and wired on other three side.

- To push $\mathcal l$ to $\mathcal l+1$, notice that the BC free on $[0,\rho n]\times\{0\}$ and wired on $\{0\}\times[0,(l+1)n]\cap[0,\rho n]\times\{l+1\}\cap \{\rho n\}\times[0,(l+1)n]$ is weaker than the BC free on $[0,\rho n]\times\{-n\}$ and wired on $\{0\}\times[-n,(l+1)n]\cap[0,\rho n]\times\{l+1\}\cap \{\rho n\}\times[-n,(l+1)n]$, since the latter may induce some links on $[0,\rho n]\times\{0\}$. Moreover, by translation invariance, we have $\phi_{[0,\rho n]\times[-n,(l+1)n]}^{1/0}[\mathcal H([0,\rho n]\times[n,2n])]\ge c(\rho,l)$.

- Let $R=[0,\rho n]\times[n,2n]$. Notice $\mathcal H(R)$ induces coarser BC on $[0,\rho n]\times [0,n]$ than $1/0$ on $[0,\rho n]\times[-n,2n]$, since the former is wiring in a lower height. So we have 
  $$
  \phi_{[0,\rho n]\times[-n,(l+1)n]}^{1/0}[H(\rho n,n)\cap H(R)]\geq^\text{CBC} c(\rho,2)\phi_{[0,\rho n]\times[-n,(l+1)n]}^{1/0}[H(R)]\geq c(\rho,2)c(\rho,l)
  $$
  
