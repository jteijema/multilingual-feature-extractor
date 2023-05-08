# ASReview multilingual feature extractor

This extension to ASReview implements a multilingual feature extractor algorithm, allowing for the analysis of records in multiple languages. The supported languages include:

Arabic, Chinese, Dutch, English, French, German, Italian, Korean, Polish, Portuguese, Russian, Spanish, Turkish, and more!

The extension utilizes the [`sentence-transformers/distiluse-base-multilingual-cased-v2`](https://huggingface.co/sentence-transformers/distiluse-base-multilingual-cased-v2) model, which is a multilingual sentence-transformers model that maps sentences to a 512-dimensional dense vector space.


## Installation

This model depends on Sentence-Transformers. Install it with:
```bash
pip install -U sentence-transformers
```

Install the multilingual feature extractor with:

```bash
pip install https://github.com/jteijema/asreview-multilingual-feature-extractor/archive/master.zip
```

## Usage

### ASReview LAB

ASReview LAB users can select the model in the [Model Selection](https://asreview.readthedocs.io/en/latest/features/pre_screening.html#select-model) step of the project setup. Choose "Multilingual Sentence Transformer" under "Feature extraction".

### Simulation

The new feature extractor `Multilingual Sentence Transformer` is defined in
[`asreviewcontrib/models/distiluse-base-multilingual.py`](asreviewcontrib/models/distiluse-base-multilingual.py) 
and can be used in a simulation.

```bash
asreview simulate example_data_file.csv -e multilingual
```

Test the feature extractor with:

```bash
asreview simulate benchmark:van_de_Schoot_2017 -e multilingual -m svm
```

Please note that, as with all sentence transformers, this model produces negative vector values. Consequently, it is not compatible with Naive Bayes classifiers, which require non-negative feature values.

## License

[MIT license](/LICENSE)

## Contact

For any questions or remarks, please send an email to asreview@uu.nl or open an issue.
