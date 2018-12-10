# E-commerce recommendation system for GCP
Recommender System (TIETS43) Project work

## Installation
Following steps are needed only first time. If you have done the installation before jump to step **Usage**

### Install Miniconda 2:

    bash Miniconda2-latest-Linux-x86_64.sh

### Install the Python packages and TensorFlow:

    cd recommendation-system
    conda create -n tfrec
    conda install -n tfrec --file conda.txt
    source activate tfrec
    pip install -r requirements.txt
    pip install tensorflow==1.4.1

## Usage

### Initialization
If you have performed the **Installation** steps before then you only need to do the following steps:

    cd recommendation-system
    source activate tfrec

### Assing the Cloud Storage Bucket
App needs a Cloud Storage Bucket to deploy the model and to load the data.

Assing the following environment variable:

### Training the model

### Deploying the model

# References
Repository is forked from [Google's Tutorial](https://github.com/GoogleCloudPlatform/tensorflow-recommendation-wals) and 
code is modified to fit our needs.

# Credits
Toni Linnusmäki, Jenni Laukkanen and Joonas Kaartoluoma

