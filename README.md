# Accent-Classification-Deep-Learning

### Introduction and Problem Statement
Non-native accents have posed a great challenge for speech recognition systems. The information of tonal variation in the speech can be used to classify the accents. The goal of this project is to classify various types of accents, specifically foreign accents, by the native language of the speaker.  We use a dataset of recorded audio files, each from different person reading the same English passage. Previous works using this audio based dataset have only been conducted for a fewer accent classes. Since the dataset is heavily imbalanced, in this paper we aim to perform data augmentation to balance the dataset and explore the performance of the models on large pool of accent classes using deep-learning approaches like CNN, LSTM and Transformer-with-Attention with accuracy as the metric.

### Feature Extraction
We use Librosa, off-the-shelf library to extract audio features like Mel Frequency Cepstral Co-efficients (MFCC)  spatial features of the audio files. These features account for human perception sensitivity with respect to frequencies, and thus is appropriate for speech/accent recognition. The MFCC is a representation of the short-term power spectrum of a sound, based on a linear cosine transform of a log power spectrum on a nonlinear mel scale of frequency.

We train three deep-learning models CNN, LSTM and Transformer(with attention) on MFCCs and report the performances of each model.

### Dataset
We used dataset from Kaggle's Speech Accent Archive[8]. The dataset contains 2140 speech samples. Each speaker reads a passage in English and the corresponding audio is recorded in mp3 format. The Dataset contains accents from 177 countries and have 214 different native languages.

### Data Augmentation
we augment the samples by adding effects like time-stretch and pitch to the audio files. These effects would in practice increase and decrease the speed of the audio files and alter the pitch of the audio files.

The effects functions are applied in the following order: 1. pitch-stretch: If the audio file is that of a male then we apply pitch-stretch with n-steps of 4 which would increase the pitch thus changing to a female tone, if female, then pitch-shift with n-steps of -4 which would decrease the pitch thus changing to a male tone. 2. time-stretch with stretch-factor 2.0 which increases speed of the audio, 3.  time-stretch with stretch-factor of 0.5 which decreases the speed of the audio.

### Approaches
1. 1D CNN + LSTM

2. 2D CNN

3. Transformer with attention

### Results

LSTM with Original Data                   -->  23.0%

1D-CNN-LSTM with Augmented Data           -->  26.46%

2D-CNN with Augmented Data                -->  64.00%

Transformer(Attention) with Augmented Data --> 49.80%

### Conclusion
The augmented data works well for CNN models and shows significant performance gains.

Harder to capture the accent as accent speech signal is different from other high-level features of speech.

Model performance was degraded due to low number of samples and the presence of non-accented speakers in the various accent categories.

### Takeaways
MFCCs performed better overall.

Always look for dataset with abundant labelled data. If not, look for augmentation techniques that suit your data.

Using complex architectures does not necessarily mean better performance. 

If the dataset is not large enough be careful with the number of neurons and layers.

Due to complexity of the Transformer model, it overfit the data and we was unable to achieve better accuracy. On further reducing the number of multi-head attention units, neurons and depth of the network the accuracy started to increase, suggesting that using simpler network will be beneficial to fit small data.



