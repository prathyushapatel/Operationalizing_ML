***
# Operationalizing Machine Learning
***
This project is part of the Udacity Microsoft Azure ML Nanodegree program, which shows the code, screenshots, results, and full video demonstration of operationalizing machine learning using Azure ML Studio, Azure SDK, and Swagger.
***
# Project Overview
***
This project first begins with uploading the dataset which is about bank showcasing which it contains a few subtleties of the clients like credit is taken or not indicated as "advance" section and different subtleties like age, work title, conjugal status. The objective is to anticipate 'y' section utilizing different highlights given in the dataset we initially accomplish it utilizing AutoML which does a lot of preparing himself. I have used the AutoML function on Azure to generate the best model using a metric and ending criteria. The model is then deployed using Azure ACI to generate a swagger URI and REST API endpoint. Using Azure and its workspace, this project looks at creating a cloud-based machine learning model, from deployment to consumption and finally publication. Commands for the deployment, processing, and endpoint results are executed using Git Bash.
The Architecture of the project followed by step-by-step screenshots with a description of the working project mentioned below.
***

## Architectural Diagram
***
![Architecture Design](https://github.com/prathyushapatel/Operationalizing_ML/blob/main/Images/Project-Architecture.png)
1. AutoML Run: In this we create a Automated ML model by selecting the Bank Marking dataset from Registered Dataset and create a compute cluster (Standard_DS12_v2) and 1 as maximum number of nodes. We will be run the Automated run as a Classification and setting the Exit Criterion to 1 hour and the Concurrency to 1.
2. Select the Best Model & Deploy: On completion of AutoML run, we will be selecting the best model and we will be deploying it and while deploying we will be using "Azure Container Instances" (ACI) and we will also enable "Authentication".
3. Enabling Application Insights: In order to Enable Application Insights we will be downloading config.json file by going into subscription details and then we need to change the deployed model name in logs.py file and set enable_application_insights to True. And run logs.py file this will enable application insights logs for deployed model.
4. Setup Swagger & interact with it: Then we will be using the swagger documentation endpoint provided in Azure for deployed model and copy content of it and create a swagger.json file and set the swagger documentation for your project by running its bash script and serve.py to serve the content of your projects swagger.json file.
5. Consume Model Endpoint: Next is we will consuming the deployed model we will do this the adding the uri and key in endpoints.py file by copying from deployed model's consume section.
6. Create pipeline via notebook: We will be uploading the notebook provided in the starter files and then modifying at required cells and then will be running the cells which will create the pipeline.
7. Consume created Pipeline: Once the pipeline is created we will runs the cells provided in notebook itself to consume the pipeline.
8. Publish Pipeline: Once pipeline is consumed we will then run the cells provided in notebook to publish the pipeline.<br /><br /><br />
***
# Key Steps
## 1. Registered Datasets

From the following list of Registered Dataset we selected the Bank Marketing dataset.<br /><br />

![Registered Datasets](https://github.com/prathyushapatel/Operationalizing_ML/blob/main/Images/1.png)<br /><br />

## 2. Create Automated ML Experiment

In this step, we created an Automated ML model using a registered bank marketing dataset, and then created a compute cluster, and started the Automated ML run which created Runs for various models using different algorithms.<br /><br />
Second one - Run 1
![Automated ML Experiment](https://github.com/prathyushapatel/Operationalizing_ML/blob/main/Images/2.png)<br /><br />

## 3. Best Run Model

Out of different algorithms tried in the Automated ML run the Best Model was ***Voting Ensemble*** which gave the accuracy of ***92.049%***. Then we deployed this model.<br /><br />

![Best Run Model](https://github.com/prathyushapatel/Operationalizing_ML/blob/main/Images/3.png)<br /><br />

## 4. Enable Application Insights

In order to enable logging downloaded the configuration from Azure workspace and added to project and the made changes in logs.py file to enable application insights. <br /><br />

![Updates in logs.py](https://github.com/prathyushapatel/Operationalizing_ML/blob/main/Images/4.png)<br /><br />

We enabled Application Insights by making its value *True* in logs.py and ran logs.py file and enabled logging successfully.<br /><br />

![Application Insights Enabled](https://github.com/prathyushapatel/Operationalizing_ML/blob/main/Images/5.png)<br /><br />

## 5. Configuring Swagger Docs

Then we configured swagger docs by installing swagger by changing the port number in bash script file and running it.<br /><br />

![Swagger default docs](https://github.com/prathyushapatel/Operationalizing_ML/blob/main/Images/6.png)<br /><br />

Then we started the server by running serve.py file inorder to serve your project's swagger.json file.<br /><br />

![Swagger project docs](https://github.com/prathyushapatel/Operationalizing_ML/blob/main/Images/7.png)<br /><br />

## 6. Consuming Endpoints
Then we added endpoint uri and key from deployed model *consume* section, in endpoints.py file and running the file.<br /><br />

![Modifying Endpoints.py](https://github.com/prathyushapatel/Operationalizing_ML/blob/main/Images/8.png)<br /><br />

![Consuming Endpoints](https://github.com/prathyushapatel/Operationalizing_ML/blob/main/Images/9.png)<br /><br />

## 7. Pipeline Created, Deployed and Consumed

For this section we uploaded the sample notebook provided and made required changes in cell and ran the notebook. This created pipeline and then we deployed the pipeline which generated the endpoint for the pipeline which we consumed it.<br /><br />

![Pipeline created](https://github.com/prathyushapatel/Operationalizing_ML/blob/main/Images/14.png)<br /><br />

![Pipeline endpoint created](https://github.com/prathyushapatel/Operationalizing_ML/blob/main/Images/15.png)<br /><br />

![Pipeline endpoind published successfully](https://github.com/prathyushapatel/Operationalizing_ML/blob/main/Images/5.png)<br /><br />

![Pipeline endpoint overview](https://github.com/prathyushapatel/Operationalizing_ML/blob/main/Images/17.png)<br /><br />

![Pipeline run details widget](https://github.com/prathyushapatel/Operationalizing_ML/blob/main/Images/18.png)<br /><br />

![Pipeline endpoint run details widget](https://github.com/prathyushapatel/Operationalizing_ML/blob/main/Images/19.png)<br /><br />



## Screen Recording
***
:movie_camera: [Click here for the Screencast](https://drive.google.com/file/d/1LbwWOPtVBOIP99pqyXy4c5bJ1FbYGkOg/view)
***

# Standout Suggestions
- Resolving data imbalance issue in the dataset can prevent the bais and could improve the model prediction even more.
- Trying out deep learning (neural net) option when training the model, this could improve the accuracy.
- Try setting the featurization parameter of the AutoMLConfig class to 'auto', meaning that the featurization step should be done automatically.

