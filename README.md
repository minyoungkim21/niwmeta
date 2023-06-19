# NIW-Meta: A (Hierarchical) Bayesian model for meta few-shot learning

The official code to reproduce some of the experimental results in our paper:<br> 
**[A Hierarchical Bayesian Model for Deep Few-Shot Meta Learning](http://arxiv.org/abs/2306.09702) [[1]](#references)** (aka *NIW-Meta*):

>We propose a novel hierarchical Bayesian model for learning with a large (possibly infinite) number of tasks/episodes, which suits well the few-shot meta learning problem. We consider episode-wise random variables to model episode-specific target generative processes, where these local random variables are governed by a higher-level global random variate. The global variable helps memorize the important information from historic episodes while controlling how much the model needs to be adapted to new episodes in a principled Bayesian manner. Within our model framework, the prediction on a novel episode/task can be seen as a Bayesian inference problem. 
However, a main obstacle in learning with a large/infinite number of local random variables in online nature, is that one is not allowed to store the posterior distribution of the current local random variable for frequent future updates, typical in conventional variational inference. We need to be able to treat each local variable as a one-time iterate in the optimization. We propose a Normal-Inverse-Wishart model, for which we show that this one-time iterate optimization becomes feasible due to the approximate closed-form solutions for the local posterior distributions. The resulting algorithm is more attractive than the MAML in that it is not required to maintain computational graphs for the whole gradient optimization steps per episode. Our approach is also different from existing Bayesian meta learning methods in that unlike dealing with a single random variable for the whole episodes, our approach has a hierarchical structure that allows one-time episodic optimization, desirable for principled Bayesian learning with many/infinite tasks.

For the details of the algorithm, see [[1]](#references).

---

## How to run (Code is coming soon!)

### 1. SineLine

   * Requirements:
      - python >= 3.9 <br>
      - pytorch >= 1.9.0 <br>
      - ```pip install higher``` <br>

   * Run:
     - ```python3 main_regression.py```


### 2. Fewshot-ViT

   * Requirements:
      - The same requirements as [PMF (CVPR'22)](https://github.com/hushell/pmf_cvpr22) <br>
      - ```pip install higher```
   
   * Instructions:
      - Install PMF and replace ```train.py``` and place ```engine_niwmeta.py``` in the root folder. <br>
      - Place ```niwmeta.py``` in the ```models/``` folder and replace ```__init__.py``` in models/. <br>
   
   * Run:
      - Command lines are similar to PMF, eg, for CIFAR-FS with DINO/s-16 
      - ```python train.py --deploy niwmeta --use_gami 1 --n0_init 1 --gam0_init 1e6 --steps 3 --burnin 0 --alp 1e-6 --ai_max 1e3 --nsamps_test 2 --dataset cifar_fs --arch dino_small_patch16 --nSupport 5 --epoch 100 --lr 1e-4```


## References

[1] Kim, Minyoung and Hospedales, Timothy, "[A Hierarchical Bayesian Model for Deep Few-Shot Meta Learning](http://arxiv.org/abs/2306.09702)", *arXiv preprint arXiv: 2306.09702* 2023.


## Citation

If you found this code useful in your research, please cite:
```
@article{niwmeta_kim_hospedales_2023,
  title={A Hierarchical Bayesian Model for Deep Few-Shot Meta Learning},
  author={Kim, Minyoung and Hospedales, Timothy},
  journal={arXiv preprint arXiv: 2306.09702},
  year={2023}
}
```
