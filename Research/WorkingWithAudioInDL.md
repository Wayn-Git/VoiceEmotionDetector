# Preprocessing Audio | Features Extracted from Audio | Neural Network Architectures for Audio 

## Step by Step Instructions

## Setup & Dataset

1. Gather Data:
- Make sure consistent file format (I think wav would be better) 
- Sample rate for speech -> 16 khz

```bash
└───data
    ├───features
    ├───processed
    ├───raw
    └───splits
```

## Preprocessing an audio dataset (Done before Splitting the data)
### Resampling the audio data
Resampling is the process where we change sample rate of an audio signal (The raw audio data) while preversing the original characteristics. 

- This is mostly to done so we can make sure that sample rate of the audio data is compatible with the model we are going ot use

- Code example
```bash 
import librosa

audio_data_path = ".../content/data/raw"

def resample_audio(audio_path, target_sr=16000):
     y, sr = librosa.load(audio_path, sr=target_sr)
     return y, sr

y_resampled, sr = resample_audio(audio_data_path)
print(sr) # Will return 16000
```

### Converting other channels to mono

Converting any other audio channel to mono is actually really important, here are some of the reasons -> 
- It's simpler for the neural network to process
- It reduces redundancy and eliminates unnessary patterns.
- Helps the neural network to extract the patterns in the audio data easily
- It focuses on the core content
- Makes the training process faster (ofc as there is no complex data to process after converting it to signal channel)


Can be done using librosa
```bash 
y_mono = librosa.to_mono(y_resampled)
```

[Reffered Link](https://librosa.org/doc/main/generated/librosa.to_mono.html)


### Silence Removal

Removing silence is yet another import factor as it reduces the data itself by getting rid of the useless part of the audio. 

We can use librosas trim function in order to do this

```bash
y_trimmed, _ = librosa.effects.trim(y_mono) # We can use _ if we don't really need the index
```

### Filtering the dataset
Filtering is one of the most important step in data pre-processing, it involves the application of signal processing filters like low-pass, high-pass or band-pass filters. 
<br>
Filtering is mainly used to modify/alter the frequency content of an audio signal.
<br>
In general cases low pass filtering is applied to audio data to remove high frequency noise which ensure that the model focuses on relevant signal information.

*Librosa doesn't really provide filtering/Filters, we can use SciPy in order to apply filters to our audio data*

```bash 

import scipy.signal as signal
# Design a butter worth low-pass filter 
cutoff = 4000 # hz

b, a = signal.butter(N=6, Wn=cutoff/(sr/2),btype='low)

# Applying the filter

y_filtered = signal.filtfilt(b, a , y_trimmed)


```

### Normalization

Audio normalization is the process of adjusting an audio file's volume to a consistent, target level without altering its overall dynamics or tonal quality

This can be achived with librosa 

```bash
y_normalized = librosa.util.normalize(y_filtered)
```

**Output**: clean, standardized raw audio ready for splitting or feature extraction.


---

## Dataset Splitting

Dataset splitting is basically the process where we devide our data into subsets of 

- Training set *The data we gonna use to train our deep learning model*

- Validation Set *Used during the training to monitor the models perfomance to hyper parameter tune, helps to prevent overfitting*

-Test set *Used after training to evaluate the final models perfomance on unseen data.* 

Common Ratios -> 
- Training: 70-80%
- Validation: 10-15%
- Test: 10-15%

*We can go like 80+10+10*

---

## Converting audio data to model’s expected input

#### Features Extracted from Audio

##### Spectrogram (via Short-Time Fourier Transform)

##### Mel Spectrogram (maps frequencies to human ear scale)

##### MFCCs (Mel-Frequency Cepstral Coefficients)

---

## Neural Network Architectures for Audio

### **Classical Models**

#### CNNs
#### RNNs 

### **Modern Models**

#### CRNNs (CNN + RNN combo for best of both worlds)

### **Pretrained Models** (transfer learning)

#### Librosa + sklearn → for small projects

#### Hugging Face models 
#### Wav2Vec2
#### HuBERT
#### Whisper

## Training Pipeline

Optimizer (Adam, SGD, RMSprop)

Loss function (Cross-entropy for classification, MSE for regression)

Learning rate schedules

Batch size, number of epochs

Regularization (Dropout, Weight Decay, Early Stopping)

## Evaluation & Challenges  
- Accuracy, Precision, Recall, F1-score  