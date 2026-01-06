# CDC-X-YHills-Open-Project---Data-Science-PS

Environment SetupTo ensure all dependencies are met:
It is recommended to use a dedicated Conda environment.

Create the Environment:
conda create -n property_val python=3.9

Activate the Environment:
conda activate property_val

Install Dependencies:
pip install tensorflow pandas numpy scikit-learn matplotlib seaborn jupyter

Before proceeding, ensure the train and test datasets are downloaded and are named exactly as mentioned in the PS.

Project Execution Pipeline
The project is divided into three functional modules. They must be executed in the following order:
  Step 1: Data Acquisition (data_fetcher.ipynb)
    Purpose: Fetches satellite imagery for the property coordinates listed in the datasets.
    Action: Open the notebook and run all cells. It will create images/train and images/test directories and populate them with .jpg files named by property ID.

  Step 2: Data Cleaning & Preparation (preprocessing.ipynb)
    Purpose: Cleans the tabular data and synchronizes it with the successfully downloaded images.
    Key Operations:
      Anomaly Correction: Automatically identifies and corrects logical errors, such as the 33-bedroom outlier, using IRC standards.
      Feature Engineering: Calculates house age and renovation status.
      Normalization: Applies Log Transformation to prices and scales all numerical features to a $[0, 1]$ range.
    Action: Run all cells to generate train_preprocessed.csv and test_preprocessed.csv.
  
  Step 3: Model Training & Prediction (model_training.ipynb)
    Purpose: Builds, trains, and evaluates the Multi-Modal Neural Network.
    Key Operations:Data Pipeline: Uses a custom generator to feed image and tabular data simultaneously.
    Architecture: Fuses a CNN (for images) and an MLP (for data) into a single regression head.
    Validation: Calculates Final $R^2$ and RMSE scores.
    Action: Run all cells to train the model. The final cell will generate the predictions.csv file.3. 
  
  
Expected Outputs
Upon successful completion, your directory should contain:
images/: Folders containing thousands of .jpg satellite images.
train_preprocessed.csv: Cleaned and scaled training data.
predictions.csv: Your final submission file containing property IDs and predicted prices.
Model Performance: An $R^2$ score of approximately 0.71 and an RMSE reported in the final notebook.
