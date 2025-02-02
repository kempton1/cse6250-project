# CSE 6250 Project Team 34

The notebook can be run on Google Colab without any arguments.

# Introduction
The aim of the paper "MIMIC-Extract: A Data Extraction, Preprocessing and Representation Pipeline for MIMIC-III" (S. Wang, M. B. A. McDermott, G. Chauhan, M. Ghassemi, M. C. Hughes, and T. Naumann, 2020) [1] is to provide a standardized processing framework to transform data from MIMIC-III database [2] into data structures that can be directly used in clinically-relevant prediction models.

Benefits of the standardized extraction pipeline are:

transform raw data into static and time-series dataframes that researchers can direclty use and focus on answering their research questions instead of spending efforts on data extraction.
solve the problem of often-noisy clinical data by unit standardization, outlier handling and clinical aggregation of semantically similar features
flexibility in cohort and variable selection with simply changing the variables instead of modifying the source code, thus making it easier to run repeated experiments with ease.

# Methodology
## Data
Data Source: MIMIC-III Clinical Database, Version: 1.4 [2] and MIMIC-III derived tables (concepts) [3]

Data Statistics: MIMIC-III dataset consists of 26 tables containing EHR of 53,423 patients admitted to critical care units at a Boston-area hospital from 2001– 2012.

We are using cloud version of the dataset hosted at Google Cloud Platform [4].

For this demo notebook, we are executing the extraction pipeline using a pre-filtered, scaled-down version of the dataset comprising records pertaining to 100 patients, also hosted on Google Cloud Platform (GCP). However, we have also executed the pipeline on the complete MIMIC-III dataset, encompassing all available records but due to time limitation, we will only load and present the already produced full results. Full dataset can be easily used by changing the variable dataset_id.

## Model
The extraction framework has been built as 3 main pipelines:

patients: static demographic and clinical data of the selected patient cohort

vital labs: hourly-aggregated and cleaned time series vitals lab results

interventions: hourly binary indicators of device treatments and drug treatments over time.

