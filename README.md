# LightGBM_LuWang
Version: Python 3.8 
IDE: Jupyter
We recommend the readers to download Anaconda (https://www.anaconda.com/download/). The install time is typically less than one hour.
**********************************************
Library:
numpy, pandas, lightgbm, sklearn, matplotlib

Function：
main_lgb_stage1.ipynb and main_lgb-Stage2.ipynb reads the training dataset to train the LightGBM model and the optimal model is then applied to the application dataset to predict zircon from the carbonatite-kimberlite-alkaline silicate rocks. main_lgb_stage1.ipynb conducts a binary classification which distinguishes zircon from all kinds of either alkaline rocks (label 1) or subalkaline rocks (label 0). main_lgb-Stage2.ipynb conducts a multiclass classification, which further classifies the predicted source rocks with label 1 into carbonatites (label 1), kimberlites (label 2), and other alkaline silicate rocks (label 3). 

Data：
application data.xlsx: The application dataset containing detrital zircons with unknown source rock types.
training_raw data_1.xlsx: The training dataset containing positive samples (zircon from carbonatites-kimberlites-alkaline silicate rocks).
training_raw data_0.xlsx: The training dataset containing negative samples (zircon from subalkaline rocks).

Parameters:
main_lgb_stage1.ipynb: test_size = 0.3; random_state = 42; objective = binary; metric = binary_error; learning_rate = 0.05; subsample = 0.8; subsample_freq = 3; num_iterations = 2000; is_unbalance = True 
main_lgb_stage2.ipynb: test_size = 0.3; random_state = 42; objective = multiclass; metric = multi_error; learning_rate = 0.01; min_child_samples = 5; max_depth = 7; num_class = 6; is_unbalance = True

Output File:
-res_stage1:
training data_lable: The merged dataset of positive and negative samples with labels (0, 1).
training_set: 70% of the training dataset (total compiled igneous zircon) used for training the model.
test_set: 30% of the training dataset (total compiled igneous zircon) used for test the predictive performance of the model.
feature importance: The importance score of the selected features in the binary classification.
ks: The Kolmogorov-Smirnov score of the selected features.
application data_label: The predicted result of the application dataset with labels (0, 1).
-res_stage2:
train: 70% of the training dataset (only alkaline igneous zircon) used for training the model.
test: 30% of the training dataset (only alkaline igneous zircon) used for test the predictive performance of the model.
feature importance: The importance score of the selected features in the multiclass classfication.
valid: The predicted result of the application dataset (zircon with label 1 in the initial binary classification) with labels (1, 2, 3).

Notice:
Please run the main_lgb_stage1.ipynb and main_lgb-Stage2.ipynb in turn.
You can change the filenames and parameters as you need.
It would take more than 2 hours for running the complete code on a "normal" computer. 
