# E-commerce recommendation system in Google Cloud Platform
Recommender Systems [TIETS43](https://coursepages.uta.fi/tiets43/) Project work.

Training and deploying this recommendation system requires the following applications from Google Cloud Platform.
* [Compute Engine](https://cloud.google.com/compute/)
* [Cloud Storage](https://cloud.google.com/storage/)
* [App Engine](https://cloud.google.com/appengine/)

Your project must have [Billing](https://cloud.google.com/billing/docs/) all the necessary [APIs](https://cloud.google.com/apis/) mentioned above enabled to run the recommender system in GCP.


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

    export BUCKET=gs://recserve_$(gcloud config get-value project 2> /dev/null)

### Training the model

Go to the wals_ml_engine folder and traing the model. 

    cd wals_ml_engine
    ./mltrain.sh local $BUCKET/data/recommendation_events.csv \
    --use-optimized --output-dir ${BUCKET} 

1. Parameter in ./mltrain.sh defines where you want to train the model (here it's set to local). 
2. Parameter is the path where the training data is located.
3. Parameter uses already hypertuned parameters for the training.
4. Paramerter defines the output directory where the model is saved. 


### Deploying the model

Go to the scripts folder and prepare the app for deployment.

    ./prepare_deploy_app.sh


Every time you want to deploy a new version to the Google App Engine.

    gcloud -q app deploy ../app/app_template.yaml_deploy.yaml


# References
Repository is forked from [Google's Tutorial](https://github.com/GoogleCloudPlatform/tensorflow-recommendation-wals) and 
code is modified to fit our needs.

# Credits
Toni Linnusmäki, Jenni Laukkanen and Joonas Kaartoluoma

