---
title: "Our Process for Collaborating on AI Projects"
date: 2019-06-26T10:07:21+06:00
# post image
image: "images/blog/ai-process/Thumbnail.jpeg"
# post type (regular/featured)
type: "regular"
# meta description
description: "How to solve problems in AI4Bharat"
# post draft
draft: false
---

> An A.I. process with high adherence is as an essential component to be successful in our mission of collaborative innovation at scale.

![Cover Image](../../images/blog/ai-process/cover.jpeg)

AI4Bharat is a community of people working across disciplines, locations, and skill-levels. To ensure effective collaborative innovation, a well-defined process is required. Unlike the development of software, wherein established processes exist, the development of AI projects is an evolving practice with no universally agreed upon practices. In this light, this article presents our (work-in-progress) process definition that will guide collaboration on all our projects. The article is not particularly detailed on coding practices, instead it primarily focusses on the tools and communication templates to use for chronicling progress through the project’s life cycle.

A machine learning project is **iterative**, at multiple levels: in defining the problem, collecting data, labelling data, training the model, fine-tuning the model, and then maintenance/deployment. So, while the following presents a series of different steps, they must be understood to be steps within an iterative whole.

---

## The Project Page - Before ML

* Define ***problem statement*** , identify ***value*** , estimate ***feasibility*** , and set ***expectations*** .
* ***Problem statement*** should first document business-as-usual in terms of process currently followed. This is significant in that it calls out the current domain expertise which is often what we seek to replace/augment with ML. Without sufficient understanding of the current process, a ML project often ends up being run inefficiently.
Then, the expected change is to be specified in terms of the role of ML. This should clearly call out the embedding of the ML component within the current process.
* Business/social ***value*** must clearly state the benefit expected out of ML. This could be either creating a new service or product, or improving speed, or increasing scale, or increasing effectiveness (such as accuracy). As the last three terms are relative quantities w.r.t. the current process, it is important to subjectively qualify existing process. In other words, are there are complex rule based systems being used for specific tasks (eg. classification of diseases in paddy), or bottlenecks in processes due to dependence on human experts (eg. doctor’s diagnosis of retinopathy). Often decision-making on funding projects is clarified if numerical estimates can be provided on the value w.r.t. the current practice.
* Estimating ***feasibility*** is challenging but must be considered along three different axes: (a) data - current availability/access and cost of new data acquisition and labelling, (b) existence of prior work (published papers or existing products) mapping the problem to both scientific findings and real practice, (c) experience of current team and existing infrastructure (compute, storage - could be cloud) in similar problems.
* ***Expectations*** or targets must be set with due consideration. Some expectations come from the engineering constraints such as expected latency of inference, or available memory for deployed model. Others come from the accuracy of the model. Sometimes, accuracy is not a single number: We may be interested in the *precision* of a model at various *recall* values such as for the top 20% cases the model should be right 99% of the times. Though these estimates are often tentative, it is best to start with some estimates on these numbers. As the project is more concretely defined, ideally a single metric must be identified as the main criterion for making engineering choices.
* The process of working through the above steps is itself iterative and is significant in ensuring clarity both for the domain and engineering teams. A good documentation of these steps is essential for successful management of ML projects.

> **In the context of AI4Bharat, this documentation forms the project page that is accessible for all open and ongoing projects.**

## Data

* ***Collect* data *, understand*** data, ***label*** data, and ***version-control*** data.

* ***Understanding*** available or to-be-collected data is often the most rewarding [technical debt](https://en.wikipedia.org/wiki/Technical_debt) for an ML engineer. Too often, specific attributes in the data are known only to domain experts and remain a mystery to the ML team. Beyond understanding what the data stands for, manual inspection of data can be handy in building intuition for ML. Finding corrupted files, unbalanced classes, noisy labels, the range of different features, etc. can provide a qualitative feel for the data that helps in subsequent model choice and tuning.

* ***Collecting*** data can be done in different ways:
  * The ideal situation is to collect data and labels being generated by an existing deployed system. For instance in one of our projects of collecting ECG plots and doctor’s classifications on the heart condition, the data is being generated by the current setup and needs to be simply collected correctly and efficiently. There are other examples of more active intervention. For instance, the AB testing of a website’s design with different choices can be automatically labelled by the click-through rates of the users.
  * The second opportunity is to harvest data from existing sources within organisations or in public repositories. For organisational data, a best practice involves storing the data in a [data lake](https://aws.amazon.com/big-data/datalakes-and-analytics/what-is-a-data-lake/) such that data is not fragmented across silos of functional units with complicated technical and bureaucratic speed bumps. For public data, there are now increasing number of online repositories. A collection of many such sources is [here](https://blog.bigml.com/list-of-public-data-sources-fit-for-machine-learning/).
  * The third opportunity is to collect data specifically for the ML task at hand. This is often expensive and limited by financial resources. Here significant care is to be taken in the design of the collection process to ensure quality.
  * The final opportunity is to create data by intelligent augmentation. For instance, in the sign-board translation project, we aim to synthetically generate a large number of examples by juxtaposing text in different fonts on to images of real sign boards.
  * In all these cases, attention is to be paid to ensure that the collected/generated data is representative of the data used to evaluate the model after deployment. This representativeness must be explicitly documented.

* *Labelling* data is often the most time-consuming human component of a ML project. Again, the technical debt here is documentation. Before starting to label, it is important to document the labelling process itself. For instance, marking the head of a human is subject to different interpretations. Instead, stating that a circle or ellipse must be drawn covering the entire head is less prone to misinterpretation. Detailed examples are to be provided for each label in this ***label document.*** Coming back to how to label data, there are several ways to consider:
  * As mentioned earlier, the ideal scenario is when the system that you are trying to augment or replace can itself generate both data and labels.
  * Crowdsourcing from websites such as [this](https://www.figure-eight.com/), [this](https://www.mturk.com/) and [this](https://desicrew.in/), is one of the most common approaches. For corporations, there is a concern here regarding data security and privacy.

  There are several tools available for labelling. Some of these are listed [here](https://www.altexsoft.com/blog/datascience/how-to-organize-data-labeling-for-machine-learning-approaches-and-tools/#t8). One specific tool to consider in the context of AI4Bharat is the [open source tool](https://github.com/DataTurks/DataTurks) from [DataTurks](https://dataturks.com/).

  In any such labelling process, computing cross-annotator agreement is crucial. To enable such down-stream processing all labelling efforts must specify the annotator’s details, the annotation tool, date, and any other meta-data relevant to distinguish between labels.
  * For problem spaces where the scale is too large for crowdsourcing, active labelling may be considered. The idea is to iteratively label parts of the data based on the output of one or more simple models (also called noisy labellers). If the simple models have high perplexity on a given input data, then that is a good candidate for explicit labelling by human annotators.
  * If there is a large mismatch across annotations by different labellers, then debugging the labelling process may also be required.

* Just as in Software 1.0 we ***document*** and ***version-control*** code, in Software 2.0 (see [Karpathy’s blog post](https://medium.com/@karpathy/software-2-0-a64152b37c35)) we are to document and version-control dataset and labels. The ***data document*** is to be prepared with domain experts to clarify the semantics and saliency of data. It must also contain the documentation of the labelling process. It must also provide subjective assessment of the quality and quantity of the data. Further, version control is essential to overcome the natural complexity of iterative and distributed data collection and labelling. The version of the dataset and label used must accompany all results reported on ML models. [DVC](https://dvc.org/) is one tool that enables version control of the datasets (along with the model).

> In the context of AI4Bharat, the data document is the first deliverable of a project.

## First Baseline with Simple Model

* Build ***peripheral code*** modules, Train ***simple baseline models* ,** Deliver ***first module***

* In most projects there is a lot of ***peripheral code*** , i.e., code that is written besides the ML model itself. This includes setting up data pipelines, visualisation of the scale and evolution of loss, computation of metrics, and ablation tests. Often in lines of code, these components significantly outweigh the model description. It is thus recommended to write and test these components for correctness first. This can be done with a simple first model such as an out-of-the-box model from a standard ML library. This also exposes any inconsistencies in the data or label formats.

* The first model is also an opportunity to estimate ***simple baselines*** . Trying out different simple models help establishes baselines. These baselines then provide the motivation and value judgement for training significantly more complex models. These baselines should ideally be augmented by estimations of ***human baselines*** (either from collected labels or as additional labelling effort).

* At this point, it is important to make a note about reproducibility. Starting from the simple baselines and onwards, it is helpful to fix the random seeds so as to be able to replicate the obtained results.

* The end-to-end code with one or more simple models provides the first ***deliverable module*** by the ML team. This is helpful in chronicling progress to other teams. This is especially important because, unlike Software 1.0, progress in ML projects is highly non-linear: Teams can spend weeks in model tuning without any apparent output to show for it.

> In the context of AI4Bharat, the baseline models and the end-to-end module becomes the second deliverable of a project.

## Literature Survey

* A survey of recent results in scientific literature can be done earlier, but should not be deferred beyond this point. Having established baseline models and understood the quality and quantity of data, existing literature can be surveyed to understand both technical progress and application to real domains.

* As the number of research results in ML grow exponentially, finding the latest state-of-the-art results can be a challenge in itself. Result aggregators like [Papers With Code](https://paperswithcode.com/) are invaluable resources for understanding both different areas of focus within a topic and the best known results for specific benchmark tasks.

* Existing results must be commented on for the approach taken, quality of results, and also feasibility. At times, published works depend on models training which can require tens of thousands of hours of GPU training, which may not be available for a specific project.

* Appropriate choices are to be made in trading-off complexity (in model architecture, loss function, or training) with the accuracy received. This is significant because latest research works have the onus to improve upon known benchmarks and sometimes do so at enormous increase in complexity.

> In the context of AI4Bharat, a detailed literature survey is the third deliverable of a project.

## Improving Models

* In this stage, there are no clear recipes but instead there are a bunch of notional best practices.

* An early thing to try out is to build a model that ***overfits*** , i.e., the model is almost able to reach a zero loss. Often, this is best started with a very few input data points or a single batch of data. This is a sure-shot confidence booster that indicates correctness of the peripheral and machine learning codes.

* The next step is to train for more data and consequently try out more complex models. This is almost always the most time consuming step and is thought of as *hyper-parameter tuning* . One major issue is individuals and teams can sometimes tune hyper-parameters for days together with no clear insight identified. From a tooling perspective it is essential to be able to systematically capture different experiments performed on tuning different hyper-parameters and their consequences. In the context of AI4Bharat, we recommend the [MLFlow](https://mlflow.org/) open-source tool to document different experiments with hyper-parameters, metrics, and log trained models and artefacts such as images plotting confusion matrices.

* Since this phase involves regular fiddling with parameters, there is a need for efficient collaboration tools. In the context of AI4Bharat we recommend the use of [Google Colaboratory](https://colab.research.google.com/) notebooks especially now that they support GPUs deterministically. The ability to write code in blocks, comment on individual elements, share the code along with intermediate output, and maintain past versions are beneficial in collaborative coding. If the bundled free GPUs are not sufficient, Colaboratory enables connecting to cloud instances or even local machines, and also mounting of Google Drive folders when working with large data-sets.

* The central visualisation to direct choices during the hyper-parameter tuning is the loss curve. (MLFlow conveniently plots the loss curve for all experiments if one chooses to log the loss metric.) For instance, if one notices a large bias, there are several potential choices such as increase learning rate or try a larger model? In such a case, if the loss curve is rather smooth and bias is high, training for longer or training with higher learning rates are reasonable choices.

* As the intermediate result of model tuning, several practitioners prefer to overfit to the train dataset with large, well-known models such as a ResNet model with well-known algorithms like Adam. If the same model has been trained a related task, then transfer learning may accelerate the speed of finding this intermediate result. There are several repositories where pre-trained models can be found including [Model Zoo](https://modelzoo.co/) and [OpenML](https://openml.org/). Also the two popular frameworks have their own “hubs” such as the [PyTorch Hub](https://pytorch.org/hub) and the [Tensorflow Hub](https://www.tensorflow.org/hub).

* Being able to overfit is most of the problem solved. Indeed, what remains to be done is regularisation which is a better understood process. Regularisation can be done in may ways such as adding a regularisation term to the loss function, adding drop-out layers, reducing model complexity, adding a weight decay, early-stopping, and even doing some manual feature selection.

* After having identified a model that overfits and then regularised it to reduce variance, the next step involves some fine-tuning of the model. Usually, a more structured phase of hyper-parameter tuning follows for instance with grid search. Again, tools like MLFlow are essential in logging and subsequent visualisation.

> In the context of AI4Bharat, we expect most teams to spend most time in this phase. Documentation in this phase requires `mlflow` logs for each experiment, and reasoning about choices made with loss plots. Several intermediate models may be check-pointed such as a model that over-fits for a single batch, a model that over-fits for whole data, a model that is regularised, and finally different fine-tuned models.

## Analysis and Iteration

* Once a model is at hand, a detailed error analysis is to be performed with an aim to discover regularities in what the model gets wrong. For instance, in a classification task, a couple of classes may have a large confusion. Tools such as [Google Facets](https://pair-code.github.io/facets/) can help visually perform such error analysis (including the ability to plot images on large multi-dimensional plots). Of course, this is only a solution where an organisation permits sharing the data on a cloud tool.

* Often, one of the outcomes of analysis is a decision to collect more training data either to decrease bias in general or to specifically target identified errors. At this stage augmentation and even generation are possible options that have to be compared against collecting fresh data.

* Advanced methods like using an ensemble of models or bayesian hyper-parameter optimisation can increase performance. But the improvement may not be large enough to justify for the complexity of these methods. Indeed, some of these approaches are to improve the accuracy in the second or third decimal points - something essential to get on top of crowded Kaggle leaderboards.

* This overall process is iterated until we are ready to evaluate the model on the test data-set. The test data-set must be considered rather sacred and not be readily exposed to manipulation such as adding or removing data items. A good analogy is studying a course in algebra. We can study each concept as many times we like (training phase with train dataset). Then, we can check our knowledge with the end-of-chapter questions and refine our understanding of the topics (tuning phase with val dataset). Only once we feel that we are ready, we choose to get evaluated by the end-of-semester examination (evaluation on the test dataset).

* There will be situations where performance on the test data-set is not as per the set expectations, and we may have to re-iterate. But this should not be ever be done with an intention to game the performance on the test data-set.

> In the context of AI4Bharat, a detailed error analysis report and evaluation on the test data-sets form a substantial deliverable for a project.

## Deployment and There-on

* Deployment is where the rubber hits the road. Often models are “served” through containers (such as [Docker](https://www.docker.com/)) or through serverless computing infrastructure like on [AWS](https://aws.amazon.com/blogs/machine-learning/how-to-deploy-deep-learning-models-with-aws-lambda-and-tensorflow/) or [Google cloud](https://cloud.google.com/solutions/building-a-serverless-ml-model). The choice of the respective ML framework such as SageMaker or TensorFlow makes deployment to cloud seamless.

* Models for inferencing need to be tested for their performance. For models deployed on edge devices such as mobile phones to micro-controllers, model pruning would be required. This involves further model tuning and retraining.

* When deploying models to specific hardware such as mobile phones, embedded GPUs, or FPGAs, respective tool-chains need to be used. Nvidia’s [TensorRT](https://developer.nvidia.com/tensorrt) tool performs several automated optimisations for GPUs and works very well in practice. Many other such compiler toolchains are available from respective hardware vendors.

* Like any other software deployment, testing a deployed ML model is significant. Usually doing a staged rollout to the public is recommended. It is important to version control and log outputs of the models that are deployed, as permissible under privacy or data governance regulations.

* It is not uncommon that new insights are obtained during deployment. Change in data distributions, identifying newer error scenarios, would prompt a newer design iteration. These iterations driven by insights from the wild are often the most valuable.

* The story does not quite end here. Usually, the next important step is to document experiences of a project. As knowledge about ML / DL deployments within organisations is still sparse, it is vitally important to share lessons learnt and best practices.

> In the context of AI4Bharat, we define success of a project only upon deployment. Further, writing the ‘experience report’ is vitally important for sharing the lessons with the community.

---

### Acknowledgements

<table style="width:50%; margin-right:50%;">
  <tr>
    <td align="center" >
      <img src="https://avatars0.githubusercontent.com/u/49815493?v=4" width="75px;" class="rounded-circle" style="margin-bottom: 0;"/>
      <br/><b>Author</b>
    </td>
    <td align="center" style="vertical-align: middle;"> <h4>
      Pratyush Kumar
      <br/>
      IIT-Madras,  One Fourth Labs
      <br/>
      <a href="https://www.linkedin.com/in/pratyush-kumar-8844a8a3/" style="color: orange">LinkedIn</a>
    </h4></td>
  </tr>
</table>
