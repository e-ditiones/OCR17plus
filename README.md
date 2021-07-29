# `OCR17+` - Layout analysis and text recognition for 17th c. French prints

This repo contains training data and models for Layout analysis and text recognition for 17th c. French prints

```diff
- This repo is an updated version of the OCR17 repo. It uses XML files and not .png/.txt pairs.
```

The old repo is still available <a href="https://github.com/e-ditiones/OCR17" target="_blank"> here</a>.

## How to use

Training data is organised per print:
* `Balzac1624_Lettres_btv1b86262420_corrected`
* `Boyer1697_Meduse_cb30152139c_corrected`
* …

To train a model, all the data needs to added to a single file, prior to the repartition between train, validation and test. To do so:
1. `git clone https://github.com/e-ditiones/OCR17plus`
2. `cd datasetsOCRSegmenter17`
3. `bash build_train_alto_Seg17.sh` creates a `trainingDataSeg17` directory
4. `python train_val_prep.py ./trainingDataSeg17/*.xml` creates two new files `train.txt` (with training data) and `val.txt` (validation data).
5. If you have kraken installed, you can use `ketos segtrain -t train.txt -e val.txt  -o model -d cuda -f alto -q early -bl` to train a model for layout analysis

The `test.txt` file is already prepared for the reproducibility of the test, and evaluate the improvement over time. It was created with 3 title pages, 14 pages containing damage, 2 pages with margin, 14 with decoration, 19 with rubric or signatures (or both), 1 with a running title on bottom of page, 3 pages with decorated drop capitals, 7 with basic drop capitals and 28 basic pages. This test file can also be used for an HTR training test.

## Structure

The structure of the repo is the following:

```
├── Data
│     ├── Print_1
│     │  ├── alto4eScriptorium
│     │  ├── pageXmlTranskribus
│     │  ├── pagexmlTranskribusCorrected
│     │  └── png
│     ├── Print_2
│     │  ├── alto4eScriptorium
│     │  ├── pageXmlTranskribus
│     │  ├── pagexmlTranskribusCorrected
│     │  └── png
│     └── …
├── Models
|     ├── HTR
|     |	 ├── bleu.mlmodel
|     |  ├── cheddar.mldmodel
|     |  ├── dentduchat.mldmodel
|     |  └── README.md
|     └── Segment
|	 ├── appenzeller.mlmodel
|        └── README.md
├── build_train_alto_Seg17.sh
├── files_informations.csv
├── parts_dataset.csv
├── train_val_prep.py
├── test.txt
├── segmontoAltoValidator.xsd
├── validator_alto.py
└── README.md
```

The [``Data``](https://github.com/e-ditiones/OCR17plus/tree/main/Data) directory contains excerpts of 17<sup>th</sup> century books, _i.e._ scans of selected pages and their encoding in
1. PageXML
2. ALTO-4 files.

Regarding the difference between all these directories, cf. _infra_, <a href="#data-description">§ Data description<a/>.

Prints have been selected in the [OCR17 repo](https://github.com/e-ditiones/OCR17), and are all 
described individually in their respective folder.
  
The [``Models``](https://github.com/e-ditiones/OCR17plus/tree/main/Model) directory contains models for:
1. [HTR](https://github.com/e-ditiones/OCR17plus/tree/main/Model/HTR)
2. [Layout analysis](https://github.com/e-ditiones/OCR17plus/tree/main/Model/Segment). The layout analysis is based on the [SegmOnto](https://github.com/SegmOnto) vocabulary.
  * [`files_informations.csv`](https://github.com/e-ditiones/OCR17plus/blob/main/files_informations.csv) indicates in which file found specific zones.
  * [``parts_dataset.csv``](https://github.com/e-ditiones/OCR17plus/blob/main/parts_dataset.csv) contains the percentage of each specificity in this dataset.

Validation of the XML data pushed on the repository is made via ``segmontoAltoValidator`` and ``validator_alto.py``. They comme from [HTR-United/cremma-medieval repository](https://github.com/HTR-United/cremma-medieval).

## Data description
Some of used data come from the [OCR17 repo](https://github.com/e-ditiones/OCR17), the composition of which started 
with [Transkribus](https://readcoop.eu/transkribus), which needs to be adapted for eScriptorium. Therefore, for each print exported from transkribus, we propose
1. The exported file (`pageXmlTranskribus`)
2. The exported file prepared form for eScriptorium (`pagexmlTranskribusCorrected`)
3. The version exported from eScriptorium (`alto4eScriptorium`)

<p align="center">
  <img src="img/general_flowchart.png" width="400"/>
</p>

## Credits

Data prepared and models trained by Claire Jahan with the help of Simon Gabay, as part of the [_E-ditiones_](https://github.com/e-ditiones) project.
  
## Contact
Claire Jahan : claire.jahan[at]chartes.psl.eu

Simon Gabay : Simon.Gabay[at]unige.ch

## Cite this dataset
Claire Jahan and Simon Gabay, _OCR17+ - Layout analysis and text recognition for 17th c. French prints_, 2021, Paris/Genève: ENS Paris/UniGE, https://github.com/e-ditiones/OCR17plus.

## Licence
Data is CC-BY, except images which come from Gallica 
(cf. [conditions d'utilisation](https://gallica.bnf.fr/edit/und/conditions-dutilisation-des-contenus-de-gallica)).

![68747470733a2f2f692e6372656174697665636f6d6d6f6e732e6f72672f6c2f62792f322e302f38387833312e706e67](https://user-images.githubusercontent.com/56683417/115237678-2150d080-a11d-11eb-903e-5a26587e12e1.png)

