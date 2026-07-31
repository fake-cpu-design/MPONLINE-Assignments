# End-to-End Render Deployment Project

## Project Overview
This project demonstrates how to train a Machine Learning model, wrap it in a FastAPI web application, and deploy it to the cloud using Render. The API exposes endpoints to check the server status and to make predictions based on incoming JSON payloads.

## Architecture
* **Machine Learning:** Scikit-Learn (RandomForestClassifier trained on the Iris dataset).
* **Web Framework:** FastAPI.
* **Server:** Uvicorn.
* **Deployment Platform:** Render (Platform as a Service).
* **Infrastructure as Code:** `render.yaml` blueprint.

## Environment
This project generates the necessary deployment files within **Google Colab**. Once generated, the files are downloaded locally to be pushed to a Git repository for continuous deployment.

## Prerequisites
* A GitHub account.
* A Render.com account linked to your GitHub.

## Workflow Pipeline
1. **Model Training:** Trains a basic Random Forest model and serializes it as `model.pkl`.
2. **API Generation:** Uses Colab's `%%writefile` magic command to create `main.py`, which loads the `.pkl` file and sets up a `/predict` POST endpoint.
3. **Dependency Management:** Generates a `requirements.txt` file listing all required Python packages for the Render environment.
4. **Render Blueprint:** Creates a `render.yaml` file that tells Render exactly how to build and start the web service.
5. **Export:** Downloads the generated files (`main.py`, `model.pkl`, `requirements.txt`, `render.yaml`) to your local machine.

## Deployment Instructions
1. Run all cells in the Google Colab notebook to generate and download the project files.
2. Create a new repository on GitHub and upload the downloaded files (`main.py`, `model.pkl`, `requirements.txt`, `render.yaml`).
3. Log in to [Render](https://render.com/).
4. Click **New** > **Blueprint**.
5. Connect your GitHub repository.
6. Render will automatically read the `render.yaml` file, build the environment, and deploy the FastAPI application.