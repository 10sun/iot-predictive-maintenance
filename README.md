# Internet of Things : Predictive Maintenance
This repository contains notebooks and scripts to get you started experimenting with predictive maintenance models.

The data for this project can be found [here](https://ti.arc.nasa.gov/tech/dash/pcoe/prognostic-data-repository/#turbofan). 

This repository is meant to accompany [this blog post](TODO: link blog post here).

## Getting Started

### Generating Train and Test Data
To generate necessary train/test data, execute the following command:
```
make data
```
This will produce a `data/` folder, which will contain the following:
```
data
├── processed
│   ├── RUL.csv
│   ├── test.csv
│   └── train.csv
└── raw
    ...
```
The files in `processed/` are cleaned and consolidated versions of the original files (stored in `raw/`), saved as CSVs. 

#### `train.csv` and `test.csv`

The `test.csv` and `train.csv` files are in the following format:

| Column     | Description                                                      |
|------------|------------------------------------------------------------------|
| dataset_id | id of the dataset where this instance is found                   |
| unit_id    | id of engine (unique in each dataset)                            |
| cycle      | number of operational cycles since beginning of engine operation |
| setting 1  | value of operational setting 1                                   |
| setting 2  | value of operational setting 2                                   |
| setting 3  | value of operational setting 3                                   |
| sensor 1   | value of sensor 1                                                |
| ...        | ...                                                              |
| sensor 21  | value of sensor 21                                               |

In the case of `train.csv`, observations continue until the time of failure of the unit. In `test.csv`, observations cease some number of cycles before engine failure. 

#### `RUL.csv`

| Column     | Description                                                                         |
|------------|-------------------------------------------------------------------------------------|
| dataset_id | id of the original dataset of this instance                                         |
| unit_id    | id of engine (unique in each dataset)                                               |
| rul        | the remaining useful life of this unit, after its maximum cycle in the test dataset |

### Example Notebook
For some example visualizations and exploration, see the example notebook in `notebooks/example.ipynb`. 
