---
description: "Algorithmic Design Considerations for Geospatial & Temporal Big Data"
date: 2020-06-06T16:56:27+02:00
draft: false
katex: true
images: ["https://images.unsplash.com/photo-1451186242394-2b461812025b?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=3152&q=80"]
markup: "pandoc"
author: "Felix Klement"
tags:
  - Algorithms
  - Big-Data
  - Geospatial
---

![“Brown textile photo - Tan'am, Oman” by [NASA](https://unsplash.com/@nasa?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)](https://images.unsplash.com/photo-1451186242394-2b461812025b?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=3152&q=80)*“Brown textile photo - Tan'am, Oman” by [NASA](https://unsplash.com/@nasa?utm_source=medium&utm_medium=referral)*

Introduction
============

We are in an era where nearly everyone carries a variety of sensors,
either as a mobile phone, medical device or another smart appliance
(e.g. sportwatch, connected car) (IDC, n.d.). The proliferation of these
devices and rapid progress in sensor technology have enabled companies
to collect vast amounts of spatial data that provide information on the
geographical location and course other objects of interest. In addition
to the basic infrastructure requirement for the realization of the
Internet of Things paradigm, the timely analysis and management of
geodata is also often decisive for the growth of a company. The massive
amounts of data, coupled with the need for complex spatial analysis,
require high throughput and low-latency query processing (Vo, Aji, and
Wang 2014).

The topic of remote sensing (e.g. remote sensing imagery, Atmospheric
Radiation Measurement (ARM)) or large-scale simulations (e.g. climate
data) have always been \"big\". Recent advances in computation make the
spatiotemporal data even larger and place various limits on data
analysis. Spatial computation must be transformed to meet the challenges
of large spatiotemporal data (R. Vatsavai et al. 2012a).

According to Terence van Zyl et al. 2014 it is important to discuss the
geospatial temporal big data conversation within the context of the
three V's: velocity, variety, and volume. In general, spatial data can
be divided into three broad categories. These are raster, vector and
areal data. Particularly important are the challenges in the calculation
of large amounts of either raster data, point clouds or even vector
data.

Related Work
============

Research on geospatial data is of particular interest to academia and
industry. With the constantly increasing amount of data, researchers
have begun to realize that there is a great need to understand and
analyze what is happening precisely in order to get the greatest
possible benefit from the data collected. Ranga Raju Vatsavai et al.
2012 (R. Vatsavai et al. 2012a) reviews the majority of spatial data
mining algorithms by closely looking at the computational and I/O
requirements. Ahmed Eldawy and Mohamed F. Mokbel 2017 (Eldawy and Mokbel
1)    provide a case study of the work in the database community for
handling big spatial data. SATO is a spatial data partitioning framework
for scalable query processing which was proposed by Hoang Vo et al. 2014
(Vo, Aji, and Wang 2014). He introduces a way on how to analyze data
samples quickly, tear the data supported with a MapReduce based scalable
partitioning scheme and finally optimize potential queries. There is
also a good book entitled \"Applications and Challenges of Geospatial
Technology - Potential and Future Trends\" (Kumar et al. 2019) which
contains 16 different articles divided into 5 topics. These writings
contain a variety of interesting approaches to various problems in the 5
subject areas of geospatial technologies covered by the book.

Challenges
==========

There are many ongoing challenges and there is no easy way to describe a
general solution that applies to the majority of cases. Generally
speaking, it is important to minimize the complexity of space, whereby
the aim is to achieve the greatest possible linear complexity of space
and a logarithmically linear, if not less time complexity. This is often
not feasible and other techniques are needed as proposed by Vatsavai et
al. 2012 (R. Vatsavai et al. 2012b). The more sophisticated or complex
the algorithms become, the more variable and unpredictable the paths,
patterns and access frequencies to the underlying data structures may
get.

In order to identify possible challenges or opportunities for
improvement, it should be analyzed when, where and in which context the
algorithm needs certain data. To address volume and velocity challenges,
multiple iterations and alterations should be eliminated or kept as low
as possible. According to Cary et al. 2009 (Cary et al. 2009), all
infrastructure platforms and toolsets for big data in geoinformatics now
support almost any of the different algorithm styles. Nevertheless, it
is important to consider the specific infrastructure in order to avoid
possible limitations.

As mentioned above, algorithmic time complexity is a general problem
that needs to be tackled. A typical solution is the \"divide and
conquer\" algorithm, where the designers create an individual model per
subspace or evaluate per subspace (e.g. large satellite time series data
cubes that are processed using per pixel algroithms). Another typical
approach to minimize space complexity is the rule: the larger the amount
of data, the easier the model is to use.

A classical difficulty with many algorithms is the need to take into
account the relationship between each pair of observations to create a
quadratic space complexity matrix. It is inevitable that the size of
this matrix will exceed the storage capacity of the system when used on
large amounts of data. To compensate the large matrix we can basically
use three major approaches:

1.  Iteratively calculate the relationship needs

2.  For algorithms that converge on correct answers, consider to use
    batches or subsets to continuously refine model parameters

3.  Map weight matrix into lower-dimensional space (e.g. by using
    multidimensional scaling)

As many of the geospatial statistical algorithms use such a weight
matrix to deal with autocorrelation, many of these geospatial
statistical techniques become intractable solutions with regards to
geospatial big data space (R. Vatsavai et al. 2012b). Another problem is
that traditional algorithms rarely address the large data demands and
instead try to maximize the information that can be obtained from the
relatively small sample of data by making appropriate assumptions
(Shekhar et al. 2015).

State of the art algorithms {#sectionStateOfTheArt}
===========================

As already mentioned in the upper lines spatial and/or temporal
algorithms are still demanded to handle a variety of data types e.g.
raster data cubes such as time series of satellite images. In the
following we consider the current state of the art of algorithms for
geospatial and/or temporal big data.

The predominant difficulties are volume problems, as it is unlikely that
this will diminish in the near future. On the contrary, data volume will
multiply rapidly. Current solutions which tackle this problem will be
briefly discussed below. Markov random field (Li 2001) with $O(N^2)$
space requirements and $O(N^3)$ computational complexity, can be reduced
to $O(N)$ and $O(N^2)$ through the use of clever algorithms. Another
method is stochastic relaxation and iterative approaches to spatial
auto-regression, also called spatial autoregressive model (SAR). In
spatial regression, the spatial dependencies of the error term, or, the
dependet variable, are directly modeled in the regression equation
(Anselin 1988). SAR models require an $O(N^2)$ memory to store the
neighborhood matrix and without any optimizations $O(N^3)$ operations
(R. Vatsavai et al. 2012a). Many efficient techniques for solving SAR
developed in the past are investigated and compared in (Kazar et al.
2004).

Before we look at possible solution methodologies for velocity problems,
we must first classify emerging issues. In general, these can be divided
into two main classes: the so-called online and streaming algorithms.
The former have to make decisions as soon as data is received and
processed. Streaming algorithms, on the other hand, allow data to be
aggregated and examined as a batch (they are mostly used because of
limited resources). The following is a brief explanation of some
selected streaming algorithms for handling large amounts of data. A
framework for clustering real-time stream data is called D-Stream. The
algorithm is split into an online component that maps each input data
record into a grid and an offline component which calculates the density
of each grid and groups the grids with a density-based algorithm (Chen
and Tu 2007). This technique proposed by Yixin Chen and Li Tu allows
clustering of high-speed data streams without affecting the quality of
the clustering. Another approach is the Naïve Bayes classifier which is
based on Bayes' Theorem where predictors are treated as independent. The
Naïve Bayes Classifier is a datamining classification technique that
uses probabilities of attributes belonging to a class for prediction
(Netti and Radhika 2016). This approach is particularly interesting due
to its low time and space complexity.

The last category of algorithms in the field of geospatial big data to
be mentioned are variety algorithms. These in turn split into two
groups. Gandomi et al. 2015 (Gandomi and Haider 2015) explains that
traditionally the variety refers to data heterogeneity. The first group
contains all types of unstructured or semi-structured data. The
complexity here is that it's necessary to process large amounts of
unstructured data to filter out the useful information. In the second
section a large variety of features are considered from a large number
of sources. Additional temporal complexity arises with a large number of
characteristics, because they add up. This causes dimensionality
challenges and can often be correlated, which can lead to instability.
Generally variety is still an open challenge in the big data community
today. In (Robinson et al. 2017) several problems within this spectrum
are outlined, such as the development of techniques for understanding
the temporal variation of large-scale geospatial data.

Brief introduction into classical algorithms {#sectionIntroductionClassicalAlgos}
============================================

There are plenty of geospatial and temporal algorithms within the
geospatial statistics and geospatial analytics community. To give a
brief overview, we now cover some classical and common algorithms in the
short. The majority of these methods have been developed in the past for
situations with sparse data, such as Kriging. It was developed for the
spatial interpolation of geological properties using a limited number of
core samples and has an $O(N^3)$ space complexity (Ryu et al. 2002).
Geographically Weighted Regression and Logistic Regression are
conventional algorithms for classification and regression. Both have an
$O(N^3)$ space complexity, but with the use of several improved
optimization techniques it is possible to reduce their temporal
complexity significantly. A typical method in spatial and temporal
modelling considering parameterizations is the maximum likelihood
estimation with $O(N^3)$ time complexity. For a large number of
solutions, the Gaussian elimination algorithm is used. It has an
$O(N^3)$ time complexity and an $O(N^2)$ space complexity. These metrics
can be improved considerably by some clever tweaks more about this below
in Section [6](#sectionAdaptionApproaches){reference-type="ref"
reference="sectionAdaptionApproaches"}.

Adaption approaches of algorithms {#sectionAdaptionApproaches}
=================================

Within the next section some approaches and hints how to scale
algorithms for big data are presented. These procedures can be applied
to the algorithms described in the previous Section.

Divide and Conquer
------------------

An important fact to consider when working with large amounts of data is
that one $[N \times N]$ matrix is considerably larger than two
$[\frac{N}{2} \times \frac{N}{2}]$ matrices. By means of this effect,
problems can be intelligently divided into sub-problems that can be
solved. The overall result can then be cumulated from the individual
solutions. The biggest advantage of the decomposition is that now the
whole problem can be parallelized. This fact allows us the use of
frameworks like MapReduce or Hardoop to distribute the computations over
several computing units to increase the performance. In (Deng et al.
2016) the authors provide a method for space--time prediction with the
aid of the divide and conquer approach. In terms of data velocity, the
information can be divided into sub-streams, each of which can be
processed separately to archive the same results but much faster thanks
to the divide and conquer approach. In general the devide and conquer
methodology can be particularly useful for conceptually difficult
problems. Furthermore, it can be implemented very efficiently and is
also suitable for parallel processing as mentioned above.

Subsampling {#sectionSubsampling}
-----------

Subsampling is a method that is often used to reduce the complexity of
large datasets. These approaches must however guarantee that the data
examined are representative of the original data set. If the subset of
input data is selected appropriately and in such a way that it is not
biased, it may be considered adequate to allow good parameterization of
the models. In case the obtained results do not meet the expectations,
additional data can be added to increase the accuracy. In the Paper
\"Semiparametric Subsampling and Data Condensation for Large-scale Data
Analytics\" (Alhussein et al. 2019) they introduce a new
clustering-based data condensation framework for large datasets. With
the use of stratified sampling, Vonoroi diagrams and the variation
inference machinery for clustering they show that they can achieve
better performance on the used dataset then stratified sampling. The
objective of stratified sampling is to obtain the most efficient
stratified method. The goals are that the interval gap is greatest and
the internal difference is smallest (Wang and Tong 2008). On the whole,
though, the sub-sampling has its own concerns. Most critical is to find
out exactly the right sample size to ensure that all underlying
properties that are modified are represented.

Filtering
---------

Another approach in regard to challenges in big data is to filter the
data intelligently. The statistical method is slightly different from
the subsample approach (as described in Section
[6.2](#sectionSubsampling){reference-type="ref"
reference="sectionSubsampling"}), where we select a subset of the data
using some stochastic criteria. In filtering, we choose a subset of the
data using a few key criteria. It is assumed that this subset is
representative of the data we need for our modeling purposes in the area
of interest. The goal is to achieve enhanced and robust results in
spatial data analysis by decomposing a spatial variable into trend, a
spatially structured random component (i.e. a spatial stochastic signal)
and random noise. The aim is to separate spatially structured random
components from both trend and coincidental noise. Thus, the statistical
modeling leads to more substantiated statistical conclusions and useful
visualization (Griffith and Chun 2014). An example of filtering is the
use of spatial indices such as R trees. This allows us to get a feel for
the points that are close together and then use this subset of points to
build the model. This is extensively used for large amounts of data to
minimize time and space complexity and is therefore characteristic of
K-nearest neighbor algorithms.

Online Algorithms
-----------------

Online algorithms demand an immediate action for each input date when it
arrives, and preferably in real time. The necessity for such algorithms
often results from the needs and not particularly from the large data
itself. However, large amounts of data aggravate this situation and make
it even more complex to solve. There is a wide range of solutions for
various applications such as DeepWalk(Perozzi, Al-Rfou, and Skiena
2014), LIBOL(Hoi, Wang, and Zhao 2014) or DeepTrack(Li, Li, and Porikli
2016). Most use machine learning to handle the enormous amount of data
and still deliver the answer in a desirable time.

Streaming Algorithms
--------------------

Streaming algorithms are similar to online algorithms. However, the main
problem is the limited space and not the need for immediate action per
element. The response can usually be postponed to a later time, but
given finite resources, some restrictions on the amount of data to be
considered are often needed. Especially in the age of the Internet of
Things (IoT) many continuous sensor data streams, video recordings or
user interactions have to be processed. Most IoT appliance are a kind of
resource-limited device, which means it lacks performance, connectivity
(e.g. sensors in remote places) and battery capacity. The memory
limitation must therefore obviously be taken into account, and applied
algorithms can only consider some relevant subsets of the data. Galić et
al. 2014 (Galić et al. 2014) present a formal framework consisting of
data types and operations needed to support geospatial data in data
streams. This framework can be used as a foundation for the development
of a completely new geospatial data stream management system (DSMS). In
summary, streaming algorithms are classical methods to cope with the
requirements for large quantities of data, since they meet the
challenges of all three Vs.

Conclusion
==========

There are still some major open challenges that need exploration when
considering some of the strategies considered in this paper to overcome
the big data challenges in the geospatial sector. Even though we might
solve all problems in terms of feasibility and performance one day,
there are many other problems, particularly in the area of variety
space, which have not been taken fully into account yet (e.g. privacy
concerns). Zhen Lie et al. 2016 (LIU, GUO, and WANG 2016) presents in
their work four main future research areas of geospatial data, covering
spatial correlation, analytics, visualization and scientific knowledge
discovery and some general considerations for upcoming research in this
sector. If the methods that we presented in this paper are used in
combination or in conjunction with large data, the capabilities
resulting from the spatial characteristics of the data can be massively
increased to reduce temporal and spatial complexity. In summary, it is
clear that progress is being made along the road to solving the
challenges of large-scale geospatial and temporal data. Although there
are many unresolved problems, and there will never be a silver bullet.

::: {#refs .references .hanging-indent}
::: {#ref-8861966}
Alhussein, Omar, Paul D. Yoo, Sami Muhaidat, and Jie Liang. 2019.
"Semiparametric Subsampling and Data Condensation for Large-Scale Data
Analytics." In *2019 Ieee Canadian Conference of Electrical and Computer
Engineering (Ccece)*, 1--6.
<https://doi.org/10.1109/CCECE.2019.8861966>.
:::

::: {#ref-ans88}
Anselin, Luc. 1988. *Spatial Econometrics: Methods and Models*.
Dordrecht: Kluwer Academic Publishers.
:::

::: {#ref-cary2009}
Cary, Ariel, Zhengguo Sun, Vagelis Hristidis, and N. Rishe. 2009.
"Experiences on Processing Spatial Data with Mapreduce." In,
5566:302--19. <https://doi.org/10.1007/978-3-642-02279-1_24>.
:::

::: {#ref-ChenT07}
Chen, Yixin, and Li Tu. 2007. "Density-Based Clustering for Real-Time
Stream Data." In *KDD*, edited by Pavel Berkhin, Rich Caruana, and
Xindong Wu, 133--42. ACM.
<http://dblp.uni-trier.de/db/conf/kdd/kdd2007.html#ChenT07>.
:::

::: {#ref-deng2016}
Deng, Min, Wentao Yang, Qiliang Liu, and Yunfei Zhang. 2016. "A
Divide-and-Conquer Method for Space--Time Series Prediction." *Journal
of Geographical Systems* 19 (November): 1--19.
<https://doi.org/10.1007/s10109-016-0241-y>.
:::

::: {#ref-3137765}
Eldawy, Ahmed, and Mohamed F. Mokbel. 2017. "The Era of Big Spatial
Data." *Proc. VLDB Endow.* 10 (12): 1992--5.
<https://doi.org/10.14778/3137765.3137828>.
:::

::: {#ref-GALIC20141}
Galić, Zdravo, Mitra Baranović, Krešimir Križanović, and Emir Mešković.
1.    "Geospatial Data Streams: Formal Framework and Implementation."
*Data and Knowledge Engineering* 91: 1--16.
<https://doi.org/https://doi.org/10.1016/j.datak.2014.02.002>.
:::

::: {#ref-gandomi2015}
Gandomi, Amir, and Murtaza Haider. 2015. "Beyond the Hype: Big Data
Concepts, Methods, and Analytics." *International Journal of Information
Management* 35 (April): 137--44.
<https://doi.org/10.1016/j.ijinfomgt.2014.10.007>.
:::

::: {#ref-Griffith2014}
Griffith, Daniel, and Yongwan Chun. 2014. "Spatial Autocorrelation and
Spatial Filtering." In *Handbook of Regional Science*, edited by Manfred
M. Fischer and Peter Nijkamp, 1477--1507. Berlin, Heidelberg: Springer
Berlin Heidelberg. <https://doi.org/10.1007/978-3-642-23430-9_72>.
:::

::: {#ref-2627450}
Hoi, Steven C. H., Jialei Wang, and Peilin Zhao. 2014. "LIBOL: A Library
for Online Learning Algorithms." *J. Mach. Learn. Res.* 15 (1): 495--99.
:::

::: {#ref-IDCdgboit}
IDC. n.d. "Data Growth, Business Opportunities, and the It Imperatives."
<https://www.emc.com/leadership/digital-universe/2014iview/executive-summary.htm>.
:::

::: {#ref-KazarSLVP04}
Kazar, Baris M., Shashi Shekhar, David J. Lilja, Ranga Raju Vatsavai,
and R. Kelley Pace. 2004. "Comparing Exact and Approximate Spatial
Auto-Regression Model Solutions for Spatial Data Analysis." In
*GIScience*, edited by Max J. Egenhofer, Christian Freksa, and Harvey J.
Miller, 3234:140--61. Lecture Notes in Computer Science. Springer.
<http://dblp.uni-trier.de/db/conf/giscience/giscience2004.html#KazarSLVP04>.
:::

::: {#ref-kumar2019book}
Kumar, Pavan, Meenu Rani, Prem Pandey, Haroon Sajjad, and B. S.
Chaudhary. 2019. *Applications and Challenges of Geospatial Technology
Potential and Future Trends: Potential and Future Trends*.
<https://doi.org/10.1007/978-3-319-99882-4>.
:::

::: {#ref-7362006}
Li, Hanxi, Yi Li, and Fatih Porikli. 2016. "DeepTrack: Learning
Discriminative Feature Representations Online for Robust Visual
Tracking." *IEEE Transactions on Image Processing* 25 (4): 1834--48.
<https://doi.org/10.1109/TIP.2015.2510583>.
:::

::: {#ref-markovrandom}
Li, Stan. 2001. *Markov Random Field Modeling in Image Analysis*.
<https://doi.org/10.1007/978-1-84800-279-1>.
:::

::: {#ref-liu2016}
LIU, Zhen, Huadong GUO, and Changlin WANG. 2016. "Considerations on
Geospatial Big Data." *IOP Conference Series: Earth and Environmental
Science* 46 (November): 012058.
<https://doi.org/10.1088/1755-1315/46/1/012058>.
:::

::: {#ref-7726906}
Netti, Kalyan, and Y Radhika. 2016. "An Efficient Naïve Bayes Classifier
with Negation Handling for Seismic Hazard Prediction." In *2016 10th
International Conference on Intelligent Systems and Control (Isco)*,
1--4. <https://doi.org/10.1109/ISCO.2016.7726906>.
:::

::: {#ref-2623732}
Perozzi, Bryan, Rami Al-Rfou, and Steven Skiena. 2014. "DeepWalk: Online
Learning of Social Representations." In *Proceedings of the 20th Acm
Sigkdd International Conference on Knowledge Discovery and Data Mining*,
701--10. KDD '14. New York, NY, USA: Association for Computing
Machinery. <https://doi.org/10.1145/2623330.2623732>.
:::

::: {#ref-robinson2017}
Robinson, Anthony C., Urška Demšar, Antoni B. Moore, Aileen Buckley, Bin
Jiang, Kenneth Field, Menno-Jan Kraak, Silvana P. Camboim, and Claudia
R. Sluter. 2017. "Geospatial Big Data and Cartography: Research
Challenges and Opportunities for Making Maps That Matter."
*International Journal of Cartography* 3 (sup1): 32--60.
<https://doi.org/10.1080/23729333.2016.1278151>.
:::

::: {#ref-ryu2002}
Ryu, Je-Seon, Min-Soo Kim, Kyung Cha, Tae Lee, and Dong-Hoon Choi. 2002.
"Kriging Interpolation Methods in Geostatistics and Dace Model." *KSME
International Journal* 16 (May): 619--32.
<https://doi.org/10.1007/BF03184811>.
:::

::: {#ref-shekhar2015}
Shekhar, Shashi, Zhe Jiang, Reem Ali, Emre Eftelioglu, Xun Tang, Venkata
Gunturi, and Xun Zhou. 2015. "Spatiotemporal Data Mining: A
Computational Perspective." *ISPRS International Journal of
Geo-Information* 4 (October): 2306--38.
<https://doi.org/10.3390/ijgi4042306>.
:::

::: {#ref-SDMITEOPBSD}
Vatsavai, Ranga, Auroop Ganguly, Varun Chandola, Anthony Stefanidis,
Scott Klasky, and Shashi Shekhar. 2012a. "Spatiotemporal Data Mining in
the Era of Big Spatial Data: Algorithms and Applications." In
*Proceedings of the 1st ACM SIGSPATIAL International Workshop on
Analytics for Big Geospatial Data, BigSpatial 2012*, 1:1--10.
<https://doi.org/10.1145/2447481.2447482>.
:::

::: {#ref-vatsavai2012}
---------. 2012b. "Spatiotemporal Data Mining in the Era of Big Spatial
Data: Algorithms and Applications." In *Proceedings of the 1st ACM
SIGSPATIAL International Workshop on Analytics for Big Geospatial Data,
BigSpatial 2012*, 1:1--10. <https://doi.org/10.1145/2447481.2447482>.
:::

::: {#ref-SASPDPF}
Vo, Hoang, Ablimit Aji, and Fusheng Wang. 2014. "SATO: A Spatial Data
Partitioning Framework for Scalable Query Processing." In, 545--48.
<https://doi.org/10.1145/2666310.2666365>.
:::

::: {#ref-5070410}
Wang, Zhenhua, and Xiaohua Tong. 2008. "Different Spatial Sampling
Models in Geographical Analysis." In *2008 International Workshop on
Education Technology and Training 2008 International Workshop on
Geoscience and Remote Sensing*, 2:484--87.
<https://doi.org/10.1109/ETTandGRS.2008.222>.
:::
:::
