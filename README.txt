This was modified from https://github.com/minerva-ml/open-solution-mapping-challenge

Instructions to Run Machine Learning Lab's Solution to the CrowdAI Challenge
1. Colone this repository

2. In the terminal
$ cd mapping-challenge
Then, install requirements using 
$ pip install -r requirements.txt

3. Download all dataset from CrowdAI website and put them in the data folder. After decompressing, the 3 folders should be named test_image, val and train by default. 

4. Register for an account on https://neptune.ml

(4.5.) Configure parameters in neptune.yaml

5. Prepare the data: 
$ neptune experiment run main.py -- prepare_metadata \
--train_data \
--valid_data \
--test_data

After several hours, there should be a new CSV file in the meta folder under data. Note that if you choose to change the location of the data folder, you will have to change the paths in Neptune.yaml

6. Prepare the eroded masks:
$ neptune experiment run main.py -- prepare_masks -d

After several hours, there should be a new folder called masks_overlayed_erode_30 in the data folder. 

7. Run the experiment: 
$ neptune experiment run main.py "--" train_evaluate_predict --pipeline_name unet --chunk_size 5000