# HW 2: The pre-trained CNN, 3 Applications of image classification: KatokKatak
![image](https://user-images.githubusercontent.com/11289173/195136123-ef90c34c-7e1d-45cf-a181-8313a237b2b4.png)

Simple overview of use/purpose.

## Data Source
Collect image from google search 1,852 picture of image of budha for each day and split data using systematic ramdom using ranking of file name.

|  Class  |   Train 60%  |  Validate 20% |  Test 20% |
|---------|----------|------------|--------|
| Mon     |     115  |      37    |   39   |
| Tue     |     113  |      37    |   39   |
| Wed (m) |     112  |      38    |   39   |
| Wed (n) |     112  |      39    |   38   |
| Thu     |     125  |      42    |   40   |
| Fri     |     202  |      69    |   68   |
| Sat     |     157  |      51    |   54   |
| Sun     |     184  |      63    |   63   |


Source : see reference.xlsx


## Methodology
[Image of process flow]
0. set seed
 1111,2222,3333

1. Data Gathering and Labeling 
  1.1 Split data 60:20:20  Train Test validation
2. Image augmentation and standard preprocessing


  2.1 rescale (if there is no scaling action in model preprocessing)
  2.2 Image augmentation for train dataset
        -layers.RandomFlip("horizontal")
        -layers.RandomRotation(0.1)
        -layers.Normalization()
        -layers.RandomFlip("horizontal")
        -layers.RandomRotation(factor=0.1)
        -layers.RandomContrast(factor=0.1)
        -layers.RandomZoom(height_factor=0.2, width_factor=0.2)
  2.3 Apply standadard preprocessing for each model
4. Select 2 well-known CNN models, VGG16 and XXXXX with pre-trained imagenet  weight and remove classification layer set
  4.1 Select base model
    - VGG16 : Freeze all feature extraction layers
    - Xception : Freeze all feature extraction layers
  4.2 Added dense layers to perform clasification tasks
       - Dense512 relu -> dropout0.4-> Sense 128 relu -> dropout 0.4 -> Dense 64  Relu -> Dense 8  softmax
       - Optimizer = Adam
       - Loss function = categorical_crossentropy
       - Metric = Accuracy
![image](https://user-images.githubusercontent.com/11289173/196020339-00d0b629-ec92-4a18-ab36-70e4124f1ea4.png)

8. Train Model
  6.1 Image of Buddha
   - Image size vary by model
   - batch size vary by model
   - Epoch vary by model
   
   |   Model  | Image size | batch size | Epoch | Remark |
   |----------|------------|------------|-------|--------|
   | Xception |  299 * 299 |    16      |   300 |        |
   | VGG16    |  256 * 256 |    16      |   300 |        |
   
9. Evaluate model

### Result for each Model
Processor : Tesla T4


  |  Model | Dataset  | Records |   Lost   | Accuracy | Train Time (s) |
  |--------|----------|---------|----------|----------|----------------|
  |Xception| Train    |   1,112 |0.5210±0.01|0.8249±0.01|   13,940±964 |
  |Xception| Validate |     368 |0.9746±0.01|0.6666±0.01|       N/A    | 
  |Xception| test     |     372 |0.9908±0.03|0.6666±0.03|       N/A    | 
  | VGG16  | Train    |   1,112 |0.3363±0.04|0.8735±0.01|    1,019±8  |
  | VGG16  | Validate |     368 |1.1404±0.06|0.7446±0.01|       N/A    | 
  | VGG16  | test     |     372 |1.2113±0.15|0.7301±0.01|       N/A    |  


### Comparison



## Team Members

6410422014 (%)

6410422012 (%)

6410422019 (%) 

6410422023 (%)

6410422035 (%)

This project is a part of subject DADS7202. Data Analytics and Data Science. NIDA



## Acknowledgments

Inspiration, code snippets, etc.
* [Network Drawing tool](https://alexlenail.me/NN-SVG/AlexNet.html)
