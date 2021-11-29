---
attachments: [Clipboard_2021-11-29-15-33-02.png, Data.jpg, datapipeline.jpg, diligence_value.jpg, diligence.jpg, history.jpg, Problems.jpg, scoping.jpg, userID.jpg]
title: Introduction to machine learning in production
created: '2021-11-28T15:12:42.089Z'
modified: '2021-11-29T14:39:28.421Z'
---

# Introduction to machine learning in production

## Define Data and Establish Baseline
How do you get data for trining and model success?
+ It is difficult to define the labels, they should be consistent. It can ambiguous
![Iamge](@attachment/Data.jpg)

+ Define Data
+ Label and organize the Data

## More label more ambiguity examples
The rounding boxes in a detection problem can be ambiguous. 

### User Id merge example
![Iamge](@attachment/userID.jpg)
Build a model that output 0 if the records belong to the same person or 1 if not. Another possible problem is: recognize if the information belong to a bot/spam account or a legit person ?
Is it a fraudolent transaction ?
In these cases the labeling can be ambiguous.
Definbe: What is the input x?
 + Lighting?Contrast?Resolution?
 + What feature need to be included? (even a rough gps location can be useful to understand if the account belong to the same person).

## Major type of data problems
![Iamge](@attachment/Problems.jpg)
### Unstrctured data
+ May or may not have a huge collection of unlabeled examples x
+ Humans can label more data
+ Data augmentation more likely to be helpful
### Structured data
+ May be more difficult to obtain more data
Human labeling may not be possible (with some exceptions)

### Small data
+ Clean label are critical
+ Can manually look thorugh dataset and fix label
+ Can get all the labelers to talk to each other
### Big data
+ Emphasis data process

## Small data and label consistency
We are in a situation in which we have a samll dataset and noisy labels. Big data can be noisy as well. If you have clean a clear labels even if the dataset is small the model can obtain good results. 
Big data problems can have small data challanges too => long tail of rare events: Web search, Self-driving cars, Product recommendation system.

## Improving label consistency
## Human level performance (HLP)
HLP is sometimes missused. Estiomate Bayes error/irreducible error analysis and priotirization. Establish the baseline.
#### Other uses of HLP
+ In Academia: beat HLP to get published
+ HLP helps establish a more reasonable target
+ Prove ML system us superior to hunmans at the job (tricky)

Human Level Performance is risen by improving label consistency and that ultimately results in better learning outcomes performance as wel

## Raising HLP
First, HLP is important for problems where human-level performance can provide a useful reference. I do measure it and use it as a reference for what might be possible and to drive air analysis and prioritization. Having said that, when you're measuring HLP, if you find the HLP is much less than 100 percent, also ask yourself if some of the gap between HLP and complete consistency is due to inconsistent labeling instructions. Because if that turns out to be the case, then improving labeling consistency will raise HLP and also give cleaner data for your learning algorithm, which will ultimately result in better machine-learning algorithm performance. Guess what I hope you take away from this video. HLP is useful and important for many applications. For problems where I think how well humans perform is a useful reference, I do measure HLP and I use that to get a sense of what might be possible, and also use HLP to drive error analysis and preservation. Having said that, if, in the process of measuring HLP, you find that HLP is much less than perfect performance, much lower than 100 percent. This is also worth asking yourself, if that gap between HLP and 100 percent accuracy may be due to inconsistent labeling instructions. Because if that's the case, then improving labeling consistency will both raise HLP, but more importantly help you get cleaner and more consistent labels which will improve your learning algorithm's performance


# Label and Organize Data
## Obtaning Data
If training the model takes 2 days do not spend to much time collecting data. Get in the iteration loop as quick as possible
Model + Hyperparameters + Data -> Trainnig -> Error analysis
Excpetion if you already know you need a big database.

## Data pipeline
+ proof of concept
+ Production phase
  + Tensor flow transform, Apache beam, Airflow

# Meta-data, data provenance and lineage
Data pipeline:

![Iamge](@attachment/datapipeline.jpg)
Then you discover errors in the spam dataset (ip addresses). It will change the systems in your pipelinem that are often made by different people/departament -> keep track of data provenance and lineage (where it comes from and sequence steps).

## Meta-data
+ example: Manufacturing visual inspection: the iamge is the data and the time, factory, line #, camera settings, phone model, inspector ID are meat-data

## Balanced train/dev/test splits
Example: Visual inspection: 100 examples, 30% positive (defective)
+ Train/dev/test: 60%,20%,20%
+ Random split: 21,2,7 positive example 35%,10%,35%
+ Want: 18,6,6 -> 30%,30%,30% balanced split
No need to worries about this for large data-set

# Scoping

## What is Scoping
![Iamge](@attachment/scoping.jpg)
## Scoping process
+ Brainstorm business problems (not AI problems)
+ Brainstorm AI solutions
+ Asses the feasibility and value of potential solutions
+ Determine milestones
+ Budget for resources

But even then I find it worthwhile to first engage in divergent thinking where you brainstorm a lot of possibilities. To be followed by conversion thinking where you then narrow it down to one or a small handful of the most promising projects to focus on.

## Diligence on feasibility and value
+ Use external benchmark (literature, other company, competitor)

I would give a human too same data as would be fed to a learning algorithm and just ask, can a human given the same data, perform the tasks such as can the human given a picture of a scratch smartphone, perform the task of detecting scratches reliably? If a human can do it, then that significantly increases the hope they can also get the learning algorithm to do it.

 ![Iamge](@attachment/diligence.jpg)

(Human eyes has more contrast than cameras)
Do we have features that ar predicitive ?
+ Gicen past purchases, predict future purchases
+ Given weather, predict shopping mall foot traffic
+ Given DNA info, predict heart disease
+ Given social media chatter, predict demand for clothing style
+ Given history of stock's price, predict future price of that stock (it seems not technically feasable (Andrew opinion's))

![Iamge](@attachment/history.jpg)

## Diligence on value
![](@attachment/diligence_value.jpg)

## Milestones and resourcing
+ ML metrics (accuracy, precision, recall etc)
+ Software metrics (letency, thorughput, etc.)
+ Business metrics (revenue etc)
+ Resources needed (data, personnel, help from other tems)
+ Timeline



















