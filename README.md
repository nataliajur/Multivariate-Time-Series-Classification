# Multivariate-Time-Series-Classification

As a final step in pursuing my degree in Applied Data Science, I conducted one semester project (30 HEC) at the automotive company Volvo Cars. 

## Overview

Topic : **Master Thesis: City Safety Event Detection using Machine Learning at Volvo Cars**
Year  : 2019

| PROPERTY        | DESCRIPTION| 
| ------------- |:-------------:| 
| Goal (DS topic)     | Binary classification of a multivariate time series data | 
| ML algorithm      | Supervised and semi-supervised, k-nn for time series, Gradient Boosting Classifier   | 
| Data | Collection of car data sensor signals. One event consists of 316 signals, each lasting 8 seconds. Data size = (n, x, t) = (152, 316, 40), where: n – number of events, x – number of signals, t – length of a time series singal (5 measurements per second) Additionally, there were more than thousand unlabelled events.     |
| Label | Event classification: true or false |
| Issues solved | Small dataset, large data dimensions |

## Background

### City safety – sensor data fusion
City Safety is a Volvo’s active safety system that consists of three activations step. If a host vehicle approaches another object and there exists a posibility of collision then the City Safety system comes in.

Firstly it sends a Collision Warning to a host vehicle driver. If he or she does not react then the car auto-brakes. Sensors collect data from the host vehicle.

Each event as such, when Auto-Brake is activated collects data from sensors 4 seconds before the Auto-Brake activation and 4 seconds after the Auto-Brake activation. Measurements are done 5 times per seconds, so each signal is measured 40 times in total, resulting in a length of a time series equalled to 40.

### Goal of the analysis – business application

Having an **algorithm that can determine quickly if the Auto-Brake activation is correct or incorrect** can help to improve the Auto-Braking system in the future. Possible roots that cause incorrections can be then clustered and scrutinized. But – to do so, the classification algorithm with a high accuracy rate is need to be applied.

### Signal Visualisation

An example of signals measured and a visualisation of one signal.

## Methods algorithms: two Machine Learning models

Two ML models were prepared on labelled data:

1. Baseline model
2. Pseudo-labelling model

I performed a modified cross validation train-test data split. Due to a small data sample, 100 train-test sets were created. Split ratio applied: 70-30.

### Baseline model

Baseline model was applied in 4 variants:
– all signals with no pre-processing,
– all signals with pre-processing,
– 11 chosen signals with no pre-processing,
– 11 chosen signals with pre-processing.

An example of pre-processing:

An algorithm applied for classification: k-nn classification for time series data. I found a great library tslearn that can be applied for a multivariate time series data.

K-NN algoriths takes 3 parameters as input: distance metrics, number of k nearest neighbours and weigth of the distance. I played with different settings to determine which one will be the best and the more robust.

Some results:

Details of this algorithm can be found in the thesis uploaded in the bottom of this page.

Each boxplot is a graphical representation of the k-nn testing score on each of 100 random splits.

### Pseudo-labelling model

This model consists of an extensive pre-processing, which aim at reducting dimensionality of data from 3 (sequential) to 2 (non-sequential). Transforming a time series data to its descriptive features, creates hundreds of one-dimension features.

#### Pre-processing

1. Feature engineering
2. Filtering

## Evaluation

