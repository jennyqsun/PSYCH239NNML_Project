# Trail-Level EEG Signals on Classifying Behaviroal Reaction Time and Accuracy during Perceptual Decision Making

Jenny Qinhua Sun <br />
Human Neuroscience Lab <br />
University of California, Irvine <br />

## Introduction
As humans, we constantly interact with the worl by quickly allocating attention, detecting stimuli and making decisions rapidly. Electroencephalogram(EEG), compared to other neuroimaging techniques, has high temporal resolution and thus has been widely used to investigate the neural correlates between brain signals and behavioral response. Traditionally, event-related potential (ERP) components has been a well-established measure to study human cognition, as the Signal-to-noise-ratio(SNR) are stronger when time series are obtained by averaging across individual trials and subjects. A growing body of research has focused on developing new computational apporaches to extract features from single-trial EEG and link them with behavior during decision making[1]. Among many important factors that influence our decision making process, attention plays an important role as it could preferentially faciliate the processing of task-relevant signals[2]. In the field of Brain-Computer Interfaces(BCI), such attention could be measured using signals such as N200 (or N1) and Steady-State Visual Evoked Potentional (SSVEP). N200 signals are negative peaks around 200ms post-stimulus that are associated with the onset of visual signal in evidence accumulation. SSVEPs are natural responses to visual stimulus flickering at certain frequencies. More specifically, single-trial SSVEP could be beneficial for patients with severe phsyical disabilities to complete daily tasks by fixating upon the simuli of interest, and there has already been research trying to use deep learning neural network on SSVEP for classification task[3].  In the current project, SSVEPs would be the brain responses to 30Hz signals follwed by target stimulus and 40Hz signals followed by distractor, hence the energy at these two frequencies would accordingly represent the deployment of attention. The goal of the current project is to train two neural networks on trial-level EEG data, in order to see whether the model(s) could correctly predict accuracy (classfied as correct or incorrect) and reaction time (classfied as fast, medium, slow RT) within that trial. The figures below demontrate the meausre of interest.

![image info](https://github.com/jennyqsun/PSYCH239NNML_Project/blob/main/Figures/demo_n200.png)<br />
**Figure 1.** *N200 signal averging from all trials from one subject*

![image info](https://github.com/jennyqsun/PSYCH239NNML_Project/blob/main/Figures/demo_ssvep.png)<br />
**Figure 2.** *Enhanced SSVEP spectrum summing from all trials using. Top two channels represent the photocells that record the stimulus at each frequency. Bottom figure shows the corresponding power at 30Hz and 40Hz obtained from Fast Fourier Transform (FFT) of the brain signals. As 40Hz has more power than 30Hz, we would interpret it as the subject deployed more attention to the distractor flicker, relative to the target flicker.* 


## Methods
### Task 
The current Task is a S-R Mapping Task. The subject was asked to discriminate 2.45 cpd Gabor from 2.55cpd Gabor. There were three difficulty levels, with the easiest being responding to either stimulus, the medium one being responding with one of the two buttons based on the spatial frequency, and the hardest one being responding to spatial frequency contingent on a certain orientation. However, considering the current goal of the project and the size of the dataset, we will treat all trials equally. The task had a cue interval followed by a response interval (see Figure 3). During the cue interval, two SSVEP noise signals flickered on both visual fields at two different frequencies, 30Hz and 40Hz for 0.5s - 1s as a probablistic cue. During the response interval, the target stimulus occured on either side of the visual field flickering at 20Hz, with a 30Hz noise in the background (see Figure 4). Accuracy and reaction time were collected and will be used as the class for the classification task.

![header image](https://github.com/jennyqsun/PSYCH239NNML_Project/blob/main/Figures/demo_task.png)<br />
**Figure 3.** *Timeline of the Task.*<br />

![image info](https://github.com/jennyqsun/PSYCH239NNML_Project/blob/main/Figures/demo_signalnoise.png)<br />
**Figure 4.** *How the actualy noise and target stimulus looke like.*<br />


### Dataset Structure and Data Preprocessing
The dataset contained 46 subjects data in total. 12 subjects were randomly selected to be used as testing set, and 33 subjects will be used as training set as one subject was excluded due to low accuracy. Within each subject there are 360 trials in total. EEG data was collected using High Density EEG cap with 128 channels. All the EEG data was cleaned by performing Independent Component Analysis (ICA) and removed the obvious non-brain signals. A trial is identified as a goodtrial when the artifact from all 128 channels don't reach a certain threshold, and when the RT is over 300ms. Within each subject, RT was broken into tertiles and labeld as slow, medium and fast RT before the trials were stacked.The input shape of the training set then become 33 subjects x goodtrials x features = 11134 trials x features. The final Test sets has an input shape of 12 subjects x goodtrials x features = 4038 trials x features. 

#### Feature Selection
The features for each sample could be broke down to two categories: Power for each channel at certain frequencies, Time Series data with the N200 time window, and N200 parameters (latency and amplitude). The chart below shows the general framework of the input data. Table 1 below shows the feautures that were explored.

![image info](https://github.com/jennyqsun/PSYCH239NNML_Project/blob/main/Figures/input_chart.png)<br />
**Table 1.** *The inputs that were fed to the neural networks. When combining Power and N200 features for CNN, the 2x1 vector for N200 signals are treated as an extra channel.*<br />





#### Oversampling
It's worth mentioning that 0.79% of the train set trials are correct trials, and 73% of the test set trials are correct trials. In order to avoid the bias in the trainset, incorrect trials were oversampled to match up with the correct trials. This makes the final number of training sameples become 17564 trials, and the testing samples stay the same.

#### Single Trial Signal Estimate
Since single trial EEG signals could be very noise, and we plan on using each channel as a feature, instead of per channel


### The two neural networks 
#### Fully Connected Neural Network

 

## Results





# References 
1. Bridwell, David A., James F. Cavanagh, Anne G. E. Collins, Michael D. Nunez, Ramesh Srinivasan, Sebastian Stober, and Vince D. Calhoun. 2018. “Moving Beyond ERP Components: A Selective Review of Approaches to Integrate EEG and Behavior.” Frontiers in Human Neuroscience 12. https://doi.org/10.3389/fnhum.2018.00106.

2. Nunez, Michael D., Joachim Vandekerckhove, and Ramesh Srinivasan. 2017. “How Attention Influences Perceptual Decision Making: Single-Trial EEG Correlates of Drift-Diffusion Model Parameters.” Journal of Mathematical Psychology 76 (Pt B): 117–30. https://doi.org/10.1016/j.jmp.2016.03.003.

3. Kwak, No-Sang, Klaus-Robert Müller, and Seong-Whan Lee. 2017. “A Convolutional Neural Network for Steady State Visual Evoked Potential Classification under Ambulatory Environment.” PLoS ONE 12 (2). https://doi.org/10.1371/journal.pone.0172578.
