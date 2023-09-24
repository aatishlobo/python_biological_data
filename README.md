# Processing, Regressions, and Web Deployment of Bioinformatic Data

## Overview

This project involves the use of Python to clean, preprocess, build machine learning models, and eventually deploy that ML model using a web app.
This repository includes four notebooks, each containing one project phase, and app.py, which contains the web app code.

Primary Libraries: pandas, numpy, sklearn, matplotlib, seaborn, streamlit

## Phase 1: Data Collection, Preprocessing

First, we download the ChEMBL webresource client. ChEMBL is a manually curated database of bioactive molecules with drug-like properties; the database brings together chemical, bioactivity and genomic data, which we can now access through our notebook. We search for 'coronavirus' and store our results in a data frame. We select "SARS coronavirus 3C-like proteinase" Single Protein ChEMBL ID 3927 to study for this project. After pulling this protein's data and storing it in a data frame, we drop entries with absent or duplicate values. Finally, we assign compounds a bioactivity value based off their IC50 value, an measure of how much drug is required to inhibit the protein by half.

## Phase 2: Data Analysis

After loading the data frame with the cleaned data from the last phase, we extract the 'canonical smiles' data into a separate datframe. Canonical smiles are a form of notation that allows us to see the atoms and bonds present in a molecule. Next, we define a function to calculate the Lipinski descriptors of the molecules in our data frame, yielding us data like the molecular weight and Hydrogen donors and acceptors of those molecules. This new data along with the canonical smiles data we used to calculate the descriptors is concatenated to the original data frame. Next, we define a function to convert our IC50 values to pIC50 values, which is the -log10 of the molecular molar weight represented by the 'standard_value' column. We do this because the pIC50 values are less variable and easier to work with because of the log function used in their calculation. We concatenate these values to the data frame and remove the standard_value column along with any entries marked as 'intermediate' for their bioactivity. We are now left with a final data frame for this phase. Finally, we run the the Mann-Whitney test for statistical significance to verify the usability of our data.

## Phase 3: Descriptor Calculation

In this intermediary phase, we run the command conatained in padel.sh, which calculates the fingerprint descriptors for the molecules contained in the final dataframe from last section and stores it in descriptors_output.csv. We create a new data frame containing the descriptors and save it to a csv.

## Phase 4: Building, Comparing ML Models

We split the data from the last phase into a training and test set and use the lazyregressor function from the lazypredict package to run multiple ML models on the data. After plotting the R-squared values and the RMSE values, we observe the K Neighbors Regression has the best performance on the test data, evident because it has the highest R-squared and the lowest RMSE. We then build a K Neighbors Regressor, testing values for the number of neighbors from 1 to 20. n=6 has the highest accuracy on the test data, so we create a model with n=6, fit it on the data and use the pickle package to store it in model_pkl.

## Phase 5: Deployment of Model

The web app source code is contained in app.py.
