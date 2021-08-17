# deepspeech
This repository contains additional resources for the paper "Effects of Layer Freezing on Transferring a Speech Recognition System to Under-resourced Languages".

The steps taken for training the models are compiled in the file `training.sh`. The training and testing output logs can be found in the `logs` directory.

The modified versions of DeepSpeech that utilize layer freezing can be found at https://github.com/onnoeberhard/deepspeech-transfer, the different versions with the first _N_ layers frozen are in the branches **transfer-1** (_N = 1_), **transfer-2** (_N = 2_), **transfer** (_N = 3_), **transfer-lstm** (_N = 4_) and  **transfer-5** (_N = 5_). The version where the fifth instead of the LSTM layer is frozen is in branch **transfer-4**.
