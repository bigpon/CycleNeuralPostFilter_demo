---
layout: default
---
This page is the demo of 
1. "A cyclical post-filtering approach to mismatch refinement of neural vocoder for text-to-speech systems" [[paper](https://arxiv.org/abs/2005.08659)] [[highlight]()] [[YouTube]()]   
  

## **Abstract**  
<p align="justify"> Building an advanced TTS system from scratch is time and resource consuming. Therefore, we propose an economical post-filtering approach for existing low-cost TTS systems. However, this approach usually suffers from two issues: 1) temporal mismatches between TTS and natural waveforms and 2) acoustic mismatches between training and testing data. To address these issues, we adopt a cyclic voice conversion (Cycle-VC) model to generate temporally matched pseudo-VC data for training and acoustically matched enhanced data for testing the proposed neural-post-filter (NPF). Because of the generality, this framework can be applied to arbitrary TTS systems. </p>

## **Acoustic mismatch**  
- Training the NPF with natural features and waveforms
- Testing the NPF with the synthetic features extracted from TTS-speech
<center><img src="res/figure/AM.svg" style="display:block;width:350px;height:240px"></center>  

## **Temporal mismatch**  
- Training the NPF with the synthetic features and natural waveforms
<center><img src="res/figure/TM.svg" style="display:block;width:350px;height:130px"></center>

## **Cycle-VC**  
- **Source**: synthetic features
- **Target**: natural features
- **Enhanced** path: synthetic -> natural conversion
- **Pseudo VC** path: natural -> synthetic -> natural conversion
<center><img src="res/figure/CycleVC.svg" style="display:block;width:560px;height:200px"></center>

## **NPF training**  
- The **temporal structures** of the pseudo VC features and natural waveforms are matched
<center><img src="res/figure/NPF_train.svg" style="display:block;width:480px;height:210px"></center>

## **NPF testing**  
- The **acoustic characteristics** of the pseudo VC and enhanced features are similar
<center><img src="res/figure/NPF_test.svg" style="display:block;width:480px;height:210px"></center>

## **Demo Sound**
- Testing with a **DNN-based** low-cost TTS

| Vocoder | Female | Male |
|:--------|:------:|:----:|
| Natural | <audio src="res/audio/lmrkt/Natural/NJ_002.wav" controls preload></audio> | <audio src="res/audio/myssi/Natural/NJ_002.wav" controls preload></audio> |
| DNN | <audio src="res/audio/lmrkt/DNN/wPF/NJ_002.wav" controls preload></audio> | <audio src="res/audio/myssi/DNN/wPF/NJ_002.wav" controls preload></audio> |
| WN (UB<sup> *1</sup>) | <audio src="res/audio/lmrkt/Natural/WN/NJ_002.wav" controls preload></audio> | <audio src="res/audio/myssi/Natural/WN/NJ_002.wav" controls preload></audio> |
| WN (AM<sup> *2</sup>) | <audio src="res/audio/lmrkt/DNN/wPF/WN/AM/NJ_002.wav" controls preload></audio> | <audio src="res/audio/myssi/DNN/wPF/WN/AM/NJ_002.wav" controls preload></audio> |
| WN (TM<sup> *3</sup>) | <audio src="res/audio/lmrkt/DNN/wPF/WN/TM/NJ_002.wav" controls preload></audio> | <audio src="res/audio/myssi/DNN/wPF/WN/TM/NJ_002.wav" controls preload></audio> |
| WN (NPF<sup> *4</sup>) | <audio src="res/audio/lmrkt/DNN/wPF/WN/NPF/NJ_002.wav" controls preload></audio> | <audio src="res/audio/myssi/DNN/wPF/WN/NPF/NJ_002.wav" controls preload></audio> |

<sup>*1. **UB**: upper bound (natural features) </sup>  
<sup>*2. **AM**: acoustic mismatch </sup>  
<sup>*3. **TM**: temporal mismatch </sup>  
<sup>*4. **NPF**: neural-post-filter </sup>  
**WN**: WaveNet vocoder

<br />  

- Testing with a **HMM-based** low-cost TTS

| Vocoder | Female | Male |
|:--------|:------:|:----:|
| Natural | <audio src="res/audio/lmrkt/Natural/NI_002.wav" controls preload></audio> | <audio src="res/audio/myssi/Natural/NI_002.wav" controls preload></audio> |
| HMM | <audio src="res/audio/lmrkt/HMM/woPF/NI_002.wav" controls preload></audio> | <audio src="res/audio/myssi/HMM/woPF/NI_002.wav" controls preload></audio> |
| WN (UB<sup> *1</sup>) | <audio src="res/audio/lmrkt/Natural/WN/NI_002.wav" controls preload></audio> | <audio src="res/audio/myssi/Natural/WN/NI_002.wav" controls preload></audio> |
| WN (AM<sup> *2</sup>) | <audio src="res/audio/lmrkt/HMM/woPF/WN/AM/NI_002.wav" controls preload></audio> | <audio src="res/audio/myssi/HMM/woPF/WN/AM/NI_002.wav" controls preload></audio> |
| WN (TM<sup> *3</sup>) | <audio src="res/audio/lmrkt/HMM/woPF/WN/TM/NI_002.wav" controls preload></audio> | <audio src="res/audio/myssi/HMM/woPF/WN/TM/NI_002.wav" controls preload></audio> |
| WN (NPF<sup> *4</sup>) | <audio src="res/audio/lmrkt/HMM/woPF/WN/NPF/NI_002.wav" controls preload></audio> | <audio src="res/audio/myssi/HMM/woPF/WN/NPF/NI_002.wav" controls preload></audio> |

<br /> 

## **Subjective Results** 
- **Mismatch refinement**: preference evaluation of speech quality
- WN w/ NPF outperforms WN w/ AM or TM   
<center><img src="res/figure/PK.png" style="display:block;width:420px;height:270px"></center> 

- **NPF performance**: MOS evaluation of speech quality   
- WN w/ NPF outperforms original low-cost TTS systems   
<center><img src="res/figure/MOS.png" style="display:block;width:420px;height:270px"></center>  

<br /> 

## **Relative distances on MCD-plane** 
- **DNN-based** low-cost TTS  
<center><img src="res/figure/MCD_DNN.png" style="display:block;width:300px;height:300px"></center> 

- **HMM-based** low-cost TTS   
<center><img src="res/figure/MCD_HMM.png" style="display:block;width:300px;height:300px"></center>  

- MCD of synthetic to natural is high -> natural and synthetic features are very different  

- MCD of enhanced to pseudo VC is much lower -> pseudo VC and enhanced features are similar   

<br /> 
[Home](https://bigpon.github.io/)

<br />  
<br />  