# Global review


# Reviewer 1
We thanks our reviewers for their time, and their positive and detailed feedback. We hope our answers below can address some of the questions raised:

>The major concern I have with the paper in it's current form is the quality of writing, which highly affects its clarity and even my ability to assess whether some of the claims are correct, let alone novel. It is not always clear what the authors assume, and what the "logic" and order of quantifiers is in their definitions and therefore in their maintheorems.

R: 


>Section 3.2 - You provide references that use coordinated ZO estimator, though no references of using therandom ZO estimator. Moreover, in figure 1 you refer to the random ZO estimator as "Our new". This ismisleading, as it gives the impression that it is used for the first time in this paper. This is definitely not true. Forexample, the seminal [Online convex optimization in the bandit setting: gradient descent without a gradient,Flaxman Kalai McMahan] and many follow ups. Your paper should at least provide such references, and adetailed discussion of what is diff erent in your setting (finite sum etc.).

R：

>The term "system error" is used throughout the paper, though it is not defined.

R:


>In my opinion there is at least one limitation of the paper which the authors do not discuss.
As I described above,the main results only hold for \epsilon larger than something, which seems to be ignored throughout the paper (though is evident from the technical main theorems).

R:

# Reviewer 2

>While reduction based approaches usually enjoy a simplifi ed analysis, in practice they are more diffi cult toimplement due to their need to maintain delicate objective reduction properties. Usually these properties dependson unknown problem parameters, e.g. smoothness, which limits the applicability of this type of methods. I wouldnot blame the authors for this drawback since it is a common problem of the reduction based approaches, but Icannot strongly recommend this work due to this reason.

R:


For the non-convex setting, the obtain the complexity does not necessary outperforms the previous SOTA when $n$ is larger than $d^2$. It is a little overstatement so please clarify this in the revision.

# Reviewer 3

# Reviewer 4
>I think the authors didn't mention any disadvantage of proposed method but final system error comparing with existing one. In my opinion, it is fine but I would like to hear more discussion orexplanation as mentioned in above box.

R: 