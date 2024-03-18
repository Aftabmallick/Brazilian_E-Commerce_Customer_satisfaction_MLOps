# Brazilian_E-Commerce_Customer_satisfaction_MLOps
**Problem Statement:**
Our goal is to predict customer satisfaction scores for upcoming orders or purchases by analyzing historical data from the Brazilian E-Commerce Public Dataset by Olist. This dataset contains information on 100,000 orders spanning 2016 to 2018, encompassing various aspects such as order status, pricing, payment details, customer location, product attributes, and customer reviews. To achieve this prediction task, we will build a machine learning pipeline using ZenML.

**Approach:**
We plan to develop an end-to-end pipeline using ZenML, enabling continuous prediction and deployment of machine learning models. This pipeline will involve stages for data ingestion, cleaning, model training, evaluation, and deployment. Additionally, we will integrate MLflow for model tracking and deployment. To facilitate real-world usage, we will create a Streamlit application.

**Key Components:**
1. **Data Ingestion:** Obtain and preprocess data from the Olist dataset.
2. **Data Cleaning:** Remove irrelevant columns and clean the dataset.
3. **Model Training:** Train machine learning models to forecast customer satisfaction scores.
4. **Model Evaluation:** Assess model performance and record metrics using MLflow tracking.
5. **Continuous Deployment:** Implement a continuous deployment workflow to deploy models meeting predefined criteria.
6. **Streamlit Application:** Develop a Streamlit app for interactive predictions based on the latest deployed model.

**Pipeline Execution:**
To execute the pipeline, follow these steps:

1. Clone the repository:
   ```bash
   git clone https://github.com/Aftabmallick/Brazilian_E-Commerce_Customer_satisfaction_MLOps.git
   cd Brazilian_E-Commerce_Customer_satisfaction_MLOps
   ```

2. Install the required Python packages:
   ```bash
   pip install -r requirements.txt
   ```

3. Launch the ZenML Server and Dashboard locally:
   ```bash
   pip install zenml["server"]
   zenml up
   ```

4. Install necessary integrations for deployment script:
   ```bash
   zenml integration install mlflow -y
   ```

5. Register components for the ZenML stack:
   ```bash
   zenml integration install mlflow -y
   zenml experiment-tracker register mlflow_tracker_customer --flavor=mlflow
   zenml model-deployer register mlflow_customer --flavor=mlflow
   zenml stack register mlflow_stack -a default -o default -d mlflow_customer -e mlflow_tracker_customer --set
   ```

6. Run the training pipeline:
   ```bash
   python run_pipeline.py
   ```

7. Execute the continuous deployment pipeline:
   ```bash
   python run_deployment.py
   ```

**Demo Streamlit App:**
To run the app locally:
```bash
streamlit run app.py
```

**FAQ:**
1. If encountering the error "No Step found for the name mlflow_deployer" during continuous deployment pipeline execution, delete the artifact store and rerun the pipeline.
2. If facing the error "No Environment component with name mlflow is currently registered," install the MLflow integration:
   ```bash
   zenml integration install mlflow -y
   ```