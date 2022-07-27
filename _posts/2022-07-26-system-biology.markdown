---
layout: post
title:  "Computational Systems Biology"
date:   2022-07-26 09:34:43 +0000
---

Biology is the study of life. Its goal is to gain comprehensive knowledge of how cells and organisms work, individually or in groups.
Systems biology is a new speciality area that actually has exactly the same goals and purposes as general biology, namely, to understand how life works. But, in contrast to traditional biology, systems biology purposes these goals with a whole new sets of tools that come from mathematics, statistics, computing and engineering, in addition to biology, biochemistry, and biophysics. System biology utilizes these tools to determine the specific roles of the many diffirent components that we find in living organisms, how these components interact with each other, and how they collaborate to create and support life. A prominent feature of systems biology is its heavy use of the enormous capacity of modern computers to store, manage, analyze and interpret huge amounts of data. In addition, systems biology readily recognizes that detailed knowledge of the molecules and structure of the life is crucial, and that traditional research absolutely needs to continue, but it stresses the point that this knowledge alone is insufficient. We need methods of putting the parts together, new ways of thinking and new methods of analysis that allow us to understand how the building blocks interact and what controls and regulates these interactions, and we need these studies to be done on huge numbers of observations simultaneously. 

The Scientific Revolution of the 17th centry brought real change with two great advances in biology. First, the microscope was invented and paved the way to an entirely new world of life: microbiology. The second novelty was a firm rule set for valid research, called *scientific method*. This method demands that exact science follow well-defined steps of formulating a hypothesis, testing this hypothesis with experiments, analyzing the results, and based on the results and their interpretation, formulating a new hypothesis. Systems biology improved this methodology complementarily, and lead to major breakthroughs, which we will try to explain with specific examples later in this post.


# The --omics revolution
In the past, experiments were time consuming and expensive and data were therefore often scarce. The so-called *--omics revolution* has changed that to a point where we often have so many data that we can not make sense of them and need to resort to sophisticated computing methods. As "omics" is not really a word, but rather a suffix that has been attached to various biological terms to indicate "all of it" or "a lot of it". The best known example is *genomics*, which means studying the structure, function and evolution of genes; not one gene at a time, as it used to be done a few decades ago, but for all genes at the same time.

The --omics revolution has not only generated huge datasets, it has turned the tried-and-true scientific method on its head. The central position of a strong hypothesis has vanished, and the new mindset is *exploratory data analysis*, which were translated into the lax mandate: "lets see what'is out there and then we will try to figure out what it means". In contrast to the traditional scientific method, there is no hypothesis that gene X or gene Y might have something to do with that particular cancer, but rather all genes are examined in the hope of detecting *patterns*. Because resulting datasets consists of thousands of data points, they are evaluated with computational methods of statistical machine learning, which reveal *patterns in the data*. 


To summarize this intro section by comparing the traditional and new scientific method of experimental (systems) biology 

**The traditional scientific method of biology**
1. Make an observation
2. Ask a question regarding the observation
3. Do background research to see what is known about the question
4. Refine the question to a point that it can be formulated as a hypothesis
5. Design an experiment to test the hypothesis and execute it
6. Analyse data resulting from the experiment and determine to what degree the results support hypothesis
7. If the results do not support the hypothesis, go back to 2,3, or 4
8. If the experiment results do support hypothesis, new insights are gained, Share these insights with the scientific community
9. Usually new insights lead to additional questions. Formulate new hypothesis that target these questions


**The new scientific method of experimental systems biology, applied to a disease.**
1. Identify an interesting phenomenon, such as a disease
2. Decide whether protemics, or metabolomics is most promising
3. Perform the same --omics analysis of genes, proteins and/or metobolites with a sample from a healthy person and from a person with a disease.
4. Collect significant diffirences between corresponding measurements in the two samples, using methods of machine learning
5. Assemble these diffirences into normal and disease profiles
6. Formulate hypothesis explaining the differences between these profiles
7. Perform traditional experiments testing the most promising hypothesis
8. If the results do not support the hypothesis, go back to 2,3 or 6.
9. If the experiment results do support one of the hypothesis, new insights are gained and should be shared with the scientific community
 
## Data, Information, Knowledge, Understanding

The new methods of --omics biology, combined with more traditional experiments, have the capacity of generating more high quaility data than ever before. So, why is not that sufficient? Before answering this question, lets explain what is the difference between these terms

  - **Data:** Data are discrete, objective facts, often without a context. Lets say you read "rainfall at the airport was 2.6 centimeters". You dont know what does that mean, is 2.6 centimeters a lot?
  - **Information:** Generally information consists of processed data augmented/enriched with *metadata* which consists of such meaning, together with some context and background. 
  - **Knowledge:** Is mixture of synthesize information, context, experience and even value judgement. It explains how the information was obtained or generated, recognizes patterns in information, often procedures for assessing a situation, and guides expectations regarding the future
  - **Understanding:** Understand interprets the knowledge. It provides casuality and rationale for a phenomenon, detail and pattern in data. Understanding helps us explain why something is the way it is.

Statistical Machine learning helps us to gain the knowledge and understand it by using given data.

## Machine Learning (ML)

ML is a scientific field that studies datasets by combining statistics with heavy-duty computing. The main goal of ML is to train computer programs (*algorithms*) to find something in a dataset that had not been known before, such as an association between two types of data. The accuracy of findings steadily improves as more data becomes available.

ML requires training that can happen with or without human supervision. In the former case, the human supervisor gives the algorithm a large dataset, lets say, containing data from healthy individuals and from individuals with lung cancer, informs the computer which individuals have cancer and which dont, and instructs the algorithm to find features or patterns in the dataset that distinguish healthy from diseased individuals. In the latter case, algorithm learns without human supervision. It does not know which individuals actually have cancer and which dont. Instead, the algorithm is asked to determine whether there are *any* significant patterns in the dataset. 


## Interdependencies of biological systems

Biological systems are super complex. In this part, I will try to write about some of the complexities in different biologies systems and how computational systems biologycan help to understand them using statistical machine learning methods.

Even the simplest of organisms rely on uncounted molecular processes that allow them to thrive, propagate, and respond threats from predators, parasites, and the environment. They contain thousands of genes defining each organism's set of functions and features; proteins that provide structure, control biochemical reactions, and serve as means of transporting molecules; metabolites for energy and other purposes; many signaling mechanisms that regulate all aspects of life. All of these components are interacting with each other continously, and at a molecular level this organization is captures in *central dogma*.

Central dogma holds that the flow of information in the cells starts with genes (DNA sequences), which are *transcribed* into messenger RNA (mRNA), which in turn *translated* into proteins. Proteins play structural and signaling roles and control the conversion of food into energy and into metabolites, that is, the numerous and diverse chemical compounds required for life. However, the information flow is regulated in multiple ways. Some proteins serve as *transcription factors*, which control the transcription of genes into mRNAs. Some of RNA can regulate or even stop the transciption of specific DNA sequences. Metabolites can trigger or prevent the expression of specific genes. The consequence of these insights is that the simple one-way process represented in central dogma is in truth much more complicated: information flows through a higly regulated systems with many feedback signals. 
![Central Dogma](/assets/central-dogma.jpeg) 
 


### Resources
 - Systems Biology: A very short introduction
