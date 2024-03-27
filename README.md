# FastAPI Hello world API to test cloud deployments quickly

## Description
This project is a RESTful API built with Python and FastAPI.

## Installation
1. Clone the repository
 ```bash
   git clone https://github.com/suvarnakd/fast-api-hw.git
```
2. Create a Python 3.9 virtual environment:
   ```bash
   python3.9 -m venv venv
3. Activate the env
   ```bash
   source venv/bin/activate
4. Install requirements
   ```bash
   pip install -r requirements.txt
## Usage
Run the API with uvicorn:
   ```bash
   uvicorn app.main:app --reload
   ```

## GCP Deployment with app engine

1. Any AI code implemented with fast-api can be deployed on gcp with app engine deployment. 
2. The gcloud app command group lets you deploy and manage your Google App Engine apps.   
3. Steps:

- Create/seclect the gcp project  https://console.cloud.google.com/
- Select APIs & Services
- Select the "Activate cloud shell" `>-`
- Make sure that you have the correct current project 
```bash 
gcloud config list project
```
- Clone the repository
```bash
   git clone https://github.com/suvarnakd/fast-api-hw.git
   cd fast-api-hw
 ```  
- You may directly deploy your app, or you may check if everything works by manually trying to run the api on VM provided with console
```bash
   virtualenv env
   source env/bin/activate
   pip install -r requirements.txt
   gunicorn -k uvicorn.workers.UvicornWorker app.main:app
```
If you could run this successfully, your requirements.txt has all required libraries to host fastapi code.
- you may stop the running process and check the app.yaml file
```bash
   cat app.yaml
```
- To see the apps already deployed on app engine use following-
```bash
   gcloud app browse
```
- To deploy our  current hello world api app `fast-api-hw`
``` bash
   gcloud app deploy
```
- to see tha log of deployment
``` bash
   gcloud app logs tail -s default
```
- You may see a url if the app is deployed correctly
``` bash
    gcloud app browse
```
- Visit the url for example https://auto-annotation-demo.as.r.appspot.com to access the deployed API.

- If there are any changes in the repo, simply pull the changes and reploy the app with
```bash
   gcloud app deploy

