i # Breast Cancer Prediction API

This project demonstrates a complete machine learning workflow: training a model on the breast cancer dataset, deploying it as a REST API using Flask, exposing the API publicly via ngrok, and testing the API with sample data.

## Notebooks Overview

- **model_training.ipynb**: Trains a Support Vector Machine (SVM) model using scikit-learn on the breast cancer dataset. The model pipeline includes data scaling, PCA for dimensionality reduction, and classification. The trained model is saved as `breast_cancer_model.pkl`.

- **get_url.ipynb**: Sets up ngrok to create a public tunnel to the local Flask API running on port 5000. This allows external access to the API without port forwarding.

- **model_deployment.ipynb**: Deploys the trained model as a Flask web application. It loads the saved model and provides a `/predict` endpoint that accepts JSON input with 30 features and returns a prediction of "benign" or "malignant".

- **api_test.ipynb**: Tests the deployed API by sending a POST request to the `/predict` endpoint with sample data. It prints the API response or any errors.

## Prerequisites

- Python 3.x
- Jupyter Notebook or JupyterLab
- Ngrok account (for public tunneling)

## Installation

Install the required Python libraries:

```bash
pip install scikit-learn flask numpy joblib pyngrok requests
```

## Usage

1. **Train the Model**:
   - Open and run `model_training.ipynb` in Jupyter.
   - This will train the model and save it as `breast_cancer_model.pkl` in the current directory.

2. **Set Up Ngrok**:
   - Open and run `get_url.ipynb` in Jupyter.
   - Note the public URL printed (e.g., `https://xxxxx.ngrok-free.app/`).
   - Update the `ngrok_url` variable in `api_test.ipynb` with this URL.

3. **Deploy the API**:
   - Open `model_deployment.ipynb` in Jupyter.
   - Run the notebook to start the Flask server on `http://0.0.0.0:5000`.
   - The cell will keep running; do not stop it while testing.

4. **Test the API**:
   - In a new Jupyter instance or terminal,<create_file>
<path>../Downloads/README.md</path>
<content>
# Breast Cancer Prediction API

Hey there! This is a fun little project I put together to show how you can go from training a machine learning model to having a live API that predicts whether a breast cancer diagnosis is benign or malignant. It's all done with Jupyter notebooks, so it's easy to follow along and tweak as you like.

## What's in Here?

I've got four notebooks that walk you through the whole process:

- **model_training.ipynb**: This one trains a Support Vector Machine (SVM) model using scikit-learn's breast cancer dataset. It uses a pipeline to scale the data, reduce dimensions with PCA, and then classify. At the end, it saves the model as `breast_cancer_model.pkl` so we can use it later.

- **model_deployment.ipynb**: Here, we load up that saved model and turn it into a simple Flask API. There's a `/predict` endpoint that takes in some features as JSON and spits back a prediction.

- **get_url.ipynb**: This sets up ngrok to give your local API a public URL. Super handy if you want to share it or test from another device without messing with port forwarding.

- **api_test.ipynb**: Finally, this tests the API by sending a sample request and showing the result. It's a quick way to make sure everything's working.

## What You Need

- Python 3.x (nothing fancy)
- Jupyter Notebook (comes with Anaconda if you use that)
- An ngrok account (free tier works fine for testing)

## Getting Started

First, grab the libraries you'll need. Run this in your terminal or a Jupyter cell:

```bash
pip install scikit-learn flask numpy joblib pyngrok requests pandas
```

Oh, and sign up for ngrok if you haven't already. You'll need to put your authtoken in `get_url.ipynb` where it says to replace the placeholder.

## How to Run It

Let's get this thing running step by step:

1. **Train the Model**: Fire up `model_training.ipynb` and run it. It'll train on the breast cancer data and save the model file right there in the folder.

2. **Start the API**: Open `model_deployment.ipynb` and run it. This kicks off a Flask server on your local machine. Keep that notebook running – it's serving the API.

3. **Make It Public**: In another tab or window, run `get_url.ipynb`. It'll connect ngrok and give you a public URL like `https://xxxxx.ngrok-free.app`. Copy that down.

4. **Give It a Test**: Open `api_test.ipynb`, paste your ngrok URL into the `ngrok_url` variable, and run it. You should see a prediction pop up!

## The API Details

The main endpoint is `/predict`. Send a POST request to `{your_ngrok_url}/predict` with JSON like this:

```json
{
  "features": [17.99, 10.38, 122.8, 1001.0, 0.1184, 0.2776, 0.3001, 0.1471, 0.2419, 0.07871, 1.095, 0.3563, 7.039, 175.7, 0.006399, 0.04904, 0.05373, 0.01587, 0.03003, 0.006193, 25.38, 17.33, 184.6, 2019.0, 0.1622, 0.6656, 0.7119, 0.2654, 0.4601, 0.1189]
}
```

You'll get back something like:

```json
{
  "prediction": "malignant"
}
```

Just make sure you send exactly 30 numbers in that "features" array – that's what the model expects.

## A Few Tips

- Keep the Flask notebook running while you're testing, or the API won't work.
- Ngrok URLs are temporary, so if you restart it, you'll get a new one.
- This is just for fun and learning – for real-world stuff, you'd want to deploy on something like Heroku or AWS.

Feel free to poke around and change things up. If you have questions or run into issues, hit me up!

## License

Go ahead and use this for whatever – it's all open source and meant for learning.
