# Processing, Regressions, and Web Deployment of Bioinformatic Data

## Overview

This project involves the use of Python to clean, preprocess, build machine learning models, and eventually deploy that ML model using a web app.
This repository includes five notebooks, each containing one project phase, and app.py, which contains the web app code.

Primary Libraries: pandas, numpy, sklearn, matplotlib, seaborn, streamlit

## Phase 1: Data Collection, Preprocessing

First, we download the ChEMBL webresource client. ChEMBL is a manually curated database of bioactive molecules with drug-like properties; the database brings together chemical, bioactivity and genomic data, which we can now access through our notebook. We search for 'coronavirus' and store our results in a dataframe. We select "SARS coronavirus 3C-like proteinase" Single Protein ChEMBL ID 3927 to study for this project. After pulling this protein's data and storing it in a data frame, we drop entries with absent or duplicate values. Finally, we assign compounds a bioactivity value based off their IC50 value, an measure of how much drug is required to inhibit the protein by half.

## Phase 2: Data Analysis

## Phase 3: Descriptor Calculation

## Phase 4: Building, Comparing ML Models

## Phase 5: Deployment of Model
