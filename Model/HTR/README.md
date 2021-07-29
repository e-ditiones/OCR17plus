# HTR Model

HTR models have to be used with [Kraken](https://github.com/mittagessen/kraken).

Except for preliminary experimentations (`bleu.mlmodel`), we use the same test set, available [here](https://github.com/e-ditiones/OCR17plus/blob/main/test.txt), to compare the efficiency of the different models.

Models are named after cheeses, following an alphabetical order.

## `bleu.mlmodel`

### Production

This model was produced thanks to the [release 1.0](https://github.com/Heresta/OCR17plus/releases/tag/1.0)). 
It was divided in three sets : `train` (training set), `val` (evaluation set) and `test` (test set), created with the [following script](https://github.com/gabays/Cours_2020_01_Strasbourg/blob/master/randomise_data.py).
1. `train` contained 82.76% of total dataset.
2. `val` contained 7.61% of total dataset.
3. `test` contained 9.62% of total dataset.

Commands used are:
* `ketos train -t train.txt -e val.txt -u NFKD -f alto` for training
* `ketos test -m model -f alto -e test.txt` for testing

### Results
Accuracy is:
* 96% on the evaluation set
* 91% on the test set.

## `cheddar.mlmodel`

### Production


This model was produced with the [2.0 version of the dataset](https://zenodo.org/record/5078165#.YQKUtY4zZPY). It was divided in three sets : `train` (training set), `val` (evaluation set) and `test` (test set). Those were created with [`train_val_prep.py`](https://github.com/e-ditiones/OCR17plus/blob/main/train_val_prep.py). It uses a prepared test set available [here](https://github.com/e-ditiones/OCR17plus/blob/main/test.txt).
1. `train` contained 75% of total dataset.
2. `val` contained 10% of total dataset.
3. `test` contained 15% of total dataset.

_Note: a problem occured during training. This model should not be used._

Commands used are:
* `ketos train -t train.txt -e val.txt -f alto -d cuda --normalization NFD` for training
* `ketos test -m model -f alto -e test.txt` for testing

### Results
Accuracy is:
* 96.3% on the evaluation set

## `dentduchat.mlmodel`

### Production

This model was produced with the [2.0 version of the dataset](https://zenodo.org/record/5078165#.YQKUtY4zZPY). It was divided in three sets : `train` (training set), `val` (evaluation set) and `test` (test set). Those were created with [`train_val_prep.py`](https://github.com/e-ditiones/OCR17plus/blob/main/train_val_prep.py). It uses a prepared test set available [here](https://github.com/e-ditiones/OCR17plus/blob/main/test.txt).
1. `train` contained 75% of total dataset.
2. `val` contained 10% of total dataset.
3. `test` contained 15% of total dataset.


Commands used are:
* `ketos train -t train.txt -e val.txt -f alto -d cuda --normalization NFD` for training
* `ketos test -m model -f alto -e test.txt` for testing

### Results
Accuracy is:
* 96.6% on the evaluation set
