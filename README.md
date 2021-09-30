# Mask Benchmark from QD dataset

Weaknesses:
- There is nothing "human" in generating such masks
- Masks often have sharp edges because of rough crops close to borders


##### NVidia Irregular Mask Dataset:
![NVidia Irregular Mask Dataset examples](https://raw.githubusercontent.com/karfly/qd-imd/master/readme/nvidia_imd_6_examples.png)

##### Our Irregular Mask Dataset:
![Quick Draw Irregular Mask Dataset examples](https://raw.githubusercontent.com/karfly/qd-imd/master/readme/qd_imd_6_examples.png)

## How it's generated
Our dataset is based on Quick Draw dataset (a collection of 50 million human drawings). Our hypothesis is that combination of strokes drawn by human hand is a good source of patterns for irregular masks. Here are steps for generating a single mask (default values are given in square brackets):
1. Randomly choose number of strokes for mask [*~N(4, 2)*]
2. Randomly sample strokes from Quick Draw dataset
3. For each stroke choose width (px) [*~Uniform(5, 15)*] and draw it on canvas
4. Sample upscale rate [*~Uniform(1.0, 1.5)*] and upscale canvas correspondingly
5. Make central crop of target shape [*(512, 512)*]
6. Binarize resulting mask


Quick Draw (simplified). [here](https://console.cloud.google.com/storage/browser/quickdraw_dataset/full/simplified). 

```bash
python generate_dataset.py
```
### 9.28 update on generate_dataset.py

0/1 label generation for the mask dataset
