# Project Internship Biosignal Processing and Modeling (PBSM)
Team: Pam, Natascha, Oscar, Alyona. Final project
# Description

This project explores the development and application of a Brain Computer Interface (BCI) system utilizing Electroencephalogram (EEG) technology to enable direct communication between the brain and external devices. Specifically, it focuses on employing non-invasive, cost-effective EEG to read and process the brain's electrical signals, with a particular emphasis on detecting the P300 event-related potential—a positive deflection in EEG data occurring approximately 300 milliseconds after stimulus presentation. The primary application demonstrated in this study is a model trained to identify P300 signals from EEG data, allowing individuals, particularly those unable to use their limbs due to neurological or muscular conditions, to dial emergency numbers by simply focusing on displayed digits. The paper details the paradigm creation, tool utilization, data pre-processing, classification methodologies, and training processes that culminated in achieving approximately 96.667% accuracy in signal detection, showcasing the potential of BCI systems in enhancing interaction with technology for patients with severe mobility impairments.

# For a complete description of the application refer to [PBSM_final_project.pdf](Deliverable/PBSM_final_project.pdf)

# Steps to use the Brain Machine Interface in the Speller Matrix application in the p300 paradigm

## Offline
### Data collection for offline training

- Step 1: Start smarting, you can follow the steps in this [video](https://www.youtube.com/watch?v=w4Qn58kp0_4). The steps to install and run the BlueSoleil application and Smarting Streamer 3.0 are not covered in this tutorial, please refer to the official documentation or follow the instructions in section 6 of Tutorial-Setting_Up.pdf.

- Step 2: Inside the folder [offline_experiment](Deliverable/offline_experiment) there are three speller matrix experiments:
  - speller_matrix_training_noFace.py: Only numbers are highlighted by changing their color to white when selected.
  - speller_matrix_training_face.py: The face of a famous person overlaps the selected numbers.
  - speller_matrix_training_familiar_face.py: A familiar face overlaps the selected numbers.

  According to our results, experiment 3 provides the best set-up for the speller matrix application. Choose one experiment and run it until line 42.

  **Note: Within this folder you will also find previously collected data. If you do not want to collect new data and prefer to use the sample data instead, please skip to step 7. However, keep in mind that for a better performance of the program it is preferable to adjust the classifier for each user following the steps in this section.**

- Step 3: Run the LabRecorder.exe application, select the stream coming from the Smarting device and speller_matrix_markers_training. Fill in the fields according to the specifications of your experiment (session, subject, age, etc) and press start.

- Step 4: Run the chosen experiment from line 42 and follow the instructions on the screen.

- Step 5: Once the experiment is finished, go to the LabRecorder application and press stop.

- Copy and paste the .xdf in the [offline_pr/data](Deliverable/offline_pr/data) folder.

### Offline training

- Step 7: Run [offline_training.ipynb](Deliverable/offline_pr/offline_training.ipynb) and follow the instructions in the script.

**Note: The best features as well as the chosen training model will be saved in the folder [online_pr/trained_model](Deliverable/online_pr/trained_model). This folder already contains examples of best features and models trained for the LDA classifier for the experiments described in step 2 of the Offline section.**

## Online

- Step 1: Start smarting, you can follow the steps in this [video](https://www.youtube.com/watch?v=w4Qn58kp0_4). The steps to install and run the BlueSoleil application and Smarting Streamer 3.0 are not covered in this tutorial, please refer to the official documentation or follow the instructions in section 6 of Tutorial-Setting_Up.pdf.

  Use lines 101 and 105 to select the best features and the classifier model according to the experiments described in step 2 of the Offline section. Example: If the model was trained with the experiment: speller_matrix_training_familiar_face.py then you should use the files best_features_Familiar_Face_idx.txt (line 101) and lda_model_Familiar_Face.pkl (line 105). In addition, you should use the online experiment: speller_matrix_online_familiar_face.py (see step 3). 
  
- Step 2: Open and run the file [online_pr.py](Deliverable/online_pr/online_pr.py).

- Step 3: Inside the folder [online_pr](Deliverable/online_pr) there are three speller matrix experiments:
  - speller_matrix_online_noFace.py: Only numbers are highlighted by changing their color to white when selected.
  - speller_matrix_online_face.py: The face of a famous person overlaps the selected numbers.
  - speller_matrix_online_familiar_face.py: A familiar face overlaps the selected numbers.

   According to our results, experiment 3 provides the best set-up for the speller matrix application. Choose one experiment and run it.

- Step 4: Follow the instructions presented on the screen to choose the desired numbers through the Brain Machine Interface.

