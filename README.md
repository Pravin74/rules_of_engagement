# Folder hierarchy for egocentric projects

```
DATASET_NAME(GTEA) /  codes /ego_action_recognition  / rgb_cnn.py
                                                        rgb_lstm.py
                                                        flow_cnn.py
                                                        flow_lstm.py
                                                        fused_lstm.py
                                                        utils/ folder.py
                                                                create_train_test_cnn.py
                                                                create_train_test_lstm.py
                                                                extract_rgb_cnn_features.py
                                                                extract_flow_cnn_features.py
                                                                conf_matrix_to_res.py
                                                                confusion_matrix.py
                                                        config/ GTEA.py
                                                                EGTEA.py
                                                                UTE.py
                                                                ADL.py
                                                                EPIC.py
                                                                HUJI.py
                                                                Kitche.py
                                                                PC.py
                                                                PlUMBING.py
                            /ego_activity_recognition / activity.py
                                                        rnn_function.py
                                                        rnn_modules.py

                            /fusionseg_for_flow/*
                    / dataset  /cnn_features/         
                                rgb_10x10x2048_features/  
                                flows/                
                                rgb_2048_features/        
                                gtea_labels/          
                                stab_pngs/                
                                gtea_labels_cleaned/  
                                pngs/
                                train_flow_cnn.csv     
                                test_flow_cnn.csv         
                                train_rgb_lstm.csv
                                train_rgb_cnn.csv                      
                                test_rgb_cnn.csv
                                test_rgb_lstm.csv
                    /weights /the weight file should always contains all hyperparameters and file name along with rgb/flow, cnn/lstm keywords, make it as explicit as possible
```
# Folder structure for staqu ocr
```
    staqu_ocr / codes / different gits, different methods each have their folder name
             / datasets / each dataset has its folder and everything about that dataset is inside in it for example if a dataset is named IIITH_HINDI and we have certain folders that are some preprocessed verion of this than all those verison should be inside IIITH_HINDI with clear naming that explain what those folders contain
             /wights to store weights
 ```
# Folder naming conventions
    1. Names of dataset should always be in caps
    2. Anything that is not dataset should always be in small and to seperate words use underscore(_)
    3. NEVER use 1,2,3,.. for versioning, make folder names very clear and informative
    4. For weights if using tensorflow or anything that generates multiple snapshot use directory name same as the code_folder inside weights to save all the weights/snapshots for that particualr code, e.g. crnn has weights saved at staqu_ocr/weights/crnn/*pth or *.tflean or *.caffemodel

# File naming conventions
    1. Unless until the file is a config file or holds only constanst it should never have any caps letter, only config/constant files should be named in all CAPS
    2. Use undersocre(_) to seperate words in file names
    3. Never create another version of a file named like this train.py==>train_fc1.py. If there a file is changed commit it to github before change and work on the same file, if old version is required just go to the old version

# Coding styles
    1. Always use proper indentetion and seperate coding block by lines
    2. Never write any hyperparameter or file path in the code line iteself use first lines to intialise constans or use a config file
    3. Alwasy use relative path, this will make sure that when you run same code on another machine with different dataset you don't need to find every directory and file again, just change few things on config file like ../../datasets/GTEA/pngs to ../../datasets/EGTE/pngs
    4. Try to add comments 
    5. If using pytorch use follwing code flow: (for example view https://github.com/sagarverma/ego_action_recognition)
        i) imports
        ii) hyperparams, filenames as constants if not using a constanst/config file
        iv) model defition
        iii) all other functions including train/test
        iv) dataloading
        v) model create
        vi) optimizer
        vii) criterion 
        viii) call train and/or test functions
    6. If you want to extract features write a different file don't change the model training file for that, model training file should always be used for training and testing only
    g. Always use dataloader to load data, don't write a rough code for epoching/batching, if you are not able to find a dataloader for your model, search google or ask team mates and create one

# Github versioning
    1. Always use commit major/minor changes to git.
    2. Never rush to experiments, clean code, commit changes, delete stale files.
    3. In commit message be explicit about the changes, dosen't matter how much line it takes. Write full path of files relative to project structure where changes have been made.