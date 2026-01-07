---


title: Three Percent Is Enough, Semi-Supervised Martian Segmentation Labeling with Active Learning
authors:
   
   
---

<!-- Using HTML to center the abstract -->
<div class="columns is-centered has-text-centered">
    <div class="column is-four-fifths">
        <h2>Abstract</h2>
        <div class="content has-text-justified">
Accurate, large-scale Martian segmentation datasets are a cornerstone
of autonomous scene understanding in support of exploration and
navigation in Martian environments. However, high-quality segmentation
labeling on planetary images requires annotators to have professional
extraterrestrial geological knowledge, and even skilled annotators need
a long time to label a single image in detail. In this paper, we
propose a semi-automatic annotation method for the Mars scene
segmentation. By integrating a semi-supervised segmentation network
architecture with an active learning strategy, our framework achieves
near-fully supervised performance using a minimal amount of manual
annotations, significantly reducing dependence on human experts.
Experiments on the S5Mars dataset show that our framework reaches
76.73% on mIoU, which is 95.73% of the accuracy of the official S5Mars
semi-supervised model trained on 5000 labeled images, while requiring
only 3.38% of the manual annotations (169 images). It even surpasses
the performance of the official model trained with 20% labeled data,
demonstrating a substantial improvement in label efficiency. 
        </div>
    </div>
</div>

---


## Purpose
We propose an efficient semi-automatic framework for the Martian segmentation labeling task,aim to leverage a very small amount
of manually labeled images to generate tens of thousands of high-quality labels, supporting future Mars exploration and scientific research


## Contribution
1. A iterative open-sourced framework combined with sem-supervised learning and active query strategy is developed to produce large-scale Martian segmentation dataset with mini-mize human expert labeling effort
2. A CPS-Mars architecture based on cross pseudo supervision (CPS)  is proposed to for SSL with self-defined loss function dealing with inter-class imbalance problem in Mars scene dataset.
3. Performance of our framework with optimized modules and strategies reaches 95.73% accuracy on labeling S$^5$Mars segmentation dataset with only nearly 3% of manually labeled images.


## frmework
We combined the idea of semi-supervision with active learning and designed a semi-supervised active learning framework. Train a semi-supervised model driven by an extremely small amount of data. Based on the performance of unlabeled data on the semi-supervised model, we use the active learning query method we designed to query the data with the greatest labeling value for manual labeling. Finally, the labeled data is integrated with the labeled data and then input into the semi-supervised learning model. Repeat this process until the user's needs are met

![Turing Machine](/static/image/SSL2.png)
*Figure 1: Semi-supervised active learning framework for Mars segmentation labeling. 
## SSL architecture
Our SSL architecture is based on a dual-branch structure. For the special Mars scenario, we have designed a special supervised loss function.

![Turing Machine](/static/image/CPSnew.png)
*Figure 2: Semi-supervised learning architecture for Mars scene segmentation.
## Table: Segmentation performance of SSL architectures and active query methods on S$^5$Mars dataset (Using 169 Labeled Images out of 5400 Total)

| SSL architecture | Active query strategy | Query frequencies | mIoU  |
|------------------|-----------------------|-------------------|-------|
| CPS-Mars         | Ramdom                | 1                 | 66.55 |
| CPS-Mars         | BALD                  | 1                 | 70.76 |
| CPS-Mars         | Uncertainty           | 1                 | 71.24 |
| CPS-Mars         | Entropy               | 1                 | 73.82 |
| CPS-Mars         | UEQ(Ours)             | 1                 | 75.00 |
| CPS-Mars         | UEQ(Ours)             | 2                 | 75.13 |
| CPS-Mars         | UEQ(Ours)             | 4                 | 76.73 |


