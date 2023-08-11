# TextMaster

Current function:  
- Extract meta data of scientific literature from savedrecs files of Web of Science (`meta_wos.ipynb`).  
- Automated opinion extraction and classification for scientific literature in materials science and related fields (`demo.ipynb`).  
  
This is the source code of our proposed SSCNN system (demo version) of our Nature Nanotechnology submission "Opinion Mining by Deep Learning Methods for Maximizing Discoverability of Nanomaterials". We use `.ipynb` to show the running results directly (Click the `.ipynb` file and you will see running results of each cell. You can also set up environment in your local machine and try out our functions with your own data). Thanks for your attention. 

## Set up
1. Make sure you have python3.8 and the pip module installed. We recommend using conda environments.  
2. After git clone this repository to local machine (if you don't have git, you can also create a folder in local machine and download the files), navigate to the root folder of this repository and run `pip install --ignore-installed -r requirements.txt`. Note: if any packages fail to be installed, you may need to install those packages manually by `pip install package_name`.  
3. Stay in the root folder, manually download the models and data [test_demo.zip](https://drive.google.com/file/d/1e0OCbzQ6GjN_yDYxNhy8ynRx2I16eaCU/view?usp=sharing) and unzipped. 

## Introduction of the data directory in test_demo.zip
- 3_in_1: provide data of each topic in the mixed-topic dataset (for example, eol_driver.txt contains End-of-Life opportunity sentences) and the final version of the train/valid/test set (in .json format).
- CNN_94_95_93: trained CNN model for opinion extraction (model used in module 2)
- CNN_Attention_91: trained CNN_Attention model for opinion classification (model used in module 3)
- final_200.json: sentiment dictionary (200 words version) formed by corpus comparison
- text.txt: a tiny example text for run demo

## Introduction of code file meta_wos.ipynb  
The analysis is based on savedrecs files from Web of Science. The running results shown in this file are based on 22752 perovskite related publications. To get your own savedrecs files, you can search papers on [Web of Science](https://www.webofscience.com/wos/woscc/basic-search) by keywords and the search results should be exported as plain text files.  

We provide following functions:  
- Extract meta data as a json file 
- Visualization of publishers, journal names, publishment by year, data types, categories

## Introduction of code file demo.ipynb
The demo of our opinion mining system is composed of two parts: 
- Reproduce the results of opinion extraction and classification models
- Run opinion mining on a tiny text sample 

The two models were trained on mixed-topic dataset (EoL, perovskite, ALD).  
CNN model for opinion extraction obtained 94.21% f1-score on test set and for each category: 
| Category | F1-score |
| :--------: | :---: |
|   non-opinion   | 95.05% |
|   opinion    | 93.03% |

CNN-Attention model for opinion classification obtained 91.58% f1-score on test set and for each category: 
| Category | F1-score |
| :--------: | :---: |
|   challenge   | 77.27% |
|   opportunity    | 94.83% |

If you want to try opinion mining on your own data, please replace the content in `data/text.txt`.

## Introduction of other code
- data_aug.ipynb: SMOTE method to generate augmentation
- supervised_lexicon.ipynb: corpus comparison method
- rule_design.ipynb: modify the embedding rank of 83 materials according to the values of our designed features (experiment 1 method 1)
- .ipynb:  supervised learning algorithm (experiment 1 method 2)
- CF.ipynb: predict candidate element combinations by the transition probabilities of elements through collaborative filtering (experiment 2 method 1)
- LSTM.ipynb: predict candidate element combinations by training LSTM (experiment 2 method 2)

## Contact  
If you have any problems, please email: yuweiwan2-c@my.cityu.edu.hk 
