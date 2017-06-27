# Spatial Current Machine Learning Guide (sc-ml-guide)

# Description

A guide for machine learning with Internet-scale geospatial data.  This guide includes information on classifiers and training datasets for parsing and understanding large geospatial datsets, including [OpenStreetMap](https://www.openstreetmap.org).

**NLTK**

Many of the examples in this guide use the Python [Natural Language Toolkit](http://www.nltk.org/) (NLTK) for machine learning tasks.

# Contributing

[Spatial Current, Inc.](https://spatialcurrent.io) is currently accepting pull requests for this repository.  We'd love to have your contributions!  Please see [Contributing.md](https://github.com/spatialcurrent/osm-ml-guide/blob/master/CONTRIBUTING.md) for how to get started.

# License

This work is distributed under the **MIT License**.  See **LICENSE** file.

# Guide

This guide includes a list of classifiers and how they can be used.

## Naive Bayes Classifier

A [naive Bayes classifier](https://en.wikipedia.org/wiki/Naive_Bayes_classifier) can be used for simple categorizing of a set of documents.  A simple use case is using 2 related attributes of geospatial features to fill in sparse data, e.g., type of cuisine.

**Setup**

For python, Python Natural Language Toolkit (NLTK) is a great tool that has a naive Bayes classifier.  See [Chapter 6, Section 1.3](http://www.nltk.org/book/ch06.html) of the [Natural Language Processing with Python](http://www.nltk.org/book/) online book.

For Java, see the [Java-Naive-Bayes-Classifier](https://github.com/ptnplanet/Java-Naive-Bayes-Classifier), including the [runnable example](https://github.com/ptnplanet/Java-Naive-Bayes-Classifier/blob/master/example/RunnableExample.java).

**Workflow**

Below is a sample workflow with some `pseudo-code`.

- Collect training dataset, e.g., OSM extract or Spatial Current [SGOL](https://github.com/spatialcurrent/sgol) query.
- Generate frequency distribution of words
- Create vocabulary (select top `N` most common words from the frequency distribution)
- For each document in a training dataset, convert into a series of binary `contains(<word>)` features
- Train dataset
- Convert input into document
- Classify document, e.g., `category = classifier.classify(convert(document))`.

**Data**

See the `data.yml` file in `/data/naive-bayes-classifier` folder for bootstrapping a classifier to guess the cuisine of a point of interest, based on the name.

# Training Datasets

**osm_name_cuisine.csv**

This dataset includes a list of amenities in Washington, DC and Virginia that have `name=` and `cuisine=` tags.
