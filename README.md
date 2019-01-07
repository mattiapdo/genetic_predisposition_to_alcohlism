# README

The data folder for this project is here

https://archive.ics.uci.edu/ml/machine-learning-databases/eeg-mld/

I downloaded the small dataset `smni_eeg_data.tar.gz`

If you extract all the files (subdirectories contain compressed files also) is more or less 20 Mb.. so when you clone the repository it may take a bit because here they are already extracted.

**To do list:**

- load data into python
- get a clue about how the dataset is logically structured
- get a clue about how to do signal reconstruction
- get a clue about how to set up the classification task



We have to somehow classify the signals in the end according to if there is a predisposition to alcohol or something else and that we can perform signal reconstruction.



## Data Type

 Multiple electrode time series EEG recordings of control and alcoholic subjects.    

## Abstract

 This data arises from a large study to examine EEG correlates of genetic  predisposition to alcoholism. It contains measurements from 64  electrodes placed on the scalp sampled at 256 Hz (3.9-msec epoch) for 1  second. 

##  Sources

####  Original Owner

```
Henri Begleiter
Neurodynamics Laboratory, 
State University of New York Health Center
Brooklyn, New York
```

####  Donor

```
Lester Ingber
POB 06440 Sears Tower
Chicago, IL 60606
ingber@ingber.com
```

Date Donated: 

 October 13, 1999     

##  Data Characteristics

 This data arises from a large study to examine EEG correlates of genetic  predisposition to alcoholism. It contains measurements from 64  electrodes placed on subject's scalps which were sampled at 256 Hz  (3.9-msec epoch) for 1 second. 

There were two groups of subjects: alcoholic and control. Each  subject was exposed to either a single stimulus (S1) or to two stimuli  (S1 and S2) which were pictures of objects chosen from the 1980  Snodgrass and Vanderwart picture set. When two stimuli were shown, they  were presented in either a matched condition where S1 was identical to  S2 or in a non-matched condition where S1 differed from S2.  

 Shown here are example plots of a [ control](https://archive.ics.uci.edu/ml/machine-learning-databases/eeg-mld/control.gif) and [ alcoholic](https://archive.ics.uci.edu/ml/machine-learning-databases/eeg-mld/alcoholic.gif) subject. The plots indicate voltage, time, and channel and are averaged over 10 trials for the single stimulus condition.   

 There were 122 subjects and each subject completed 120 trials  where different stimuli were shown. The electrode positions were located  at standard sites (Standard Electrode Position Nomenclature, American  Electroencephalographic Association 1990).  Zhang et al. (1995)  describes in detail the data collection process.      

## Data Format

 There are three versions of the EEG data set.   

#### The Small Data Set

 The small data set (smni97_eeg_data.tar.gz) contains data for the 2  subjects, alcoholic a_co2a0000364 and control c_co2c0000337. For each of  the 3 matching paradigms, c_1 (one presentation only), c_m (match to  previous presentation) and c_n (no-match to previous presentation), 10  runs are shown.   

#### The Large Data Set

 The large data set (SMNI_CMI_TRAIN.tar.gz and SMNI_CMI_TEST.tar.gz)  contains data for 10 alcoholic and 10 control subjects, with 10 runs per  subject per paradigm. The test data used the same 10 alcoholic and 10  control subjects as with the training data, but with 10 out-of-sample  runs per subject per paradigm.   

#### The Full Data Set

 This data set contains all 120 trials for 122 subjects. The entire set of data is about 700 MBytes.     

 NOTE:  There are 17 trials with empty files in co2c1000367. Some trials have "err" notices, e.g., search/grep for "err" and see "S2 match err" or "S2 nomatch err" etc.  

#### File Format

 Each trial is stored in its own file and will appear in the following format.  

```
# co2a0000364.rd
# 120 trials, 64 chans, 416 samples 368 post_stim samples
# 3.906000 msecs uV
# S1 obj , trial 0
# FP1 chan 0
0 FP1 0 -8.921
0 FP1 1 -8.433
0 FP1 2 -2.574
0 FP1 3 5.239
0 FP1 4 11.587
0 FP1 5 14.028     
...
```

 The first four lines are header information. Line 1 contains the  subject identifier and indicates if the subject was an alcoholic (a) or  control (c) subject by the fourth letter. Line 4 identifies the matching  conditions: a single object shown (S1 obj), object 2 shown in a  matching condition (S2 match), and object 2 shown in a non matching  condition (S2 no-match).  

 Line 5 identifies the start of the data from sensor FP1. The  four columns of data are: the trial number, sensor position, sample  number (0-255), and sensor value (in micro volts).     

## Past Usage

 X.L. Zhang, H. Begleiter, B. Porjesz, W. Wang, and A. Litke. (1995).  "Event related potentials during object recognition tasks".  Brain Research Bulletin. Volume 38. Number 6. Pages 531-538. 

##  Acknowledgements, Copyright Information, and Availability

There are no usage restrictions on this data.  

Acknowledgments for this data should made to Henri Begleiter at the Neurodynamics Laboratory at the State University of New York Health Center at Brooklyn.  

 Plots are courtesy of Roger Gabriel.   

## References and Further Information

 L. Ingber. (1997). [Statistical mechanics of neocortical interactions: Canonical momenta indicators of electroencephalography](http://www.ingber.com/smni97_cmi.ps.gz). Physical Review E. Volume 55. Number 4. Pages 4578-4593.  

 L. Ingber. (1998).  [Statistical mechanics of neocortical interactions: Training and testing canonical momenta indicators of EEG](http://www.ingber.com/smni98_cmi_test.ps.gz). Mathematical Computer Modelling. Volume 27. Number 3. Pages 33-64.  

 J. G. Snodgrss and M. Vanderwart. (1980). "A standardized set of 260  pictures: norms for the naming agreement, familiarity, and visual  complexity." Journal of Experimental Psychology: Human Learning and  Memory. Volume 6. Pages 174-215. 



# Compressed sensing

Guideline at http://www.pyrunner.com/weblog/2016/05/26/compressed-sensing-python/  - **Reconstruction of a Simple Signal**

Required libraries: 

- `scipy`

- `numpy`

- `cvxpy`: if you use Python 3 you must use pip: `pip install cvxpy`

  or:

   `conda create -n env_py2 python=2.7 ; activate env_py2; conda install notebook ipykernel; ipython kernel install --user` 

  `conda install -n env_py2 scipy numpy`

  ```
  conda install -n env_py2 -c conda-forge lapack
  conda install -n env_py2 -c cvxgrp cvxpy
  ```




