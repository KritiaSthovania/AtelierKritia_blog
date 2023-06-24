---
title: 基于SPH的强流体-刚体耦合解算器
Author: Yanxi Liu
category: Project
---

这个是我的研究生毕设，基于论文[Interlinked SPH Pressure Solvers for Strong Fluid-Rigid Coupling](https://dl.acm.org/doi/10.1145/3284980)，我的导师Jan Bender也是这篇文章的作者之一。由于这篇文章的前几个作者都是弗莱堡大学的，所以其实我们并没有源代码，于是毕设的内容就是把这篇文章的算法集成到我导师的开源框架[SPlisHSPlasH](https://github.com/InteractiveComputerGraphics/SPlisHSPlasH)中，由于目前还没有全部完成，所以代码暂时在我的[Fork](https://github.com/KritiaSthovania/SPlisHSPlasH)里，目前绝大多数的部分已经实现。

SPH即“光滑粒子流体动力学”，是一个在图形学中常用的模拟流体的方法。所谓的“强耦合”自然是针对于“弱耦合”来说的。在弱耦合中，我们有流体和刚体两个互不相干的解算器，在每一模拟步长中，我们会先解算流体（需要多次迭代），然后再解算刚体（可以用任意解算器），在迭代解算流体的过程中我们假设流体的压力是不会影响刚体的（即刚体的速度和位置不变），反之亦然，所以在判断流体压强是否收敛的时候我们不考虑刚体。在强耦合中，流体与刚体使用统一的解算器，因此在每次迭代中，我们同时解算刚体与流体，即每次迭代得到的流体压强会影响刚体的速度，而刚体的速度反过来也会影响流体的压强，所以在判断压强是否收敛时，我们同时考虑流体和刚体。这样做带来的好处是在相同的时间步长下误差更小，于是通过增大时间步长，我们便可以得到更快的模拟速度。这个方法的核心是一个基于SPH的刚体解算器，具体算法较为复杂，有兴趣的话可以看看这篇论文，可以直接在[这里](https://animation.rwth-aachen.de/publication/0563/#:~:text=The%20approach%20interlinks%20the%20iterative%20pressure%20update%20at,as%20artificial%20density%20deviations%20at%20rigid%20body%20particles.)下载。