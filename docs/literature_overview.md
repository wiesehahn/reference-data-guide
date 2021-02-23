
# Reference Data for Random Forest

## A Guide for Tree Species Classification with Multispectral Satellite Imagery

Often, one set of reference data is used for training and validation.
Whereas splitting the data set in a training set and a validation set is
a valid option as long as they are independent (?), using the same data
for both does not result in an unbiased accuracy estimation. But also
splitting a data set and using one part for the prediction and and the
other part for the validation is in many cases not the best option as
different requirements exist. Training data requirements are dependent
on the classification algorithm and do not necessarily need to be
uncorrelated. For an unbiased estimation of classification accuracy the
validation data on the other hand needs to follow a probability sampling
scheme.

## Training data

### General Questions

#### Number of training samples

How many training data samples should be used?

In addition to a total number (5400)
[Colditz](#ref-colditzEvaluationDifferentTraining2015)
([2015](#ref-colditzEvaluationDifferentTraining2015)) also reported a
size relative to the study area (0.25%). Many studies and technical
notes report a minimal number of samples per class (e.g. 50).

According to [Millard and
Richardson](#ref-millardImportanceTrainingData2015)
([2015](#ref-millardImportanceTrainingData2015)) as many training data
samples as possible are recommended to improve classification accuracy
and stability. [Rodriguez-Galiano et
al.](#ref-rodriguez-galianoAssessmentEffectivenessRandom2012)
([2012](#ref-rodriguez-galianoAssessmentEffectivenessRandom2012)) in
contrast, tested the effect of training data reduction and found that RF
is not sensitive to a reduction until a certain threshold. They also
state that training data size is not problematic for homogeneous
classes, but larger number of samples are necessary for classes with
high variability.

Hypothesis: The more the better. Optimal number of training samples
(consent between cost and classification result) is dependent on the
number of classes and class separability.

#### Distribution within classes

Is it better to use homogeneous or heterogeneous data within classes?

A number of studies suggest that training data should be heterogeneous
to represent all the variability present in a category ([Pal and Mather
2003](#ref-palAssessmentEffectivenessDecision2003); [Rodriguez-Galiano
et al. 2012](#ref-rodriguez-galianoAssessmentEffectivenessRandom2012)).
But as [Colditz](#ref-colditzEvaluationDifferentTraining2015)
([2015](#ref-colditzEvaluationDifferentTraining2015)) and [Millard and
Richardson](#ref-millardImportanceTrainingData2015)
([2015](#ref-millardImportanceTrainingData2015)) already state, a widely
used method for training data collection in large-area mapping projects
is to use polygons in homogeneous areas, which produces highly clustered
and spatially auto-correlated training samples. Training data does not
necessarily have to be spatially evenly distributed. However, doing so
(e.g. via systematic or simple random sampling) ensures spectrally
heterogeneous training data which is recommended.

Should outliers be removed from training data samples a priori?

According to the literature Random Forest classification is not very
sensitive to outliers and hence it might not be necessary to treat
outliers ([Rodriguez-Galiano et al.
2012](#ref-rodriguez-galianoAssessmentEffectivenessRandom2012)). This
might be the reason why most studies do not mention outliers in their
training data set. Considering the principle to select heterogeneous
training data the removal of outliers might even be counterproductive.
On the other side training data might contain mislabeled data and the
treatment of outliers per class could assist removing false samples from
training data. The effect is unclear as it is not known if and how many
samples are labeled wrong and also it might be unnecessary as RF is
relatively robust to noise ([Rodriguez-Galiano et al.
2012](#ref-rodriguez-galianoAssessmentEffectivenessRandom2012)).

### Questions for classes of different sizes

#### Distribution between classes

How to distribute the training data among classes?

Class imbalance is known for increasing the bias towards the majority
class ([Dittman, Khoshgoftaar, and Napolitano
2015](#ref-dittmanEffectDataSampling2015)). [Dittman, Khoshgoftaar, and
Napolitano](#ref-dittmanEffectDataSampling2015)
([2015](#ref-dittmanEffectDataSampling2015)) found that RF is relatively
robust to imbalanced data.

Many studies suggest to balance the training data in order to achieve
good classification results. But usually these studies make no
assumptions about the underlying class abundance in the data set they
want to classify. Either they simply do not have this information or
they assume it is equally distributed. But also for heavily imbalanced
data sets many studies suggest some kind of resampling to balance the
training data. The majority deals with two-class problems where one
class is rare and this class should be classified with high precision
(e.g. tumor cells). For this case they have shown that a balanced data
set performs better in predicting the rare class. Land-cover classes are
seldom evenly distributed in the landscape. The same applies for tree
species. Also, the goal is to produce a land-cover map with an overall
high accuracy and not just for one class. Hence, it is of interest to
which degree the distribution of training samples among classes effects
the classification outcome.
[Colditz](#ref-colditzEvaluationDifferentTraining2015)
([2015](#ref-colditzEvaluationDifferentTraining2015)),
[Freeman](#ref-freemanEvaluatingEffectivenessDownsampling2012)
([2012](#ref-freemanEvaluatingEffectivenessDownsampling2012)) and
[Millard and Richardson](#ref-millardImportanceTrainingData2015)
([2015](#ref-millardImportanceTrainingData2015)) found that area
proportional sampling of training data performs better than balanced
data. [Mellor](#ref-mellorExploringIssuesTraining2015)
([2015](#ref-mellorExploringIssuesTraining2015)) also found that a fine
imbalance can be introduced (between best and worst performing classes)
to improve the accuracy. Nevertheless, most studies use balanced
training data sets.

#### Methodoloy for redistribution

If data has to be resampled what method should be used?

In the case of systematic sampling or simple random sampling the
training data is area-proportional and thus fulfills the recommendations
in the literature (see above). But there might also be cases when
resampling is necessary, for example if training data is collected in
subjective polygons and should be resized to fit actual class
proportions or if the classification of difficult classes should be
enhanced. Many studies evaluated the performance of various resampling
techniques for the classification of imbalanced classes in general and
for RF in particular. The most widely used methods are Upsampling (syn.
Oversampling), where samples from the rare class are drawn multiple
times to increase samples from this class, and Downsampling (syn.
Undersampling), where only a part of the majority class is sampled to
reduce the size. In Synthetic Minority Oversampling (SMOTE) new
synthetic samples are created and drawn from the feature space of the
minority class. Undersampling of the majority class is integrated in the
RF algorithm and called Balanced Random Forest (BRF). Weighted Random
Forest (WRF) uses the idea of cost-sensitive learning.

[Dittman, Khoshgoftaar, and
Napolitano](#ref-dittmanEffectDataSampling2015)
([2015](#ref-dittmanEffectDataSampling2015)) found no statistical
difference between under-sampling, over-sampling and SMOTE-sampling for
RF. And also [McCarthy, Zabar, and
Weiss](#ref-mccarthyDoesCostsensitiveLearning2005)
([2005](#ref-mccarthyDoesCostsensitiveLearning2005)) found no consistent
winner between cost-sensitive learning, up-sampling and down-sampling.
But they conclude that cost-sensitive learning tends to outperform
sampling methods for large data sets and that up-sampling tends to
perform better than down-sampling for small data sets. [Japkowicz and
Stephen](#ref-japkowiczClassImbalanceProblem2002)
([2002](#ref-japkowiczClassImbalanceProblem2002)) also propose to use
cost-sensitive learning over sampling methods. [C.
Chen](#ref-chenUsingRandomForest2004)
([2004](#ref-chenUsingRandomForest2004)) propose Balanced Random Forest
(sampling) and Weighted Random Forest (cost-sensitive) to give good
results but state that WRF might be more vulnarable to noise (mislabeled
data). [Freeman](#ref-freemanEvaluatingEffectivenessDownsampling2012)
([2012](#ref-freemanEvaluatingEffectivenessDownsampling2012)) evaluated
the effectiveness of down-sampling and found that it did not improve
classification performance. Instead they suggest to use threshold
optimization.

### Options not directly related to training data

#### Number of predictor variables

Is it better to use more or less predictor variables?

Some studies perform feature selection methods to reduce the number of
predictor variables. In most cases this is rather used to reduce the
computational effort than to improve the classification accuracy. Most
studies however, simply choose predictor variables a priori and stick to
them. [Millard and Richardson](#ref-millardImportanceTrainingData2015)
([2015](#ref-millardImportanceTrainingData2015)) found that many
variables introduced noise in the classification and accuracy was lower.
They advise to remove correlated variables and use only the most
important variables for prediction.

#### Hyperparameter

Number of trees Minimum Leaf size Number of variables per split

## Key Statements

[Rodriguez-Galiano et
al.](#ref-rodriguez-galianoAssessmentEffectivenessRandom2012)
([2012](#ref-rodriguez-galianoAssessmentEffectivenessRandom2012))

-   “RF has low sensitivity to the training set size reduction”
-   “RF is relatively little noise sensitive”
-   used equal number of samples per class
-   as RF generates unbiased estimation of error (oob) a validation data
    set is unnecessary
-   “For homogeneous classes, training data size is not problematic, but
    it is necessary to use a larger number of training sites for classes
    with high variability.”

[Colditz](#ref-colditzEvaluationDifferentTraining2015)
([2015](#ref-colditzEvaluationDifferentTraining2015))

-   “only a few studies have focused on training data allocation
    schemes, such as between-class sample balance or the structure of
    heterogeneous samples”
-   “classification trees may suffer from an unbalanced sample size
    between classes because the number of samples in each leaf defines
    the class”
-   “A few studies recommend heterogeneous training data for discrete
    classification but most large-area mapping projects select
    homogeneous areas for training”
-   validated with equal number of samples per class
-   “For classification trees, heterogeneous training pixels are
    recommended”
-   “Area-proportional allocation is recommended”

[Freeman](#ref-freemanEvaluatingEffectivenessDownsampling2012)
([2012](#ref-freemanEvaluatingEffectivenessDownsampling2012))

-   “balancing the number of presences and absences in a training data
    set by down-sampling did not improve predictive models”
-   “By seeking to minimize overall error, such algorithms can increase
    the error rate for the rare class”
-   “in theory, Balanced models are proposed as a way of improving
    predictions in species with very low or very high prevalence.
    Instead we found that when the threshold is kept at the default of
    0.5, Balanced models actually did worse than the Baseline models for
    our very low prevalence species”
-   “the default Baseline model tended to over predict the high
    prevalence species and under predict the low prevalence species,
    while the default Balanced model over predicted all but one of our
    species and highly over predicted the rare species”
-   “the predictive performance in terms of AUC, kappa and prevalence of
    the Balanced model was considerably improved by threshold
    optimization”

[Chao Chen and Breiman](#ref-chenUsingRandomForest2004a)
([2004](#ref-chenUsingRandomForest2004a))

-   “similar to most classifiers, RF can also suffer from the curse of
    learning from an extremely imbalanced training data set. As it is
    constructed to minimize the overall error rate, it will tend to
    focus more on the prediction accuracy of the majority class, which
    often results in poor accuracy for the minority class”

-   “Both methods \[Balanced RF and Weighted RF\] are shown to improve
    the prediction accuracy of the minority class, and have favorable
    performance compared to the existing algorithms”

[McCarthy, Zabar, and Weiss](#ref-mccarthyDoesCostsensitiveLearning2005)
([2005](#ref-mccarthyDoesCostsensitiveLearning2005))

-   “between cost-sensitive learning, up-sampling, and down-sampling,
    there is no clear or consistent winner for maximizing classifier
    performance”
-   for small data sets “up-sampling clearly does much better than
    down-sampling and cost-sensitive learning”
-   “for the large data sets, cost-sensitive learning does often yield
    the best results”

[Japkowicz and Stephen](#ref-japkowiczClassImbalanceProblem2002)
([2002](#ref-japkowiczClassImbalanceProblem2002))

-   linearly separable (not complex) data is not sensitive to imbalance
-   sensitivity to imbalance increases with complexity level
-   class imbalance is not a problem if training set size is large
-   “the higher the degree of class imbalance the higher the complexity
    of the concept and the smaller the overall size of the training set,
    the greate the effect of class imbalances”
-   all methods (under-, oversampling, cost-modifying) improve
    classification
-   under-sampling is least effective (in case where no data is
    irrelevant e.g. when majority class consists of repeated samples)
-   over-sampling is quite effective in these cases
-   cost-modifying is more effective than resampling

[Mellor](#ref-mellorExploringIssuesTraining2015)
([2015](#ref-mellorExploringIssuesTraining2015))

-   “the error rate of the RF classifier is relatively insensitive to
    mislabelled training data”
-   “balanced training data resulted in the lowest overall error rates
    for classification experiments”
-   “imbalance can be introduced to improve error rates of more
    difficult classes, without adversely affecting overall
    classification accuracy”

[Millard and Richardson](#ref-millardImportanceTrainingData2015)
([2015](#ref-millardImportanceTrainingData2015))

-   “classifiers may be biased where the proportions of training or
    validation data classes are distributed unequally or are imbalanced
    relative to the actual land cover proportions”
-   “increasing sample size significantly should lead to improved
    classification accuracy”
-   “Once the proportion of the class of interest was increased to near
    its actual proportion in the landscape, that class always became the
    class with the lowest proportion-error. As its proportion increased
    beyond its actual proportion in the landscape, rfOOB error tended
    towards zero and the proportion-error for that class increased”
-   “As the proportion of the class of interest in the training data set
    increased, the resulting proportion of that class in the predicted
    image also increased”
-   “As spatial autocorrelation of training data increased, rfOOB error
    decreased while independent assessment error increased”
-   “RF image classification is highly sensitive to training data
    characteristics, including sample size, class proportions and
    spatial autocorrelation”
-   “larger training sample sizes are recommended to improve
    classification accuracy”
-   “variable reduction should be performed to obtain the optimum
    classification. When high dimensional datasets were used,
    classification results were noisy”
-   “classification results reflected the forced proportions”
-   “These results indicate the importance of carefully selecting
    training data sample points without bias and so that landscape
    proportions are maintained”
-   “High-dimension datasets should be reduced. Using only important,
    uncorrelated variables”
-   “As many training and validation sample points should be collected
    as possible”
-   “An unbiased sampling strategy that ensures representative class
    proportions should be used”
-   “spatial autocorrelation should be minimized within the training and
    validation data sample points”

## Schemes used in selected studies

[Wessel, Brandmeier, and
Tiede](#ref-wesselEvaluationDifferentMachine2018)
([2018](#ref-wesselEvaluationDifferentMachine2018))

-   equal number of samples per class
-   from inventory data
-   only pure stands
-   multiple samples per area

[Persson, Lindberg, and
Reese](#ref-perssonTreeSpeciesClassification2018)
([2018](#ref-perssonTreeSpeciesClassification2018))

-   from systematic grid and subjective plots
-   only dominated stands (&gt;70% BA)
-   samples for rare classes were added (sampling scheme between equal
    and proportional)
-   reference used for training and testing (with cross-validation)

[Lim et al.](#ref-limMachineLearningTree2020)
([2020](#ref-limMachineLearningTree2020))

-   equal number of samples per class
-   only sparse information about the validation data and process

[Hościło and Lewandowska](#ref-hosciloMappingForestType2019)
([2019](#ref-hosciloMappingForestType2019))

-   (almost) equal number of samples per class
-   from inventory data and randomly added plots
-   only dominated stands

[Grabska et al.](#ref-grabskaForestStandSpecies2019)
([2019](#ref-grabskaForestStandSpecies2019))

-   more or less proportional number of samples per class
-   from inventory data
-   only pure (main species) or dominant (rare species) stands were
    selected (and spectrally homogeneous)
-   all pixels within polygon per area

[Bjerreskov, Nord-Larsen, and
Fensholt](#ref-bjerreskovForestTypeTree2021)
([2021](#ref-bjerreskovForestTypeTree2021))

-   from inventory data
-   validation data from different plots
-   only dominant stands
-   more or less proportional reference data (train and validation)

[Kollert et al.](#ref-kollertExploringPotentialLand2021)
([2021](#ref-kollertExploringPotentialLand2021))

-   reference data from subjective polygons
-   only pure stands but some species merged in one class
-   seperation between train and validation polygons (spatially
    uncorrelated between but correlated within reference sets)
-   folded cross-validation used
-   unequal number of reference samples but not proportionally

[Breidenbach et al.](#ref-breidenbachNationalMappingEstimation2020)
([2020](#ref-breidenbachNationalMappingEstimation2020))

-   training data from NFI plots (proportional)
-   for all unsplit forest plots the dominant species was determined
-   validation data from independent stand inventories
-   validation data for pure stands (&gt;95%)
-   models were validated using cross-validation with training data
-   models were validated with independent forest stands

<div id="refs" class="references csl-bib-body hanging-indent">

<div id="ref-bjerreskovForestTypeTree2021" class="csl-entry">

Bjerreskov, Kristian Skau, Thomas Nord-Larsen, and Rasmus Fensholt.
2021. “Forest Type and Tree Species Classification of Nemoral Forests
With Sentinel-1 and 2 Time Series Data,” January.
<https://doi.org/10.20944/preprints202101.0235.v1>.

</div>

<div id="ref-breidenbachNationalMappingEstimation2020"
class="csl-entry">

Breidenbach, Johannes, Lars Waser, Misganu Debella - Gilo, Johannes
Schumacher, Johannes Rahlf, Marius Hauglin, Stefano Puliti, and Rasmus
Astrup. 2020. *National Mapping and Estimation of Forest Area by
Dominant Tree Species Using Sentinel-2 Data*.

</div>

<div id="ref-chenUsingRandomForest2004" class="csl-entry">

Chen, C. 2004. “Using Random Forest to Learn Imbalanced Data.” 2004.
[/paper/Using-Random-Forest-to-Learn-Imbalanced-Data-Chen/2138b37bfced70599d26dfccbf93a8e7a4b7ad85](https:///paper/Using-Random-Forest-to-Learn-Imbalanced-Data-Chen/2138b37bfced70599d26dfccbf93a8e7a4b7ad85).

</div>

<div id="ref-chenUsingRandomForest2004a" class="csl-entry">

Chen, Chao, and Leo Breiman. 2004. “Using Random Forest to Learn
Imbalanced Data.” *University of California, Berkeley*, January.

</div>

<div id="ref-colditzEvaluationDifferentTraining2015" class="csl-entry">

Colditz, RenÃÂ Roland. 2015. “An Evaluation of Different Training Sample
Allocation Schemes for Discrete and Continuous Land Cover Classification
Using Decision Tree-Based Algorithms.” *Remote Sensing* 7 (8, 8):
9655–81. <https://doi.org/10.3390/rs70809655>.

</div>

<div id="ref-dittmanEffectDataSampling2015" class="csl-entry">

Dittman, David J., Taghi M. Khoshgoftaar, and Amri Napolitano. 2015.
“The Effect of Data Sampling When Using Random Forest on Imbalanced
Bioinformatics Data.” In *2015 IEEE International Conference on
Information Reuse and Integration*, 457–63. San Francisco, CA, USA:
IEEE. <https://doi.org/10.1109/IRI.2015.76>.

</div>

<div id="ref-freemanEvaluatingEffectivenessDownsampling2012"
class="csl-entry">

Freeman, Elizabeth A. 2012. “Evaluating Effectiveness of down-Sampling
for Stratified Designs and Unbalanced Prevalence in Random Forest Models
of Tree Species Distributions in Nevada.” *Ecological Modelling*, 10.

</div>

<div id="ref-grabskaForestStandSpecies2019" class="csl-entry">

Grabska, Ewa, Patrick Hostert, Dirk Pflugmacher, and Katarzyna
Ostapowicz. 2019. “Forest Stand Species Mapping Using the Sentinel-2
Time Series,” 24.

</div>

<div id="ref-hosciloMappingForestType2019" class="csl-entry">

Hościło, Agata, and Aneta Lewandowska. 2019. “Mapping Forest Type and
Tree Species on a Regional Scale Using Multi-Temporal Sentinel-2 Data.”
*Remote Sensing* 11 (8): 929. <https://doi.org/10.3390/rs11080929>.

</div>

<div id="ref-japkowiczClassImbalanceProblem2002" class="csl-entry">

Japkowicz, Nathalie, and Shaju Stephen. 2002. “The Class Imbalance
Problem: A Systematic Study.” *Intelligent Data Analysis* 6 (5): 429–49.

</div>

<div id="ref-kollertExploringPotentialLand2021" class="csl-entry">

Kollert, Andreas, Magnus Bremer, Markus LÃÂ¶w, and Martin Rutzinger.
2021. “Exploring the Potential of Land Surface Phenology and Seasonal
Cloud Free Composites of One Year of Sentinel-2 Imagery for Tree Species
Mapping in a Mountainous Region.” *International Journal of Applied
Earth Observation and Geoinformation* 94 (February): 102208.
<https://doi.org/10.1016/j.jag.2020.102208>.

</div>

<div id="ref-limMachineLearningTree2020" class="csl-entry">

Lim, Joongbin, Kyoung-Min Kim, Eun-Hee Kim, and Ri Jin. 2020. “Machine
Learning for Tree Species Classification Using Sentinel-2 Spectral
Information, Crown Texture, and Environmental Variables.” *Remote
Sensing* 12 (12): 2049. <https://doi.org/10.3390/rs12122049>.

</div>

<div id="ref-mccarthyDoesCostsensitiveLearning2005" class="csl-entry">

McCarthy, Kate, Bibi Zabar, and Gary Weiss. 2005. “Does Cost-Sensitive
Learning Beat Sampling for Classifying Rare Classes?” In *Proceedings of
the 1st International Workshop on Utility-Based Data Mining*, 69–77.
UBDM ’05. New York, NY, USA: Association for Computing Machinery.
<https://doi.org/10.1145/1089827.1089836>.

</div>

<div id="ref-mellorExploringIssuesTraining2015" class="csl-entry">

Mellor, Andrew. 2015. “Exploring Issues of Training Data Imbalance and
Mislabelling on Random Forest Performance for Large Area Land Cover
Classification Using the Ensemble Margin.” *ISPRS Journal of
Photogrammetry and Remote Sensing*, 14.

</div>

<div id="ref-millardImportanceTrainingData2015" class="csl-entry">

Millard, Koreen, and Murray Richardson. 2015. “On the Importance of
Training Data Sample Selection in Random Forest Image Classification: A
Case Study in Peatland Ecosystem Mapping,” 27.

</div>

<div id="ref-palAssessmentEffectivenessDecision2003" class="csl-entry">

Pal, Mahesh, and Paul M Mather. 2003. “An Assessment of the
Effectiveness of Decision Tree Methods for Land Cover Classification.”
*Remote Sensing of Environment* 86 (4): 554–65.
<https://doi.org/10.1016/S0034-4257(03)00132-9>.

</div>

<div id="ref-perssonTreeSpeciesClassification2018" class="csl-entry">

Persson, Magnus, Eva Lindberg, and Heather Reese. 2018. “Tree Species
Classification with Multi-Temporal Sentinel-2 Data,” 17.

</div>

<div id="ref-rodriguez-galianoAssessmentEffectivenessRandom2012"
class="csl-entry">

Rodriguez-Galiano, V. F., B. Ghimire, J. Rogan, M. Chica-Olmo, and J. P.
Rigol-Sanchez. 2012. “An Assessment of the Effectiveness of a Random
Forest Classifier for Land-Cover Classification.” *ISPRS Journal of
Photogrammetry and Remote Sensing* 67 (January): 93–104.
<https://doi.org/10.1016/j.isprsjprs.2011.11.002>.

</div>

<div id="ref-wesselEvaluationDifferentMachine2018" class="csl-entry">

Wessel, Mathias, Melanie Brandmeier, and Dirk Tiede. 2018. “Evaluation
of Different Machine Learning Algorithms for Scalable Classification of
Tree Types and Tree Species Based on Sentinel-2 Data.” *Remote Sensing*
10 (9): 1419. <https://doi.org/10.3390/rs10091419>.

</div>

</div>
