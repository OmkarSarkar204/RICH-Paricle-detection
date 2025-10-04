# RICH Particle Detection

This project explores how machine learning can identify subatomic particles using simulated data from CERN’s LHCb experiment.
The goal is to classify electrons, muons, protons, kaons, and pions from their detector signatures.

## Overview

Each particle interacts with the detector in a unique way.
By studying signals such as momentum, energy deposits, and Cherenkov radiation, the model learns to recognize patterns that distinguish one particle type from another.

## Dataset

The dataset includes several detector readings for each recorded particle track.

## Feature	Description
TrackP	Total momentum of the particle
EcalE, HcalE	Energy deposited in electromagnetic and hadronic calorimeters
RICH_DLL*	Log-likelihood difference scores from the RICH detector
BremDLLbeElectron	Score related to electron braking radiation
ParticleType	True particle label (electron, muon, pion, kaon, proton)
Model

Objective: Multi-class classification
Algorithm: Gradient Boosted Decision Trees (XGBoost)
Inputs: Detector signal features
Output: Predicted particle type

The model uses these physical properties to learn how to separate different particle types. It captures real physical patterns rather than arbitrary correlations.

## Visualizations
1. Momentum Distribution

Shows how each particle type occupies a different range of total momentum.

<img width="1017" height="717" alt="parti_momentum" src="https://github.com/user-attachments/assets/796d960b-ca67-4633-9848-140a00f7f246" />


2. Calorimeter Energy Map

Illustrates how electrons deposit most of their energy in the electromagnetic calorimeter, while heavier hadrons deposit energy deeper into the hadronic layer.

<img width="984" height="784" alt="Calorimeters" src="https://github.com/user-attachments/assets/e0ff9a31-b5cc-4b41-a7a1-8efaf7b9125b" />


3. RICH Detector Comparison

Displays how kaons and protons overlap in RICH detector outputs, explaining why they are difficult to distinguish.


<img width="984" height="784" alt="new_kaons_protons" src="https://github.com/user-attachments/assets/f59a748b-dcdd-44ad-a3e0-3da1588c4756" />


4. Anomaly Detection

Shows particles that the model found most confusing. These may represent rare or noisy detector events.


<img width="944" height="968" alt="Anomalies" src="https://github.com/user-attachments/assets/5385baf3-17b8-4b20-a63f-1e07c5686a94" />


# Results

* Metric	Value
Accuracy:	77.41%
* Key Features: Momentum, EcalE, HcalE, RICH_DLLbeKaon, RICH_DLLbeProton
* Hardest Classes: Kaon vs Proton

## Insights

The model easily learned to separate electromagnetic particles (electrons and muons) from hadronic particles (protons, kaons, pions).

The main difficulty came from distinguishing kaons and protons, which are physically similar in both mass and behavior.

The anomalies revealed genuine detector ambiguities rather than model errors.
