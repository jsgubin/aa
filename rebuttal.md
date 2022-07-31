# To AC
complain reviewer 1

# Global review



# Reviewer 1
We thanks our reviewers for their time, and their positive and detailed feedback. We hope our answers below can address some of the questions raised:

>The major concern I have with the paper in it's current form is the quality of writing, which highly affects its clarity and even my ability to assess whether some of the claims are correct, let alone novel. It is not always clear what the authors assume, and what the "logic" and order of quantifiers is in their definitions and therefore in their maintheorems.

R: Thanks 


>Section 3.2 - You provide references that use coordinated ZO estimator, though no references of using therandom ZO estimator. Moreover, in figure 1 you refer to the random ZO estimator as "Our new". This ismisleading, as it gives the impression that it is used for the first time in this paper. This is definitely not true. Forexample, the seminal [Online convex optimization in the bandit setting: gradient descent without a gradient,Flaxman Kalai McMahan] and many follow ups. Your paper should at least provide such references, and a detailed discussion of what is diff erent in your setting (finite sum etc.).

R：

>The term "system error" is used throughout the paper, though it is not defined.

R:


>In my opinion there is at least one limitation of the paper which the authors do not discuss.
As I described above,the main results only hold for \epsilon larger than something, which seems to be ignored throughout the paper (though is evident from the technical main theorems).

R:

# Reviewer 2

>While reduction based approaches usually enjoy a simplified analysis, in practice they are more difficult to implement due to their need to maintain delicate objective reduction properties. Usually these properties dependson unknown problem parameters, e.g. smoothness, which limits the applicability of this type of methods. I would not blame the authors for this drawback since it is a common problem of the reduction based approaches, but I cannot strongly recommend this work due to this reason.

R:


>For the non-convex setting, the obtain the complexity does not necessary outperforms the previous SOTA when $n$ is larger than $d^2$. It is a little overstatement so please clarify this in the revision.

R:

# Reviewer 3

# Reviewer 4
>**Limitation**: I think the authors didn't mention any disadvantage of proposed method but final system error comparing with existing one. In my opinion, it is fine but I would like to hear more discussion or explanation as mentioned in above box.

**R**: Thanks for discussing the limitations or disadvantages of the paper. We have one or two more hyper-parameters (i.e., $\gamma_0$ and $\mathcal{K}$ in Algorithm 1, $\lambda$ in Algorithm 2) needed be set in our reduction frameworks, compared to existing variance reduced ZO proximal  algorithms such as ZOR-ProxSVRG and ZOR-ProxSAGA. However, choosing these hyper-parameters can be done by the cross validation  with the criteria of running time to converge. Below we provide some principles for choosing them.

   - $\gamma_0$ and $\mathcal{K}$ conficts each other. Specifically, if $\gamma_0$ is larger, $\mathcal{K}$ is smaller such that finally $\gamma_S$ closes to zero. In our experiments, we set  $\gamma_0$ and $\mathcal{K}$  ~~add specific settings in our experiments~~
   - $\lambda$ is           In our experiments, we set  $\gamma_0$ and $\mathcal{K}$ ~~add specific settings in our experiments~~

In addition, our method maybe have one more system error as mentioned by the reviewer.




# Todo

- []  plot figure 3 with residue error, y axis is in log. x axis in Figure  4 is log.

- [] plish definition, theorems to make them more logic
