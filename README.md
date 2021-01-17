# multimodal-speech-emotion
This repository contains migrate code from below repository
because original repo is made in 2018 (use python2, tf1)

**Multimodal Speech Emotion Recognition using Audio and Text**, IEEE SLT-18, <a href="https://arxiv.org/abs/1810.04635">[paper]</a>[[repo]](https://github.com/david-yoon/multimodal-speech-emotion)

----------
### [Migrate Flow]
1. Python2 Migrate python 3.8 (current working)
2. tf1 -> tf2
3. tf -> pytorch

### [requirements]
	tensorflow==2.4 (tested on cuda-10.2)
	python==3.8
	scikit-learn==0.23.2
	nltk==3.5

---
## SAME WITH ORIGINAL REPO

### [download data corpus]
- IEMOCAP <a href="https://sail.usc.edu/iemocap/">[link]</a>
<a href="https://link.springer.com/article/10.1007/s10579-008-9076-6">[paper]</a>
- download IEMOCAP data from its original web-page (license agreement is required)


### [preprocessed-data schema (our approach)]
- <a href="https://forms.gle/4qV4BgXDMz4UoYxe8">Get the preprocessed dataset [application link]</a>
	>If you want to download the "preprocessed dataset," please ask the license to the IEMOCAP team first.
- for the preprocessing, refer to codes in the "./preprocessing"
- We cannot publish ASR-processed transcription due to the license issue (commercial API), however, we assume that it is moderately easy to extract ASR-transcripts from the audio signal by oneself. (we used google-cloud-speech-api)

- Format of the data for our experiments:<br>
	> MFCC : MFCC features of the audio signal (ex. train_audio_mfcc.npy) <br>
	[#samples, 750, 39] - (#sampels, sequencs(max 7.5s), dims) <br>

	> MFCC-SEQN : valid lenght of the sequence of the audio signal (ex. train_seqN.npy)<br>
	[#samples] - (#sampels) <br>
	
	> PROSODY : prosody features of the audio signal (ex. train_audio_prosody.npy) <br>
	> [#samples, 35] - (#sampels, dims) <br>
	
	> TRANS : sequences of trasnciption (indexed) of a data (ex. train_nlp_trans.npy) <br>
	[#samples, 128] - (#sampels, sequencs(max)) <br>

	> LABEL : targe label of the audio signal (ex. train_label.npy) <br> 
	[#samples] - (#sampels) <br>
    

### [source code]
- repository contains code for following models
	 > Audio Recurrent Encoder (ARE) <br>
	 > Text Recurrent Encoder (TRE) <br>
	 > Multimodal Dual Recurrent Encoder (MDRE) <br>
	 > Multimodal Dual Recurrent Encoder with Attention (MDREA) <br>

----------

### [Training]
- refer "reference_script.sh"
- fianl result will be stored in "./TEST_run_result.txt" <br>


----------


### [Reference]
- Please cite our paper, when you use our code | model | dataset
  >   @inproceedings{yoon2018multimodal, <br>
  >   title={Multimodal Speech Emotion Recognition Using Audio and Text}, <br>
  >   author={Yoon, Seunghyun and Byun, Seokhyun and Jung, Kyomin}, <br>
  >  booktitle={2018 IEEE Spoken Language Technology Workshop (SLT)}, <br>
  >   pages={112--118}, <br>
  >   year={2018}, <br>
  >   organization={IEEE} <br>
  > }
