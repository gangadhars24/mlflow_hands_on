### Install MLFlow in Virtual environment
`pip install mlflow[extra]`

### Run mlflow server
`mlflow server --backend-store-uri mlruns/ --default-artifact-root mlruns/ --host 0.0.0.0 --port 5000`

### Deploy the model locally by running
`mlflow models serve -m mlruns/<exp_id>/<run_id>/artifacts/model/ -h 0.0.0.0 -p 1234`

### Test the endpoint
`curl -X POST -H "Content-Type:application/json; format=pandas-split" --data '{"columns":["alcohol", "chlorides", "citric acid", "density", "fixed acidity", "free sulfur dioxide", "pH", "residual sugar", "sulphates", "total sulfur dioxide", "volatile acidity"],"data":[[12.8, 0.029, 0.48, 0.98, 6.2, 29, 3.33, 1.2, 0.39, 75, 0.66]]}' http://0.0.0.0:1234/invocations`
