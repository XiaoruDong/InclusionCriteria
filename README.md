# InclusionCriteria
Instruction Creator: Xiaoru Dong, Linh Hoang <br/>
Date preparation: 12-14-2018 <br/>
Manuscript working title: Machine classification of inclusion criteria from Cochrane systematic reviews <br/>
Manuscript authors: Xiaoru Dong, Jingyi Xie, Linh Hoang, and Jodi Schneider <br/>

# INSTRUCTIONS

## Description:
These instructions describe the steps needed to replicate the results in the manuscript. There are 2 main sections:
1. Python program: Steps to run the Python script. Python is used to generate features and to create the Weka input files corresponding to 3 feature extraction and selection approaches that we implemented in this study: 
	- Features generated by the bag of words feature extraction strategy.
	- Features selected by the information gain feature selection strategy. 
	- Features selected by a manual analysis feature selection strategy.
2. Weka: Steps to run Weka to build the classifiers using three algorithms, NaiveBayes, Random Forest and J48. 

## 1. Python program:
- Programming Language: Python (version 3.0)

- Please make sure that you have the following programs on your machine in order to run the script:
  - Python 3.0: https://www.python.org/downloads/
  - Jupyter Notebook: http://jupyter.org/install 

- Please follow these steps in order to run the Python script:
  - Step 1: Download the source code from the GitHub site: https://github.com/XiaoruDong/InclusionCriteria/blob/master/code_classification_fall2018.ipynb 

  - Step 2: Download the input file “Inclusion_Criteria_Annotation.csv” (one of the study’s data files), which is available at: https://doi.org/10.13012/B2IDB-5958960_V1  . Note where you store the file.

  - Step 3: Open the source code in Jupyter Notebook. 

  - Step 4: Change the “path” variable in the source code to the path of your own folder where you stored the input file. 

  - Step 5: Run the whole script to get all of the output files.

  - Step 6: Check the output files, which will be in the same folder where you stored the input file. There should be 7 output files: <br/>
   --> 2 data files (they are 2 out of 5 data files that we deposited and reported in the manuscript):<br/>
   “AllWords.csv”: list of all words (features) generated by Bag of words feature extraction strategy. <br/>
   "WordsSelectedByInformationGain.csv”: list of words (features) selected by Information Gain feature selection strategy. <br/>
   --> 3 Weka input files (which will be used to run classifiers in Weka later): <br/>
   “AllWords_weka_input.arff”: Weka input file to run classifiers with “All words” features. <br/>
   “WordsSelectedByInformationGain_weka_input.arff”: Weka input file to run classifiers with “Words selected by Information Gain” features. <br/>
   “ManualAnalysis_Words_weka_input.arff”: Weka input file to run classifiers with “Words selected by Manual Analysis” features. <br/>
   --> 2 temporary output files: <br/>
   “AllWord_Noredundant.csv”: a temporary file that contains a list of words after eliminating words with the same meanings <br/>
   “AllWord_Noredundant_weka_input.arff”: Weka input file to the Information Gain feature selection. <br/>
- **Notes** 
  - The other data file which is also reported in the manuscript, named “WordSelectedByManualAnalysis.csv” was created manually, not generated by the Python script. Therefore, it is not in the list of output files. <br/>
  - The two output files: “AllWord_Noredundant.csv” and “AllWord_Noredundant.arff” are considered as temporary files and not reported in the manuscript because they are just other versions of “AllWords” when words with the same meaning were eliminated. We used them as the input for Weka to run Information Gain feature selection, not for running classifiers.  


## 2. Weka program:

- Please make sure that you have Weka on your machine in order to implement the classifiers: https://www.cs.waikato.ac.nz/ml/weka/downloading.html 

- Steps to run Weka:
  - Step 1: Open Weka on your machine, select “Explorer” mode. 
  - Step 2: On the “Preprocess” tab: <br/>
  --> Click “Open file” and select the Weka input file that you want to implement classification with. For example: if you want to implement a classifier with all features, select the “AllWords_weka_input.arff” Weka input file as shown in the screenshot below. <br/>
  ![1](https://user-images.githubusercontent.com/34040989/50197129-6aa17300-030b-11e9-9180-1f0baa518fa3.png) <br/>
  --> Click “All” to choose all of the words and use them as features to train the classifier as shown in the screenshot below. <br/>
  ![2](https://user-images.githubusercontent.com/34040989/50197245-e00d4380-030b-11e9-9bb6-1f9fa53a6d02.png) <br/>
  - Step 3: On the “Classify” tab: <br/>
  --> Click “Choose” to select the algorithm that you want to run. For example: if you want to run a classifier using “Random Forest” algorithm, select RandomForest as shown in the screenshot below: <br/>
  ![3](https://user-images.githubusercontent.com/34040989/50197249-e3083400-030b-11e9-844d-c7e4254a5a64.png) <br/>
  --> Click “Percentage split” in the “Test options” and put 90% (this means we want to get 90% of our data set for training, 10% for testing). <br/>
  --> Click “Start” to run the classifier: <br/>
  ![4](https://user-images.githubusercontent.com/34040989/50197252-e56a8e00-030b-11e9-8f5f-cdf8304ab4ea.png) <br/>
  - Step 4: Get the classifier results. Three measurements were reported in our manuscript: Precision, Recall and F-Measure as shown in the screenshot below. <br/>
  ![5](https://user-images.githubusercontent.com/34040989/50197255-e7cce800-030b-11e9-9fb0-8a062e72e822.png) <br/>
- **Notes** 
  - For each Weka input file that we generated from the Python program section and each algorithm (Random Forest, Naïve Bayes, J48), we built one classifier. Therefore, in total, we implemented 9 classifiers as reported in detail in the manuscript. 
  - We also used Weka to run Information Gain feature selection. To do so: <br/>
  --> On the “Select attributes” tab: <br/>
  Click “Choose” and select “InfoGainAttributeEval” as shown in the screenshot below. <br/>
  ![6](https://user-images.githubusercontent.com/34040989/50197256-e8fe1500-030b-11e9-84e8-2b842452cc2d.png) <br/>
  Click “Start” to run the Information Gain feature selection. <br/>
  --> Weka generated a list of informative words selected by Information Gain feature selection strategy. We then used the python script (above) to generate the data file “WordsSelectedByInformationGain.csv” and the Weka input file “WordsSelectedByInformationGain_weka_input.arff” accordingly. <br/>


**For any questions about the instruction, please contact: <br/>
Linh Hoang - lhoang2@illinois.edu.**
