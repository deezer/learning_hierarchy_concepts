# Learning Unsupervised Hierarchies of Audio Concepts

This repository contains the Python (Tensorflow) code to reproduce the results of our accepted paper ["Learning Unsupervised Hierarchies of Audio Concepts"](https://arxiv.org/pdf/2207.11231.pdf) by D. Afchar, R. Hennequin and V. Guigue, that was presented at [ISMIR 2022](https://ismir2022.ismir.net/) (December 4-8, 2022).

## Result demo

You can access results demos at [research.deezer.com/concept_hierarchy](http://research.deezer.com/concept_hierarchy/), which includes useful interactive visualisations of the obtained graphs, as well as additional figures to help better interpret our (dense) tables of results.

## Conference material

Here is the playback of my moment of fame during ISMIR 2022. Watch me trip from the stage at 0:16, a must-see!

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/5UhiMOkU5W8/0.jpg)](https://www.youtube.com/watch?v=5UhiMOkU5W8)

You can also find my [**poster online**](https://research.deezer.com/concept_hierarchy/poster_ismir_29_afchar.pdf).


## Dataset

You could manage to provide the community with the main components of our experiment data. You can access it at [zenodo.org/record/7382664](https://zenodo.org/record/7382664). Due to legal requirements (and pragmatical upload size), we have

1.  Reduced each track to its 30 seconds preview;
2.  Transformed each 30s in mel-spectrograms, resulting in tensors of size `(7501, 96)`;
3.  Embedded each spectrogram through a CNN backbone, resulting in tensors of size `(29, 128)`;
4.  Saved each tensor under an anonymised id in tensorflow-serialised format.

In our original training pipeline, we randomly sampled tensors along the temporal axis of the spectrogram for data augmentation. Because we cannot publish the spectrogram but only the embedded part, we have adapted the published code to sample along the temporal axis of the embedding. Doing so necessarily changes our results a little. For obvious reproducibility reasons, we have partly rerun our pipeline and checked that this added embedding step resulted in less than a 1% mean drop of accuracy (std 0.7%).

Note that the weights made available with this repository correspond to the the one directly trained on the spectrograms that thus benefited from a richer sampling strategy.


## Usage

If you want to run scripts for this repo you have multiple options :

* Using docker : run ```make docker SCRIPT=1_CAV_train.py``` 
* using poetry : run `````poetry install````` and then execute python code via \
```poetry run python concept_hierarchy/script.py```

*Usage for macOS ARM*

See https://developer.apple.com/metal/tensorflow-plugin/

## References

Contact: [research@deezer.com](mailto:research@deezer.com)

Consider citing our paper if you use our method in your own work:

```BibTeX
@inproceedings{afchar2022learning,
  title={Learning Unsupervised Hierarchies of Audio Concepts},
  author={Afchar, Darius and Hennequin, Romain and Guigue, Vincent},
  booktitle={International Society of Music Information Retrieval Conference (ISMIR)},
  year={2022}
}
```
