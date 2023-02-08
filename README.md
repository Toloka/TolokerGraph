# Toloker Graph: Interaction of Crowd Annotators

This repository contains a graph representing interactions between crowd annotators on a project labeled on the [Toloka](https://toloka.ai/) crowdsourcing platform (see the [Toloka overview](https://toloka.ai/en/docs/guide/concepts/overview) for the details on the used terminology).

The graph contains 11,759 nodes and 519,000 edges. Each node represents an individual annotator; nodes are provided with four numerical and three categorical features. An edge is drawn between a pair of annotators if they annotated the same task. Also, each node is provided with a label showing whether the annotator was banned on this project, or not.

## Nodes

Nodes are stored in the [nodes.tsv](nodes.tsv) file in the TSV format of the following structure:

- `id`: unique identifier of the annotator
- `approved_rate`: percentage of the approved labels of this annotator
- `skipped_rate`: percentage of the skipped tasks of this annotator
- `expired_rate`: percentage of the expired tasks of this annotator
- `rejected_rate`: percentage of the rejected labels of this annotator
- `education`: level of education as self-reported by this annotator (`none`, `basic`, `middle`, `high`)
- `english_profile`: knowledge of English as self-reported by this annotator (`0` for no, `1` for yes)
- `english_tested`: whether the annotator passed the Toloka language test for English (`0` for no, `1` for yes)
- `banned`: whether the annotator was banned on this project (`0` for no, `1` for yes)

The `*_rate` attributes should sum up to 1.

## Edges

Edges are stored in the [edges.tsv](edges.tsv) file in the TSV format of the following structure:

- `source`: source identifier of the annotator
- `target`: target identifier of the annotator

As the graph is undirected, `source` and `target` can be interchanged for the given pair of nodes.

## Cross-Validation

We also release ten cross-validation train/validation/test splits in the files [splits_train.tsv](splits_train.tsv), [splits_val.tsv](splits_val.tsv), and [splits_test.tsv](splits_test.tsv). The first column, `id`, is the unique identifier of the annotator. Other ten columns are binary masks indicated whether this node is included in the current split. To obtain the complete first cross-validation split, one has to pick the first split from train, the first split from validation, and the first split of the test files.

## Copyright

Licensed under the Creative Commons Attribution 4.0 License. See LICENSE file for more details.
