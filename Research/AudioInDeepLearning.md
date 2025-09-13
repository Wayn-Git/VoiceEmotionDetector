# Audio in Deep Learning | Digital Representation of Sound 

## Analog → Digital

- Analog Sound -> Analog Sound is basically continous, we can also say that it is the true form while at the moment it was recorded. Some examples of analog sound are your voice, guitar, thunder. Here the vibration between the particles is continous. <br> the key idea is that Analog is smooth, infinite and a real world signal

- Digital Sound -> Digital Sound is more like the sound broken down in to pieces. A computer can't store infinite details, so it takes snapshots of the analog wave. This process is also called sampling. Sampling is when we convert the analog sound to digital sound to get snapshots of the analog sound instead of the whole thing. Examples are MP3, Wav. <br> The key idea in this case is that Digital -> Chopped in numbers -> easy for the computer

<img src="https://www.electronicproducts.com/wp-content/uploads/digital-ics-video-graphics-audio-1.png" alt="Compression and Refraction" width="600">

[Referred Article/Webpage](https://www.electronicproducts.com/analog-vs-digital-sound/)


## Sampling rate

Sample rate is the number of number of snapshots of the original digial signal the computer takes in a signal second. <br> it is mainly measured in kilohertz (khz)

[Video Referred](https://youtu.be/xJKypZXc3B4)

### Audio's with different sample rates 

#### Orginal Audio
<audio controls>
  <source src="Images\Original-16-bit-44-1-khz.flac" type="audio/flac">
  Your browser does not support the audio element.
</audio>

#### 16-bit-32-khz
<audio controls>
  <source src="Images\16-bit-32-khz.flac" type="audio/flac">
  Your browser does not support the audio element.
</audio>



#### 16-bit-16-khz.flac
<audio controls>
  <source src="Images\16-bit-16-khz.flac" type="audio/flac">
  Your browser does not support the audio element.
</audio>

#### 16-bit-8-khz.flac
<audio controls>
  <source src="Images\16-bit-8-khz.flac" type="audio/flac">
  Your browser does not support the audio element.
</audio>

## Bit depth

Bit depth in digital audio is the number of bits used to represent the amplitude of each individual sample of a sound wave <br>
Examples of Common Bit Depths -> 

- 16-bit: <br> The standard for CD audio, it offers 65,536 possible amplitude levels and a dynamic range of approximately 96 dB

- 24-bit: <br>Used for high-resolution audio and professional recording, providing over 16 million levels and a dynamic range of about 144 dB, which allows for greater detail and a lower noise floor

### How Bit Depth Works

1. Sampling: When an analog sound wave is converted to digital, it's broken down into discrete snapshots or "samples" at regular intervals. 

2. Quantization: Each sample's amplitude (loudness) is then assigned a numerical value

3. Bits: Bit depth defines how many bits are used for this numerical value. Each bit can be a 0 or a 1, so the number of bits determines the total number of possible amplitude values

[Link Referred](https://headphonesaddict.com/sample-rate-bit-depth-and-bit-rate-explained/)

*Using a higher sample rate and bit depth theoretically more accurately reconstructs the sound waves.*

## Channels

What is a channel ? -> A channel normally is a passage where data is tranported. A channel could have multiple meaning depending on the context but when we are talking about audio we are mainly talking about a medium where we transport sound signal from player source to a speaker

An audio file can contain one(*mono*) two (*stereo*) or even more channels (*surround sound*)

Mono audio is like the same audio/loudness on both left and right of the speaker

Stereo is like the same sound but different loudness on both left and right of the speaker depending on the way it has been represented

<!-- ![Mono and Stereo](https://www.headphonesty.com/wp-content/uploads/2023/12/Differences_Between_Mono_vs__Stereo_Audio-1100x825.jpg) -->

<img src="https://www.headphonesty.com/wp-content/uploads/2023/12/Differences_Between_Mono_vs__Stereo_Audio-1100x825.jpg" width="600">

[Image From Headphonesty](https://www.headphonesty.com/2022/01/what-is-the-difference-between-mono-and-stereo/)


When we talk about channels it's the way the sound is heard. Surround sound would have the audio coming frmo multiple directions 

<!-- ![Surround Sound](https://www.audioholics.com/audio-technologies/7-1-surround-sound/image_large2) -->

<img src="https://www.audioholics.com/audio-technologies/7-1-surround-sound/image_large2" width="600">

[Image frmo UDIOHOLICS](https://www.audioholics.com/audio-technologies/7-1-surround-sound)


[Article Read](https://www.metadata2go.com/file-info/channels)


## File formats

Some of the common audio file formats for deep learning are as follow -> <br>

#### WAV (Waveform Audio File Format): <br>
- Type: Uncompressed <br>
- It's widely supported, large file size and high fidelity.<br>Often preferred for research and tasks that require higher <br> or we can say maximum audio quality

#### FLAC (Free Losleess Audio Codec): <br>
- Type: Lossless Compression <br>
- It reduces file size without any loss of audio data maintaing high fidelity <br> Represents a good balance between quality and size making it suitable for larger data sets

#### MP3 (MPEG-1 Audio Layer 3): <br>
- Type: Lossy Compression. 
- It achives some massive file reduction while sacrificing a little bit of audio quality.
- Useful for applications where file size is a major constraint and minor quality degradation is acceptable, such as mobile or web-based deployments.

## Time vs frequency domain

- Time domain is all about analysis of signals amplitude over time, It's like watching the ups and downs of the wave as it moves across the time line

<img src="https://miro.medium.com/v2/resize:fit:640/format:webp/1*GTqfmSzZtd_PJEjNV41O8A.png" alt="Compression and Refraction" width="600">


- Frequency Domain on the other hand represents a signal by analyzing its frequency compononents showing how much of the signals energy is distributed across different frequencsies


<img src="https://miro.medium.com/v2/resize:fit:640/format:webp/1*V4WWDPO_chv-CX-dILyPPw.png" alt="FrequencyDomain" width="600">

### Analogy

Time domain = Like watching someone talk and measuring how loud they are each moment

Frequency domain = Like analyzing which notes they’re using, regardless of when

### Why does it matter ? 

It matters because time domain data is more like raw waveform which is harder for the models and has a huge size<br>

like wise the data of frequency domain which is mostly 
spectrograms, MFCCS (Mel-Frequency Cepstral Coefficients) It's much more compact and meaningful making most deep learning audio models work with spectrograms. 

<img src="http://www.polytechnichub.com/wp-content/uploads/2017/05/time-and-frequency1.gif" alt="Compression and Refraction" width="600">

[Referred Link](https://www.polytechnichub.com/difference-time-domain-frequency-domain/)