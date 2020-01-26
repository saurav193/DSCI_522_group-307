# Income Level Predictor
A data analysis project for DSCI 522 Data Science Workflows

Authors: <br>Saurav Chowdhury, Evhen Dytyniak, and Reiko Okamoto </br>
Date: 2020-01-24

## About

In this project, we build a classification model to predict the income levels of individuals based on their demographic and other socio-economic information.

The data that was used in this project was the created by Ronny Kohavi and Barry Becker, Data Mining and Visualization division at Silicon Graphics. This data is extracted from 1994 US Census. It was sourced from the UCI Machine Learning Repository (Dua and Graff 2017) and can be found [here](https://archive.ics.uci.edu/ml/datasets/adult). Each row in the data represents the attributes of an individual like - age, education level, race, working hours, etc. The target variable is whether his/her income is above or below $$50K. There are other less important features not taken into consideration are - capital_gain, capital_loss, fnlwgt. 

## Report
The report can be found [here]().

## Usage
To replicate this analysis, clone this repository, install the dependencies, and run the following commands at the command line from the root directory. 

```
# Download data -train
Python scripts/1_download_data.py --url="https://archive.ics.uci.edu/ml/machine-learning-databases/adult/adult.data" --out_path="data/adult_train_data.csv"

# Download data -test
Python scripts/1_download_data.py --url="https://archive.ics.uci.edu/ml/machine-learning-databases/adult/adult.test" --out_path="data/adult_test_data.csv" --skiprows=1

# Pre-process - train
Python scripts/2_wrangle_data.py --in_file="data/adult_train_data.csv" --out_dir="data"

# Pre-process - test
Python scripts/2_wrangle_data.py --in_file="data/adult_test_data.csv" --out_dir="data" --istrain=0

# Create EDA tables and figures
Rscript scripts/3_eda.R --train=clean_train_data.feather --out_dir=data --out_dir_plt=imgs

# Run ML analysis
Python scripts/4_ml_analysis.py --train="data/clean_train_data.feather" --valid="data/clean_validation_data.feather" --test="clean_test_data.feather" --outputdir="results"

# Render final report
```

## Dependencies
- Python 3.7.3 and Python packages:
    - docopt == 0.6.2
    - requests == 2.22.0
    - pandas == 0.25.3
    - numpy ==  1.18.1
    - scikit-learn == 0.22.1
    - feather == 0.4.0
- R version 3.6.1 and R packages:
    - knitr == 1.27.2
    - feather == 0.3.5
    - tidyverse == 1.3.0
    - plyr == 1.8.4
    - docopt == 0.6.1
    - ggridges == 0.5.2
    - ggthemes == 4.2.0


### License

The Income Level Predictor materials are licensed under the MIT License - Copyright (c) 2020 Master of Data Science at the University of British Columbia. 

## References

Dua, D. and Graff, C. (2019). UCI Machine Learning Repository . Irvine, CA: University of California, School of Information and Computer Science. [http://archive.ics.uci.edu/ml]
