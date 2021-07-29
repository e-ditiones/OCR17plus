# Models for layout analysis
HTR models have to be used with [Kraken](https://github.com/mittagessen/kraken).

Models are named after cheeses, following an alphabetical order.

The vocabulary of the segmentation is based on [SegmOnto vocabulary](https://github.com/SegmOnto/examples).


## `appenzeller.mlmodel`

### Production

This model was produced thanks to this dataset. Repartition between the train set and the evaluation set has been done automatically by Kraken.

### Results
This model has 99% accuracy, according to training Kraken.

It was tested on an untouched document, and it gave good results, except concerning Rubric lines or DropCapitalLine, which are rare in training dataset.

