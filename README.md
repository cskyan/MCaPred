# MCaPred:A interpretable pan-cancer model based on MoE
Mcapred is an interpretable cancer prediction tool that combines Mixture of Experts (MoE), self-attention, and cross-network methods to detect cancer using microbial genotype data. It also can get feature importance.
# Package requirement
*   torch\=\=1.9.0+cu111
*   deepctr-torch\=\=0.2.7
*   shap\=\=0.35.0
# Installation
  ```pip install -r requirements.txt```
# Organization of files
### All of the input data used for the scripts in "bin" are provided in the folder ```./data```
    TCGA Cancer            // data for pre-training
    WIS                    // data for fine-tuned and test
### The methods for training, testing, and interpretation are located in the folder ```./bin```
    config.py             // path configuration
    train.py              // for pre-training and fine-tuned
    test.py               // for cancer prediction
    get_msi.py            // save model weight
    imp.py                // calculate the feature importance
### The methods for constructing the MoE layer are located in the folder ```./layer```
### The method for model are located in the folder ```./model```
    non-fine.py          // the MCaPred-nonfine workflow
    pretrained_finetuned.py  // the MCaPred workflow
# Model training
To train MCaPred, three files are required as input including fungal features (e.g. species，gene, etc.), tumor sites information and cancer labels.
1) fungal features (required)
   
   | SampleID | Species_1 | Species_2 | ... | Species_m |  
   | ---      | ---       |    ---    | --- | ---       |  
   | Sample_1 |     0     |    2467   | ... |    7694   |
   | Sample_2 |   25600   |     0     | ... |      0    |
   | ...      |   ...   |    ...    | ... |      ...    |
   | Sample_n |  0      |    0    | ... |     0   |
   
2) Tumor labels (required)

   | SampleID |    label   |  
   | ---      | ---       |    
   | Sample_1 |     0     |   
   | Sample_2 |  1        |    
   | ...      |   ...   |    
   | Sample_n |  1      |

3) tumor sites (required)
   | SampleID |    primary_site  |  
   | ---      | ---       |    
   | Sample_1 |     1     |   
   | Sample_2 |  2      |    
   | ...      |   ...   |    
   | Sample_n |  3    |
# Classfication
Then you can run the ```pretrained_finetuned.py``` or ```non-fine.py``` files to obtain the results of five-fold cross-validation.
# Contact
All problems please contact   
Dongmei He  Email：hedongmei@hainanu.edu.cn  
Shankai Yan Email: skyan@hainanu.edu.cn
