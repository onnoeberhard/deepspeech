# Effects of Layer Freezing on Transferring a Speech Recognition System to Under-resourced Languages
Link to paper: https://konvens2021.phil.hhu.de/wp-content/uploads/2021/09/2021.KONVENS-1.19.pdf

Link to talk: https://youtu.be/xYqrwV2y2jc, Slides in this repository.

BibTeX:
```
@inproceedings{eberhard2021effects,
  author    = {Onno Eberhard and Torsten Zesch},
  title     = {Effects of Layer Freezing on Transferring a Speech Recognition System to Under-resourced Languages},
  booktitle = {Proceedings of the 17th Conference on Natural Language Processing (KONVENS 2021)}
}
```

---

This repository contains additional resources for the paper "Effects of Layer Freezing on Transferring a Speech Recognition System to Under-resourced Languages".

The steps taken for training the models are compiled in the file `training.sh`. The training and testing output logs can be found in the `logs` directory.

The modified versions of DeepSpeech that utilize layer freezing can be found at https://github.com/onnoeberhard/deepspeech-transfer, the different versions with the first _N_ layers frozen are in the branches **transfer-1** (_N = 1_), **transfer-2** (_N = 2_), **transfer** (_N = 3_), **transfer-lstm** (_N = 4_) and  **transfer-5** (_N = 5_). The version where the fifth instead of the LSTM layer is frozen is in branch **transfer-4**.

---

For freezing the LSTM, some custom modification of TensorFlow had to be made. This version of DeepSpeech uses TensorFlow 1.15.2 and the LSTM (when training on GPU) is an instance of `CudnnLSTM`. To make this class freezable, we had to modify the method `_create_saveable` of the `_CudnnRNN` class by exchanging all instances of `self.trainable_variables` by `self.trainable_variables if self.trainable else self.non_trainable_variables`.
