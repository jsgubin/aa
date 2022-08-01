# To AC
complain reviewer 1

# Global review



### Response to Reviewer


We thanks our reviewers for their time, and their positive and detailed feedback. We hope our answers below can address some of the questions raised:

>The major concern I have with the paper in it's current form is the quality of writing, which highly affects its clarity and even my ability to assess whether some of the claims are correct, let alone novel. It is not always clear what the authors assume, and what the "logic" and order of quantifiers is in their definitions and therefore in their maintheorems.

R: Thanks 


>Section 3.2 - You provide references that use coordinated ZO estimator, though no references of using therandom ZO estimator. Moreover, in figure 1 you refer to the random ZO estimator as "Our new". This ismisleading, as it gives the impression that it is used for the first time in this paper. This is definitely not true. Forexample, the seminal [Online convex optimization in the bandit setting: gradient descent without a gradient,Flaxman Kalai McMahan] and many follow ups. Your paper should at least provide such references, and a detailed discussion of what is diff erent in your setting (finite sum etc.).

R：

>The term "system error" is used throughout the paper, though it is not defined.

R:


>In my opinion there is at least one limitation of the paper which the authors do not discuss.
As I described above,the main results only hold for \epsilon larger than something, which seems to be ignored throughout the paper (though is evident from the technical main theorems).

> For which functions should the algorithm satisfy this? Clearly not for any function whatsoever, since then no such algorithm exists. Also, what is gamma? How should it apply to the non-strongly-convex setting where there is no gamma? Furthermore, what is the order of quantifiers for K,\delta,E? Do they just need to exist? Depend on A? On F? For all F? Under which assumptions?

Definition 5 means for a function $F = f(\cdot) + r(\cdot)$, where $f(\cdot)$ is $L$-smooth and $\gamma$-strongly convex, and an optimizer $\mathcal{A}（F, \cdot)$, if the following property holds: for any input $x$, the optimizer outputs $x' \gets \mathcal{A}（F, x)$ with total function query complexity $\mathcal{C}(L,\gamma)$. Further, the function value should satisfies $\mathbb{E}\left[F(\mathbf{x}')-\min_{\mathbf{x}}F(\mathbf{x})-\delta_\mu\right] \leq \mathcal{K}\left[F(\mathbf{x}_0)-\min_{\mathbf{x}}F(\mathbf{x})-\delta_\mu\right] + \mathcal{E}$, where $\delta_\mu$ is a fixed error introduced by smoothing parameter $\mu$; $\mathcal{K}$ and $\mathcal{E}$ depend on the optimizer $\mathcal{A}$ and the parameter $L, \gamma$ of $F$. Then we call it the ZOOD property.

> Theorem 2: "If the inner algorithm satisfies ZOOD". For what \gamma? In this section you do not assume strong convexity.

Theorem 2 states that Assumption 3 holds, i.e., $F$ is $\sigma$-weakly convex. Then we have $F^{(s)}(x) = F(\mathbf{x}) + \frac{1}{2\lambda} \|\mathbf{x}-\mathbf{x}_{s-1}\|^2 = F(\mathbf{x}) + \sigma \|\mathbf{x}-\mathbf{x}_{s-1}\|^2 $ is $\sigma$-strongly convex. That to say $\gamma = \sigma$ in ZOOD property.

> Theorem 1+2: In both theorems there are terms which do not go to zero (e.g. E/(1-K)). This is not emphasized in your complexity bounds throughout the paper, but is crucial since it implies that all your complexity bounds hold only for \epsilon larger than something, and are not truly asymptotic.

The system error term is induced by the random zeroth-order gradient estimator. To tackle this problem, we take the following strategy: at the beginning of the iterations of the experiments, we use the proposed reduction frameworks to rapidly decrease the function value until we reach a stuck region where objective function cannot decrease much. In this case, we switch our algorithms to PROX-ZO-SPIDER to guarantee our algorithms to converge to the same system accuracy as other compared algorithms.

> Algorithm 3: What do you mean by "Option I" and "Option II" in the pseudocode?

This means Algorithms neither update update by "Option I" or "Option II". In the proof, we only analyse $Option I$ but $Option II$ also work in practice. In the revised version, we will remove Option II to avoid misunderstanding.

> You write $\mathcal{E} = \mathcal{O}(\|\nabla f(x^*)\|^2)$. But $\nabla f(x^*) = 0$ (for nonsmooth functions, 0 is at least a subgradient). So either I'm missing something, or this is a mistake.

We don't agree with this statement because the definition of $\epsilon$-stationary point of problem (1) is stated in Definition 3.

> Definition 6: You call this is a definition, but it seems like an assumption rather than a definition

Thanks for pointing this out. We define $G_{C}^2$ and $G_{NC}^2$ to be the upper bounds of $\|\nabla f^{(\gamma_s)}(\mathbf{x}_s^*)||^2$ and $\|\nabla f^{(s)}(\mathbf{x}_s^*)\|^2$, respectively. In the revised version, will re-write this definition to make it more formal.

### Response to Reviewer JovT

Re Q1: We analyse the ZOOD property under the setting when $F$ is strongly convex. SPIDER is designed to solve non-convex optimization problems. So we need to focus on its strongly convex counterpart, i.e., the well-known SARAH method https://arxiv.org/pdf/1703.00102.pdf. Unfortunately, under the strongly convex setting. The SARAH method has the same oracle complexity as SVRG. Thus, although SARAH also has the ZOOD property under subtle derivation, the total complexity is almost the same as SVRG based methods.

Re Q2: Thanks for pointing this out. We can also consider the application of the ZOOD property to the momentum based algorithms like ZO-VARAG https://arxiv.org/pdf/2007.03311.pdf, which may further improve the complexity $1/\sqrt{\epsilon}$. But the main idea of this work is to use the proposed reduction frameworks to further decrease the function query complexities of the original algorithms. To this end, we consider applying the two reduction frameworks to two classical methods: ZO-SVRG and ZO-SAGA.



>While reduction based approaches usually enjoy a simplified analysis, in practice they are more difficult to implement due to their need to maintain delicate objective reduction properties. Usually these properties depends on unknown problem parameters, e.g. smoothness, which limits the applicability of this type of methods. I would not blame the authors for this drawback since it is a common problem of the reduction based approaches, but I cannot strongly recommend this work due to this reason.

R: We have  two or three more hyper-parameters (i.e., $\gamma_0$ and $\mathcal{K}$ in Algorithm 1, $\lambda$ in Algorithm 2, and epoch number $S$ in both algorithms) needed be set in our reduction frameworks, compared to existing variance reduced ZO proximal  algorithms such as ZOR-ProxSVRG and ZOR-ProxSAGA. Choosing these hyper-parameters can be done by the cross validation  with the criteria of running time to converge. Below we provide some principles for choosing them.

   - $\gamma_0$ and $\mathcal{K}$ conficts each other. Specifically, if $\gamma_0$ is larger, $\mathcal{K}$ is smaller such that finally $\gamma_S$ closes to zero. In our experiments, we set  $\gamma_0$ and $\mathcal{K}$ $S=$  ~~add specific settings in our experiments~~
   - $\lambda$ could be any value  such that $F^{(s)}(\mathbf{x})$ is strongly convex.   In our experiments, we set  $\lambda$ and $S=$ ~~add specific settings in our experiments~~


>For the non-convex setting, the obtain the complexity does not necessary outperforms the previous SOTA when $n$ is larger than $d^2$. It is a little overstatement so please clarify this in the revision.

R: Thanks for the suggestion. In the abstract and introduciton of the revised version, we have highlighted the condition in terms of the improvement of our algorihtm on the non-convex setting comapred to the previous SOTA.

### Response to Reviewer  q2AU

> The new ZOOD condition used in the paper is different from the prior work. Therefore direct comparisons might not be fair.

We want to emphasize that ZOOD is an inherent property of algorithms in solving general strongly convex problems, not a condition. The core idea of this work is to use the ZOOD property to design two reduction framework for solving general convex and weakly convex problems.

> In the experimental results presented in Figure 4, the two proposals have a very sharp descending at the very beginning and have a turning point after which they converge much slower. Is there a specific reason for that and do you have some ideas about what the turning point stands for?

The sharp descending phenomenon at the beginning iterations of the experiments is because of the use the reduction framework (i.e., we transform the problem into a strongly convex problem for optimization.). However, due to the existence of the system error term $G_{N}$ $G_{NC}^2$, the optimizer will encounter a turning point. In order to guarantee our algorithms to converge to the same system accuracy, we switch our algorithms to PROX-ZO-SPIDER if the improvement of objective function (\textit{i.e.}, $F(\mathbf{x}_s)-F(\mathbf{x}_{s-1})$) is smaller than a threshold. That's why it converge slower after the turning point.

> Do you find any failure cases of the proposals (divergence) in the experiments due to not satisfying the ZOOD property?

The ZOOD property is always guaranteed by the algorithm itself. In the experiments, one important hyper-parameter we need to tune is the $\gamma_0$ in algorithm 1 and $\lambda$ in algorithm 2. In fact, we can always use the grid search method to find the smallest hyperparameter that satisfies the condition.

### Response to Reviewer 9Fqq

> What is the typical order between the $\mathcal{O}(\delta_\mu)$ and $O(G_*^2)$ terms in the system error? Can authors elaborate these more?

The system error term $\delta_\mu$ typically proportional to the smoothing parameter, so we can always choose a small enough smoothing parameter to control this term. While $O(G_*^2)$ is corresponding to the problem itself, which is typically unknown in practice. To tackle this problem, we take the following strategy: at the beginning of the iterations of the experiments, we use the proposed reduction frameworks to rapidly decrease the function value until we reach a stuck region where objective function cannot decrease much. In this case, we switch our algorithms to PROX-ZO-SPIDER to guarantee our algorithms to converge to the same system accuracy as other compared algorithms.

> I don't quite understand how the authors established the final FQC

According to Theorem 1, the reduction framework has a linear convergence rate before it reaches the threshold of the system error term $\mathcal{E}/(1-\mathcal{K})$. So the number of the outer loop $S$ is $O(\log 1/\epsilon)$，where we use $O$ to hide the constant terms. To tackle the system error term that cannot be eliminated, we propose the strategy as stated response to the above question.


>**Limitation**: I think the authors didn't mention any disadvantage of proposed method but final system error comparing with existing one. In my opinion, it is fine but I would like to hear more discussion or explanation as mentioned in above box.

**R**: Thanks for discussing the limitations or disadvantages of the paper. We have  two or three more hyper-parameters (i.e., $\gamma_0$ and $\mathcal{K}$ in Algorithm 1, $\lambda$ in Algorithm 2, and epoch number $S$ in both algorithms) needed be set in our reduction frameworks, compared to existing variance reduced ZO proximal  algorithms such as ZOR-ProxSVRG and ZOR-ProxSAGA. Choosing these hyper-parameters can be done by searching in some candidates  with the criteria of less running time to converge. Below we provide the principles and some examples of tuning them.

   - $\gamma_0$ and $\mathcal{K}$ in Algorithm 1 conficts each other. Specifically, if $\gamma_0$ is larger, $\mathcal{K}$ is smaller such that finally $\gamma_S$ closes to zero. In our experiments, we set   $\mathcal{K}=0.9$ and $S=30$ for the all experiments. For  $\gamma_0$, we search it from the candidates $\{1, 0.5, 0.1, 0.05, 0.01, 0.005, 0.001, 0.0005, 0.0001\}$. We find that $\gamma_0=0.005$  has a good performance for most of datasets.
   - $\lambda$ could be any value  such that $F^{(s)}(\mathbf{x})$ is strongly convex.  We  In our experiments, we set $S=30$ for the all experiments， and search $\lambda$ from the candidates .

In addition, as mentioned by the reviwer, our methods achieve lower query complexities  by sacrificing the accuracy of solver, i.e., maybe have one more system error.


# Todo

- []  plot figure 3 with residue error, y axis is in log. x axis in Figure  4 is log.

- [] plish definition, theorems to make them more logic

- [] the obtain the complexity does not necessary outperforms the previous SOTA when $n$ is larger than $d^2$. It is a little overstatement so please clarify this in the revision.
