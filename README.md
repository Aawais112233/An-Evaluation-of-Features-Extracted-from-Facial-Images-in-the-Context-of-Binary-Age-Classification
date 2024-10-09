# An-Evaluation-of-Features-Extracted-from-Facial-Images-in-the-Context-of-Binary-Age-Classification


**Abstract**
Age verification via facial images is used to enhance security, ensure online child safety, and
manage access control with many approaches using classification models. However, many existing
classification approaches face generalisation challenges due to homogenous racial nature of datasets.
Moreover, many approaches fail to explicitly address the predictive potential of extracted facial
features. To address the lack of racial diversity we selected representative samples from four different
benchmark datasets: UTK-Face, Fg-Net, Morph and All-Age-Faces. Subsequently, we examined the
predictive potential of local, global and hybrid sets of facial features. We extracted local features
using two types of Local Binary Pattern (LBP)—one based on the number of uniform patterns
resulting in 16384 features and one with 10 features based on fixed length histogram. To extract
global features, we used a geometric ratio model with 12 features. Finally, two hybrid feature
sets were generated using hybrid partial active appearance model(HPAAM) with 10136 features
and a model combining the 10 bin LBP features and the 12 geometric ratios. We then assessed
feature predictiveness for larger feature sets via Chi-Square, Anova and Information Gain. Finally,
we conducted classification experiments with and without data K-Means balancing to evaluate the
accuracy of the models generated based on various feature sets. The results show that histogrambased LBP and geometric ratios models consistently outperform the uniform LBP and HPAAM,
even when balancing and feature selection were employed: uniform LBP and hybrid partial AAM
lead to average accuracies of 70.48% and 72.68%, respectively. Conversely, the histogram-based LBP
and facial ratio models lead to average accuracies of 78.5% and 76.5%, respectively, reaching 80% on
balanced data. We observed further improvements in accuracy, precision and recall when histogrambased LBP and facial ratios features were combined reaching 83% accuracy. These findings indicate
that using large subsets of features does not lead to better performance due to irrelevant features
that introduce noise. A more effective approach is to use conservative feature extraction techniques
with smaller number of features, which not only improves model accuracy and reduces the need to
apply feature selection, but also assumes a reduced computational overhead.


**1 Introduction**

The use of computers, global connectivity and accessibility has opened the path for cybercrimes [1]. The increased online connectivity has made it easier for the preparators to exploit children via Children Sexual Exploitation Materials (CSEM) [2]. As a result, age estimation is becoming increasingly important for access control to help re- strict access to CSME. One approach to achieving this is by utilizing facial attributes [3]. 

Much of the existing research on facial age estimation employ classification approaches that rely on publicly available datasets heavily skewed towards specific races, predominantly white or black and classification models trained on such data can produce biased outcomes [4]. Additionally, existing approaches employ a variety of feature extraction techniques that can produce large feature sets, however, they do not explicitly assess the predictive potential of the extracted features, thus overlooking the opportunity to eliminate noise and decrease computational overhead. 

To address the lack of racial diversity, in this paper we selected representative samples from four benchmark datasets. From these combined samples we then selected high-quality images of neutral faces without background by applying several filtering techniques for face detection, cropping, blur detection, and facial expression detection. To investigate feature predictiveness, we extracted local features using two types of LBP – one with full length features and the second with fixed length histogram bins. Additionally, we extracted global features using geometrical facial ratios, and hybrid features using a hybrid partial AAM model and a model where we combined the 10-binLBP features   and the 12 geometric ratios. We then conducted classification experiments with full feature set and with reduced feature subsets based on Chi-Square, Anova, and Information Gain. We evaluated these feature sets through classification model performance using accuracy, precision and recall on both imbalanced and balanced datasets.


**Our contributions are as follows: \\**
We combined several benchmark datasets, i.e., UTK-Face, Morph, FG-Net, and All-Age- Faces, to form a single dataset and applied techniques including face detection, cropping, image enhancement, and emotion detection to ensure the selection of good quality neutral face images without background. 

 We conducted experiments to compare large and small features sets and results indicate conservative feature extraction techniques that yield smaller number of features improve model accuracy and reduce the need to apply feature selection.    

**2 Methodology

**
2.1 Data Sampling, Filtering
and Labelling****
In this paper we have utilized four different bench- mark datasets: UTK-Face, Fg-Net,
Morph and All-age-faces [4][25]. The UTK-Face
consists of more than 20000 images of people between 0-116 years in unconstrained conditions;
races present in this dataset include Asian, Black,
Indian, and others. The Morph dataset consists
of 55134 images of people in a controlled environment of ages between 16 to 77 years across
five racial groups (African or Black, European
or White, Asian, Hispanic and others. Fg-Net
dataset consists of 1002 images of people aged
between 0 - 69 years; because no race information is included, we manually checked each image
2
and assigned races as follows: B for Black, W for
White, I for Indian and A for Asian. The final
benchmark dataset we included is All-Age-Faces
that consists of Asian; it has 13322 face images
distributed across ages from 2 to 80.
We then applied several filtering techniques:
Viola-Jones [10] and cropping to detect faces
and eliminate background outside the detection
bounding boxes; facial expression detection [11]
to select facial images with neutral expressions;
and blur detection using Laplacian Variance [12]
with a threshold of 20 to select clear images only.
The final dataset consists of 12213 images, 225
images from Fg-Net, 5000 images from All- AgeFaces, 1112 images from UTK-Face and 5877 images from Morph. Finally, to conduct classification experiments, the ages are binarized by mapping those younger than 18 to class 1 and those
18 or older to class 0. Figures 1,2,3 and 4 show
the distribution of images of the final dataset in
terms of age, gender, race and binary age groups.
