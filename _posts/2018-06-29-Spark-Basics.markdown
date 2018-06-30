---
layout: post
title: "Spark Basics"
date: 2018-06-29
categories: spark notes
---

## Basic Concepts

# DataFrame
What we used to hold data.

# Transformation vs Action
Given data, we can perform 2 kinds of operation on it:  

**Transformation**: DataFrame -> DataFrame  
example operation: filter, map, groupBy  
**Action**: DataFrame -> anything other than DataFrame  
example operation: count, collect, saveAsTextFile

# Narrow Transformation vs Wide Transformation
![Narrow Transformation Img]({{ "/assets/img/NarrowTransformation.jpg" }})
![Wide Transformation Img]( {{ "/assets/img/WideTransformation.jpg" }})

Five rows in each partition, we can see that in a narrow transformation,
each result partition only has one parent partition, and in a wide transformation,
each result partition contains rows from different parent partitions.  
Wide transformation requires a shuffle of DataFrames, it's expensive.

# Anatomy of a spark application
![Anatomy of a spark application]({{ "/assets/img/Anatomy.jpeg" }})

* All jobs in one **Spark Context / Session** is one **Spark Application**.
* Each **Action** will results in a **Job**.
* **Wide Transformations** will cut **Job** into **Stages**.
* Computation to evaluate one **Partition** in one **Stage** is called one **Task**.
