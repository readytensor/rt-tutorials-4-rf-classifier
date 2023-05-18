## Introduction

This repository is part of a comprehensive tutorial series on Ready Tensor aimed at building adaptable machine learning models. In this repository, we add an Random Forest binary classifier model with generalized APIs. The implementation uses a generalized interface for the classifier so that we can easily replace it with other classifier models, such as neural networks, without requiring any code change in the rest of the implementation.

The purpose is to create generalized algorithm implementations that avoid hard-coding your logic to a specific dataset. This makes it easier to re-use your algorithms with new datasets in the future without requiring any code change.

This repository is part of a tutorial series on Ready Tensor, a web platform for AI developers and users.

## Repository Contents

```bash
binary_class_project/
├── examples/
│   ├── titanic_schema.json
│   ├── titanic_train.csv
│   └── titanic_test.csv
├── inputs/
│   ├── data/
│   │   ├── testing/
│   │   └── training/
│   └── schema/
├── model/
│   └── artifacts/
├── outputs/
│   ├── hpt_outputs/
│   ├── logs/
│   └── predictions/
├── src/
│   ├── config/
│   │   ├── default_hyperparameters.json
│   │   ├── model_config.json
│   │   ├── paths.py
│   │   └── preprocessing.py
│   ├── data_model/
│   ├── hyperparameter_tuning/
│   ├── prediction/
│   │   ├── __init__.json
│   │   └── predictor_model.py
│   ├── preprocessing/
│   │   ├── custom_transformers.py
│   │   ├── pipeline.py
│   │   ├── preprocess.py
│   │   └── target_encoder.py
│   ├── schema/
│   │   └── data_schema.py
│   ├── xai/
│   ├── predict.py
│   ├── train.py
│   └── utils.py
├── tests/
│   ├── <mirrors `/src` structure ...>
│   ...
│   ...
│   └── test_utils.py
├── tmp/
├── .gitignore
├── LICENSE
├── README.md
└── requirements.txt
```

- **`/examples`**: This directory contains example files for the titanic dataset. Three files are included: `titanic_schema.json`, `titanic_train.csv` and `titanic_test.csv`. You can place these files in the `inputs/schema`, `inputs/data/training` and `inputs/data/testing` folders, respectively.
- **`/inputs`**: This directory contains all the input files for your project, including the data and schema files. The data is further divided into testing and training subsets.
- **`/model/artifacts`**: This directory is used to store the model artifacts, such as trained models and their parameters.
- **`/outputs`**: The outputs directory contains all output files, including the prediction results, logs, and hyperparameter tuning outputs.
- **`/src`**: This directory holds the source code for the project. It is further divided into various subdirectories such as `config` for configuration files, `data_model` for data models for input validation, `hyperparameter_tuning` for hyperparameter-tuning (HPT) related files, `prediction` for prediction model scripts, `preprocessing` for data preprocessing scripts, `schema` for schema scripts, and `xai` for explainable AI scripts. The script called `predictor_model.py` under `src/prediction` is used to implement the main classifier model.
- **`/tests`**: This directory contains all the tests for the project. It mirrors the `src` directory structure for consistency. Extensive unit tests are provided for the data preprocessing pipeline and target encoder.
- **`/tmp`**: This directory is used for storing temporary files which are not necessary to commit to the repository.
- **`.gitignore`**: This file specifies the files and folders that should be ignored by Git.
- **`LICENSE`**: This file contains the license for the project.
- **`README.md`**: This file contains the documentation for the project, explaining how to set it up and use it.
- **`requirements.txt`**: This file lists the dependencies for the project, making it easier to install all necessary packages.

See the following repository for information on the use of the data schema that is provided in the path `./src/inputs/data_config/`.

- [https://github.com/readytensor/rt-tutorials-data-schema](https://github.com/readytensor/rt-tutorials-data-schema)

See the following repository for more information on the data proprocessing logic defined in the path `./src/data_management/`.

- [https://github.com/readytensor/rt-tutorials-data-preprocessing](https://github.com/readytensor/rt-tutorials-data-preprocessing)

## Usage

- Create your virtual environment and install dependencies listed in `requirements.txt`.
- Place the following 3 input files from the `examples` folder in the sub-directories in `./src/inputs/`:
  - Train data, which must be a CSV file, to be placed in `./src/inputs/data/training/`. File name can be any; extension must be ".csv".
  - Test data, which must be a CSV file, to be placed in `./src/inputs/data/testing/`. File name can be any; extension must be ".csv".
  - The schema file in JSON format , to be placed in `./src/inputs/data_config/`. The schema conforms to Ready Tensor specification for the **Binary Classification** category. File name can be any; extension must be ".json".
- Run the script `train.py` to train the random forest classifier model. This will save the model artifacts, including the preprocessing pipeline and label encoder, in the path `./src/outputs/artifacts/`.
- Run the script `predict.py` to run test predictions using the trained model. This script will load the artifacts and create and save the predictions in a file called `predictions.csv` in the path `./src/outputs/predictions/`.

## Requirements

The code requires Python 3 and the following libraries:

```makefile
pandas==1.5.2
numpy==1.20.3
scikit-learn==1.0
feature-engine==1.2.0
imbalanced-learn==0.8.1
```

These packages can be installed by running the following command:

```python
pip install -r requirements.txt
```
