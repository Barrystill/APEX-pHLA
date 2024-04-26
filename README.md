# APEX-pHLA: A novel method for accurate prediction of the binding between exogenous short peptides and HLA class I molecules

This is the code for "APEX-pHLA: A novel method for accurate prediction of the binding between exogenous short peptides and HLA class I molecules" paper.
The training code and test code have been uploaded. Critiques and feedback from industry professionals are welcome.

## Abstrate 
Human leukocyte antigen (HLA) molecules play critically significant role within the realm of immunotherapy due to their capacities to recognize and bind exogenous antigens such as peptides, subsequently delivering them to immune cells. Predicting the binding between peptides and HLA molecules (pHLA) can expedite the screening of immunogenic peptides and facilitate vaccine design. However, traditional experimental methods are time-consuming and inefficient. In this study, an efficient method based on deep learning was developed for predicting peptide-HLA binding, which treated peptide sequences as linguistic entities. It combined the architectures of textCNN and BiLSTM to create a deep neural network model called APEX-pHLA. This model operated without limitations related to HLA class I allele variants and peptide segment lengths, enabling efficient encoding of sequence features for both HLA and peptide segments. On the independent test set, the model achieved Accuracy, ROC_AUC, F1, and MCC is 0.9449, 0.9850, 0.9453, and 0.8899, respectively. Similarly, on an external test set, the results were 0.9803, 0.9574, 0.8835, and 0.7863, respectively. These findings outperformed fifteen methods previously reported in the literature. The accurate prediction capability of the APEX-pHLA model in peptide-HLA binding might provide valuable insights for future HLA vaccine design.

## Environment
We train the code in the following conda environment

build the environment as follow
```shell
conda create -n APEX-pHLA python=3.7
conda activate APEX-pHLA
```
Please install the relevant packages use 'pip'
```shell
python==3.7
tensorflow==2.10.0
pandas==0.25.3
keras==2.6.0
sklearn==0.0
numpy==1.19.5
```

## Step 2. train the data
Run the following command in the terminal
```shell
python train.py --task fold0 --test_data val_data_fold0
```
When using the training code, you may encounter a situation where the CUDA version is incompatible and unable to utilize the GPU. This could be related to internal modifications within the TensorFlow package. You can try reinstalling a compatible CUDA version and TensorFlow version, or downgrade the CUDA version.

## Step 3. Test the model 
Run the following command in the terminal
```shell
python test.py --ckpt_path ckpt/fold0.h5 --test_file independent_set
# output the metrics as accuracy,AUC,F1,and MCC
```

We have also provided code for the ablation study section. You can use this code to conduct ablation experiments and testing. The training set, independent test set, and extended test set have all been annotated and are included in the data folder. You can use this data to complete the utilization and trial of a deep learning model.

