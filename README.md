# Trail-Level EEG Signals on Classifying Behaviroal Reaction Time and Accuracy during Perceptual Decision Making

Jenny Qinhua Sun <br />
Human Neuroscience Lab <br />
University of California, Irvine <br />

## Introduction
As humans, we constantly interact with the worl by quickly allocating attention, detecting stimuli and making decisions rapidly. Electroencephalogram(EEG), compared to other neuroimaging techniques, has high temporal resolution and thus has been widely used to investigate the neural correlates between brain signals and behavioral response. Traditionally, event-related potential (ERP) components has been a well-established measure to study human cognition, as the Signal-to-noise-ratio(SNR) are stronger when time series are obtained by averaging across individual trials and subjects. A growing body of research has focused on developing new computational apporaches to extract features from single-trial EEG and link them with behavior during decision making[1]. Among many important factors that influence our decision making process, attention plays an important role as it could preferentially faciliate the processing of task-relevant signals[2]. In the field of Brain-Computer Interfaces(BCI), such attention could be measured using signals such as N200 (or N1) and Steady-State Visual Evoked Potentional (SSVEP). N200 signals are negative peaks around 200ms post-stimulus that are associated with the onset of visual signal in evidence accumulation. SSVEPs are natural responses to visual stimulus flickering at certain frequencies. In the current project, SSVEPs would be the brain responses to 30Hz signals follwed by target stimulus and 40Hz signals followed by distractor, hence the energy at these two frequencies would accordingly represent the deployment of attention. 

The goal of the current project is to train two neural networks on trial-level EEG data, in order to see whether the model(s) could correctly predict accuracy (classfied as correct or incorrect) and reaction time (classfied as fast, medium, slow RT) within that trial.   
  
## Methods
### Task 
The current Task is a S-R Mapping Task. The subject was asked to discriminate 2.45 cpd Gabor from 2.55cpd Gabor. There were three difficulty levels, with the easiest being responding to either stimulus, the medium one being responding with one of the two buttons based on the spatial frequency, and the hardest one being responding to spatial frequency contingent on a certain orientation. However, considering the current goal of the project and the size of the dataset, we will treat all trials equally. 

### Data Preprocessing

## Results





# References 
1. Bridwell, David A., James F. Cavanagh, Anne G. E. Collins, Michael D. Nunez, Ramesh Srinivasan, Sebastian Stober, and Vince D. Calhoun. 2018. “Moving Beyond ERP Components: A Selective Review of Approaches to Integrate EEG and Behavior.” Frontiers in Human Neuroscience 12. https://doi.org/10.3389/fnhum.2018.00106.

2. 