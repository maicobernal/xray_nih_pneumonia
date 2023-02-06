# Pneumonia Detection from NIH Chest X-Rays

## Execution order for scripts:
1. EDA.ipynb
2. MODEL.ipynb
3. INFERENCE.ipynb

The full dataset can be downloaded from [Kaggle datasets](https://www.kaggle.com/datasets/nih-chest-xrays/data) with the following script from bash:

```
kaggle datasets download -d nih-chest-xrays/data
```

The model weights and arquitecture is zipped and splitted. 
To unzip it execute in bash: 
```
zip -s 0 v11_my_model_xray_udacity_Pneumonia_final.zip --out model.zip
unzip model.zip
```

### First data insights

## Overview

A convolutional neural network was trained for binary classification of pneumonia from chest x-rays as part of Udacity project for AI for Healthcare nanodegree program using the NIH chest x-ray dataset.

The dataset contains 112K chest x-ray images with disease labels acquired from 30.000 unique patients.

The goal was to create a CNN system capable of make predictions for the presence or abscense of pneumonia for acting as a suplementary tool for the radiologist with human-eye level of accuracy.

The main limitation for reaching this objective is on the data labeling and specific issues regarding lung infection biology:
1) Labeling for each pathology was created by the NIH team with NLP tools of radiology reports, reporting a accuracy of ~90% for labeling. 
2) Chest x-rays represent a picture of a continuous biological process (as is a lower lung infection like pneumonia). This makes the accuracy of a radiologist limited depending on certains conditions which may lead to a non-radiological expression of this pathologhy (like inmunosupression), leading to a missdiagnosis. 
3) The dataset also includes potential diagnosis that can lead to a similar diagnosis depending on the clinical setting and current medical guidelines: it is not rarely to make a clinical diagnosis of pneumonia with the labeling of 'consolidation' or 'infiltrate' in the radiologist report if the patient has clinical high probability of pneumonia (fever, cough, physical examination with positive findings).

It is documented a previous F1 score for CheXNet of 0.435 and a averaged radiologist score from [CheXNet original publication](https://arxiv.org/pdf/1711.05225.pdf) is 0.387 *CI95% (0.330, 0.442).* 

All these limitations, specially in data labeling, translate directly to the perfomance of the algorithm training. 


### First data insights

#### Data glossary
- 'id': unique patient id
- labels: Disease types (can be concomitant)
- 'followup': the number of follow-up chest x-ray scan. the first scan has 'nr_follow_up'==0, the second ==1, and so on. The time between two scans is not given.
- 'age': patient age in years
- sex: binary: 'm', 'f'
- 'position':
    - PA: Posteroanterior (PA) view: the x-ray source is positioned in the back of the patient, xray goes from posterior to anterior. 
    Requires patient to be able to standup and hold breath. Not usually possible for critical patients, or patients with reduced mobility. 
    - AP: Anteroposterior chest view is performed with the x-ray tube anteriorly. Usually done on bed for critically ill patients.
- 'width': original image widht
- 'height': original image height
- 'x': Physical distance in the patient between the centers of two 2D pixels (2 adjacent columns, or horizontal spacing) in mm in x direction, also called column spacing
- 'y': Physical distance in the patient between the center of each pixel (2 adjacent rows, or vertical spacing) in mm in y direction, also called row spacing
- 'labels*': label of all deseases/findings.
    - atelectasis
    - cardiomegaly
    - consolidation
    - edema
    - effusion
    - emphysema
    - fibrosis
    - hernia
    - infiltration
    - mass
    - no_finding
    - nodule
    - pleural_thickening
    - pneumonia
    - pneumothorax

#### To be continued.