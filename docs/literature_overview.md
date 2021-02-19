
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

### Data set size

How many training data samples should be used?

-   as many as possible: ([Millard and Richardson
    2015](#ref-millardImportanceTrainingData2015))
-   not sensitive to reduction: ([Rodriguez-Galiano et al.
    2012](#ref-rodriguez-galianoAssessmentEffectivenessRandom2012))

How to distribute the training data among classes?

-   area proportional: ([Colditz
    2015](#ref-colditzEvaluationDifferentTraining2015); [Freeman
    2012](#ref-freemanEvaluatingEffectivenessDownsampling2012); [Millard
    and Richardson 2015](#ref-millardImportanceTrainingData2015))
-   balanced is good but fine imbalance (best/worst class) is better
    ([Mellor 2015](#ref-mellorExploringIssuesTraining2015))

If data has to be resampled what method should be used?

-   upsampling: ([Japkowicz and Stephen
    2002](#ref-japkowiczClassImbalanceProblem2002); [McCarthy, Zabar,
    and Weiss 2005](#ref-mccarthyDoesCostsensitiveLearning2005))

Which other methods are suggested to consider class imbalance?

-   threshold optimization: ([Freeman
    2012](#ref-freemanEvaluatingEffectivenessDownsampling2012))
-   balanced random forest: ([C. Chen
    2004](#ref-chenUsingRandomForest2004))
-   weighted random forest: ([C. Chen
    2004](#ref-chenUsingRandomForest2004))
-   cost sensitive learning: ([Japkowicz and Stephen
    2002](#ref-japkowiczClassImbalanceProblem2002); [McCarthy, Zabar,
    and Weiss 2005](#ref-mccarthyDoesCostsensitiveLearning2005))

Is it better to use homogeneous or heterogeneous data within classes?

-   heterogeneous: ([Colditz
    2015](#ref-colditzEvaluationDifferentTraining2015))

Is it better to use more or less predictor variables?

-   as few as necessary: ([Millard and Richardson
    2015](#ref-millardImportanceTrainingData2015))

## Key Statements

[Rodriguez-Galiano et
al.](#ref-rodriguez-galianoAssessmentEffectivenessRandom2012)
([2012](#ref-rodriguez-galianoAssessmentEffectivenessRandom2012))

-   “RF has low sensitivity to the training set size reduction”
-   “RF is relatively little noise sensitive”
-   used equal number of samples per class
-   as RF generates unbiased estimation of error (oob) a validation data
    set is unnecessary

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
