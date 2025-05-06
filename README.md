# Time-Series Circula Knitting Dataset, 
First Edition of the Circula Knitting Dataset
— Intelligent Systems Software Laboratory, National Central University, Taiwan

## Introduction to the First Edition of the Circula Knitting Dataset
The first edition of the Circula Knitting Dataset has been compiled and open-sourced by the Intelligent Software Systems Laboratory at National Central University, Taiwan. It includes three types of knitted fabrics. The dataset consists of 5422 training images and 67835 test images, with image resolutions of 800x640 and 400x320.

## Dataset Characteristics
### Cutline Characteristics
To facilitate precise cutting after production, circular knitting machines incorporate two missing needles at fixed positions to form cutlines. These cutlines are an intentional part of the design, serving as guidelines for fabric cutting rather than defects. However, these cutlines closely resemble common defects, such as vertical line defects (V-line). Therefore, distinguishing cutlines from actual defects is a critical challenge in real-time defect detection.

![img_3.png](img_3.png)
defect-free sample image

### Illumination Characteristics
Since the camera lacks a color sensor, the captured images are strongly affected by lighting conditions. As the camera can only capture grayscale information, the same fabric may appear in different shades under varying lighting conditions. Hence, accurately distinguishing between normal and defective images across different lighting levels is another key challenge in real-time defect detection.
![img_5.png](img_5.png)

### Periodicity Characteristics
The periodicity of images in different datasets may vary. Periodicity refers to the number of images between the occurrences of two consecutive cutlines. In the Circula Knitting Dataset, this value ranges from 60 to 300.

For example, periodicity = 60:
![img_7.png](img_7.png)

### Defect Characteristics
The dataset includes a wide range of defect types, including common defects such as linear defects, point defects, and medium-sized holes. Additionally, it contains rare large-scale defects and defects that appear alongside cutlines in the same image.
![img_6.png](img_6.png)

Defect sample image

## Dataset Structure
The dataset includes three different knitted fabric textures, labeled as Texture 1, Texture 2, and Texture 3. These textures are further divided based on lighting conditions, resulting in six datasets:
![img_10.png](img_10.png)

## Training and Testing Data Splits
Each testure has one training dataset and several testing datasets.

The test images are collected sequentially to reflect the dynamic nature of real-world industrial processes. The table below provides a detailed information of each texture:

### Dataset Summary for texture1

| train/test | Dataset Name        |Period|Illumination|Normal Samples|defect Samples|cutline samples|total samples| Note            |
|------------|---------------------|------|------------|-------------|--------------|----------------|-----------|----------------------|
| train      | 243_2_0407          | 170  | 30         | 1733        | 0            | 74             | 1807      |                      |
| test       | 243_2_0411          | 170  | 30         | 1732        | 0            | 75             | 1807      |                      |
| test       | 243_2_0411_2        | X    | 30         | 0           | 352          | 13500          | 13852     | culine/defect only   |
| test       | 1129_02_00          | 130  | 70         | 191         | 121          | 68             | 380       |Not continuous data   |
| test       | 243_1_20210318_1    | 170  | 110        | 15749       | 0            | 682            | 16431     |                      |
| test       | 243_1_20210318_2    | 170  | 110        | 17838       | 0            | 682            | 18520     |                      |
| test       | 1065_1              | 500  | 100        | 213         | 198          | 213            | 624       | Extremely large period|
| test       | 243_1_00            | 170  | 110        | 173         | 173          | 278            | 624       | Not continuous data |
| test       | 1065_1_00           | X    | 110        | 0           | 404          | 237            | 641       | Not continuous data  |
| test       | 1129_1_0407_01      | 130  | 70         | 16          | 0            | 14             | 30        |                      |
| test       | 1129_1_0407_02      | 230  | 90         | 144         | 0            | 215            | 359       |                      |
| test       | 1129_1_0407_03      | 230  | 90         | 987         | 0            | 494            | 1481      |                      |
|     SUM    |                     |      |            | **41219**   | **1087**     | **15618**      | **57924** |                      |

### Dataset Summary for texture2

| train/test | Dataset Name | Period | Illumination | Normal Samples | defect Samples | cutline samples | total samples | Note |
| ---------- | ------------ | ------ | ------------ | -------------- | ----------------- | --------------- | ------------- | ---- |
| train      | 839\_1\_0706 | 170    | 170          | 1727           | 0                 | 81              | 1808          |      |
| test       | 839\_2       | 170    | 70           | 498            | 0                 | 21              | 519           |      |
| test       | 839\_1\_0705 | 170    | 170          | 455            | 0                 | 18              | 473           |      |
| test       | 839\_1\_0712 | 170    | 170          | 1733           | 0                 | 74              | 1807          |      |
| **SUM**    |              |        |              | **4413**       | **0**             | **194**         | **4607**      |      |

### Dataset Summary for texture3

| train/test | Dataset Name      | Period | Illumination | Normal Samples | defect Samples | cutline samples | total samples | Note                   |
| ---------- | ----------------- | ------ | ------------ | -------------- | ----------------- | --------------- | ------------- | ---------------------- |
| train      | 1480\_1\_0728\_25 | 200    | 170          | 1729           | 0                 | 78              | 1807          |                        |
| test       | 1480\_2\_1        | 130    | 40           | 291            | 0                 | 12              | 303           |                        |
| test       | 1480\_2\_0812     | 130    | 40           | 1549           | 0                 | 73              | 1622          |                        |
| test       | 1480\_2\_0906     | 130    | 40           | 1461           | 0                 | 65              | 1526          |                        |
| test       | 1480\_2\_2        | 230    | 40           | 4099           | 0                 | 191             | 4290          | Extremely large period |
| test       | 1480\_1\_0728\_15 | 300    | 170          | 1052           | 75                | 51              | 1178          |                        |
| **SUM**    |                   |        |              | **10181**      | **75**            | **402**         | **10726**     |                        |


## File Structure
The Circula Knitting Dataset (CKD-1) folder contains three fabric types: Texture 1, Texture 2, and Texture 3. These are placed in three separate directories, each named accordingly. The overall structure is as follows:
![img_8.png](img_8.png)

Each knitted fabric dataset includes two subdirectories: train (training set) and test (test set). The training set contains defect-free images and periodic cutline images, stored in the defect-free folder. Corresponding ground truth defect masks are stored in the groundtruth folder. The test set includes periodic cutline images (circular folder) and ground truth annotations. The test set consists of defect-free images, periodic cutline images, and defective samples (defect folder).

For example, the file structure of Texture 1 is shown below:

![img_9.png](img_9.png)

## Download

To be announced.
