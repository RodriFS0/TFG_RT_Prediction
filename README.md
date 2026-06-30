# TFG_RT_Prediction

This repository contains the code, processed data blocks, model outputs, statistical analyses, and figures developed for a Bachelor's Thesis focused on retention time prediction using machine learning.

The project evaluates different modelling strategies for predicting chromatographic retention time. In particular, it compares global models and individual models trained under different optimization settings, with a specific focus on the effect of hyperparameter optimization using Optuna.

## Project overview

Retention time is an important variable in chromatographic analysis. Accurate retention time prediction can support compound annotation, method comparison, and data interpretation in analytical workflows.

This project studies whether the training strategy affects prediction performance across multiple chromatographic configurations. The analysis includes:

* Data preprocessing and feature preparation.
* Train, validation, and test split generation.
* Global model training.
* Individual model training by chromatographic configuration.
* Hyperparameter optimization using Optuna.
* Model evaluation using regression metrics.
* Paired statistical comparison between modelling strategies.
* Generation of supplementary plots and result tables.

## Repository structure

```text
TFG_RT_Prediction/
│
├── data/
│   ├── DataSet_Blocks.zip
│   └── README.md
│
├── notebooks/
│   ├── Data_Preprocessing/
│   │   ├── column_codification.ipynb
│   │   ├── fingerprints_preprocessing.ipynb
│   │   └── gradient_codification.ipynb
│   │
│   ├── Data_Splitting/
│   │   └── Data_SplitModelPreparator.ipynb
│   │
│   ├── Optuna_Training/
│   │   ├── OptunaGeneral.ipynb
│   │   └── OptunaIndividual.ipynb
│   │
│   ├── Results_Statistical_Tests/
│   │   ├── ResultDataMerger.ipynb
│   │   └── PairedStatisticAnalisis.ipynb
│   │
│   ├── Plotter_utils/
│   └── extras/
│
├── Optuna_Training_Results/
│   ├── Final_Global_Optimized_Model-20260630T215554Z-3-001.zip
│   ├── Global_Optuna-20260630T215546Z-3-001.zip
│   ├── Individual_Optuna.zip
│   └── README.md
│
├── figures/
│   ├── global_fixed_vs_global_optuna_*.png
│   ├── individual_fixed_vs_global_fixed_*.png
│   ├── individual_fixed_vs_individual_optuna_*.png
│   ├── individual_optuna_vs_global_optuna_*.png
│   └── README.md
│
├── Documents/
└── README.md
```

## Workflow

The project follows this general workflow:

1. Data preprocessing

   The raw and intermediate data are processed to generate a numerical representation suitable for model training. This includes molecular fingerprint preprocessing, column codification, and chromatographic gradient codification.

2. Data splitting

   The preprocessed dataset is divided into training, validation, and test sets. This step prepares the data used for model development and final evaluation.

3. Model training and hyperparameter optimization

   Two main training strategies are evaluated:

   * Global model: one model trained using data from all chromatographic configurations.
   * Individual models: separate models trained for each chromatographic configuration.

   Optuna is used to optimize the hyperparameters of the models.

4. Results integration

   Model outputs are merged into summary tables to allow direct comparison between strategies.

5. Statistical analysis

   Paired statistical tests are performed to compare model performance across chromatographic configurations. These analyses are used to evaluate whether the observed differences between strategies are consistent and statistically meaningful.

6. Figure generation

   Supplementary plots are generated to visualize performance differences, improvement distributions, ranked improvements, paired comparisons, and estimation summaries.

## Main notebooks

### Data preprocessing

`notebooks/Data_Preprocessing/column_codification.ipynb`

Encodes categorical or descriptive columns into numerical variables suitable for modelling.

`notebooks/Data_Preprocessing/fingerprints_preprocessing.ipynb`

Processes molecular fingerprint information and prepares molecular descriptors for model input.

`notebooks/Data_Preprocessing/gradient_codification.ipynb`

Processes chromatographic gradient information and converts experimental conditions into model-compatible features.

### Data splitting

`notebooks/Data_Splitting/Data_SplitModelPreparator.ipynb`

Creates the train, validation, and test partitions used during model development and evaluation.

### Optuna training

`notebooks/Optuna_Training/OptunaGeneral.ipynb`

Performs hyperparameter optimization and training for the global modelling strategy.

`notebooks/Optuna_Training/OptunaIndividual.ipynb`

Performs hyperparameter optimization and training for the individual modelling strategy.

### Results and statistical tests

`notebooks/Results_Statistical_Tests/ResultDataMerger.ipynb`

Merges model outputs and evaluation results into unified comparison tables.

`notebooks/Results_Statistical_Tests/PairedStatisticAnalisis.ipynb`

Performs paired statistical analyses between modelling strategies.

## Model comparisons

The repository includes results and figures for the following comparisons:

* Individual fixed model vs global fixed model.
* Individual fixed model vs individual optimized model.
* Global fixed model vs global optimized model.
* Individual optimized model vs global optimized model.

These comparisons allow the analysis to separate two effects:

* The effect of the modelling strategy.
* The effect of hyperparameter optimization.

## Evaluation metrics

The models are evaluated using regression metrics, including:

* Mean Absolute Error, MAE.
* Root Mean Squared Error, RMSE.
* Coefficient of determination, R².

The paired comparison across chromatographic configurations is used to assess whether performance differences are consistent across experimental conditions.

## Statistical analysis

The statistical analysis is based on paired comparisons between model strategies. This approach compares the models under the same chromatographic configurations, which makes the comparison more appropriate than using only global aggregate metrics.

The statistical workflow includes:

* Paired performance comparison by chromatographic configuration.
* Hypothesis testing.
* Multiple testing correction when required.
* Effect size estimation.
* Summary of improved configurations.

## Data and results

The `data/` directory contains compressed data blocks used during the project.

The `Optuna_Training_Results/` directory contains compressed outputs from the optimized training workflows, including global and individual Optuna results.

The `figures/` directory contains the plots generated from the comparative analyses.

Before running the notebooks, extract the compressed `.zip` files and ensure that the expected folder paths are correctly set inside each notebook.

## Requirements

The project was developed using Python and Jupyter Notebooks.

Main Python packages used in the workflow include:

```text
numpy
pandas
scikit-learn
scipy
statsmodels
matplotlib
seaborn
torch
optuna
```

A recommended setup is:

```bash
pip install numpy pandas scikit-learn scipy statsmodels matplotlib seaborn torch optuna
```

If running the notebooks in Google Colab, install any missing package inside the notebook before executing the corresponding section.

## How to reproduce the workflow

1. Clone the repository.

```bash
git clone https://github.com/RodriFS0/TFG_RT_Prediction.git
cd TFG_RT_Prediction
```

2. Extract the compressed data files.

Extract the contents of:

```text
data/DataSet_Blocks.zip
Optuna_Training_Results/Final_Global_Optimized_Model-20260630T215554Z-3-001.zip
Optuna_Training_Results/Global_Optuna-20260630T215546Z-3-001.zip
Optuna_Training_Results/Individual_Optuna.zip
```

3. Run the notebooks in order.

Recommended execution order:

```text
1. notebooks/Data_Preprocessing/
2. notebooks/Data_Splitting/Data_SplitModelPreparator.ipynb
3. notebooks/Optuna_Training/OptunaGeneral.ipynb
4. notebooks/Optuna_Training/OptunaIndividual.ipynb
5. notebooks/Results_Statistical_Tests/ResultDataMerger.ipynb
6. notebooks/Results_Statistical_Tests/PairedStatisticAnalisis.ipynb
7. notebooks/Plotter_utils/
```

4. Check generated outputs.

Review the output tables, statistical summaries, and figures generated by each notebook.

## Notes on reproducibility

Some notebooks may require path adjustments depending on whether they are executed locally or in Google Colab.

For reproducible execution, check:

* Input file paths.
* Output directory paths.
* Random seeds.
* Python package versions.
* Availability of extracted data files.
* GPU availability for model training.

## Thesis context

This repository supports the computational part of a Bachelor's Thesis in Biomedical Engineering. The objective of the work is not to develop a final state-of-the-art retention time prediction model, but to evaluate how different training strategies affect model performance across chromatographic configurations.

The repository is intended to provide transparency, traceability, and reproducibility for the data processing, model training, result generation, and statistical analysis performed during the project.

## Author

RodriFS0

## License

No license has been specified for this repository.
