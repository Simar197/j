## Training Setup for Sundanese Dataset

### Sample images
![Sample sundanese 1](../readme_imgs/CB-3-18-90-7.jpg)

![Sample sundanese 2](../readme_imgs/CB-3-18-90-12.jpg)

### Dataset
```
pip install gdown
gdown 1bYqKGPeqZ0XpFJS6d9X8rKk078ESTUHn
mkdir data/
mv SD.zip data/
unzip data/SD.zip -d data/SD/ 
rm -rf data/SD.zip
```

or 

Download directly from [here](https://drive.google.com/file/d/1bYqKGPeqZ0XpFJS6d9X8rKk078ESTUHn/view?usp=sharing). Follow the below data hierarchy after unzipping it.

```
data
├── SD
│   ├── SD_Train
│   │   ├── images
│   │   ├── binaryImages
│   │   ├── SD_TRAIN.json
│   ├── SD_Test
│   │   ├── images
│   │   ├── binaryImages
│   │   ├── SD_TEST.json

```

### Experiment Json Configuration
- Refer: [SD_exp1_Configuration.json](../SD_exp1_Configuration.json)

### Data Preparation for training
- Train Data
```bash
python datapreparation.py \
 --datafolder '.data/' \
 --outputfolderPath '.data/SD_train_patches' \
 --inputjsonPath '.data/SD/SD_Train/SD_TRAIN.json' \
 --binaryFolderPath '.data/SD/SD_Train/binaryImages'
```
- Validation/Test Data
```bash
python datapreparation.py \
 --datafolder '.data/' \
 --outputfolderPath '.data/SD_test_patches' \
 --inputjsonPath '.data/SD/SD_Test/SD_TEST.json' \
 --binaryFolderPath '.data/SD/SD_Test/binaryImages'
```

### Training Binarisation Branch
```bash
python train.py --exp_json_path 'SD_exp1_Configuration.json' --mode 'train' --train_binary
```

### Training Scribble Branch
```bash
python train.py --exp_json_path 'SD_exp1_Configuration.json' --mode 'train' --train_scribble
```
