# Learning on Compressed Output (LoCO)
### Accepted to CVPR 2020

This repo contains the code related to the paper [Compressed Volumetric Heatmaps for Multi-Person 3D Pose Estimation](https://arxiv.org/abs/2004.00329) accepted to CVPR 2020 with the instructions for training and testing our models on the JTA dataset. I will add code and models for Panoptic and Human3.6m soon.


## Some Results
<table>
  <tr>
    <th>Input</th>
    <th>Prediction</th>
  </tr>
  <tr>
    <th><img src=imgs/sample_1.jpg width=960></th>
    <th><img src=imgs/sample_1.gif width=960></th>
  </tr>
  <tr>
    <th><img src=imgs/sample_2.jpg width=960></th>
    <th><img src=imgs/sample_2.gif width=960></th>
  </tr>
  <tr>
    <th><img src=imgs/sample_3.jpg width=960></th>
    <th><img src=imgs/sample_3.gif width=960></th>
  </tr>
  <tr>
    <th><img src=imgs/sample_5.jpg width=960></th>
    <th><img src=imgs/sample_5.gif width=960></th>
  </tr>
  <tr>
    <th><img src=imgs/sample_4.jpg width=960></th>
    <th><img src=imgs/sample_4.gif width=960></th>
  </tr>
</table>


## Quick Demo
- run `python demo.py --ex=1` (python >= 3.6)
  - please wait some seconds: it will display some precomputed results. You can change the `ex` number from 1 to 3 to see different results
  
## Compile Cuda Kernel
- `cd` into the folder `nms3d` and run `python setup.py install` (python >= 3.6). Make sure to add your cuda directory to your environment variables.

## Intructions
- Download the [JTA dataset](http://aimagelab.ing.unimore.it/jta)
 in `<your_jta_path>`
- Run `python to_poses.py --out_dir_path='poses' --format='torch'` 
([link](https://github.com/fabbrimatteo/JTA-Dataset)) 
to generate the `<your_jta_path>/poses` directory
- Run `python to_imgs.py --out_dir_path='frames' --img_format='jpg'`
([link](https://github.com/fabbrimatteo/JTA-Dataset)) 
 to generate the `<your_jta_path>/frames` directory
- Download our precomputed codes from [here](https://drive.google.com/file/d/1aj2QqoUvkzzM4ZeehvIFOvMAO_OOtR8v/view?usp=sharing) 
and unzip them into `<your_jta_path>`
- Modify the `conf/default.yaml` configuration file specifying the 
path to the JTA dataset directory
     - `JTA_PATH: <your_jta_path>`

#### Train
- run `python train.py --exp_name=default` (python >= 3.6)

#### Show Visual Results
- run `python show.py --exp_name=default` (python >= 3.6)
    - Note that, before showing the results, you must have 
    completed at least one training epoch; however, to achieve 
    results comparable to those reported in the paper, 
    it is advisable to carry out a training of at least 100 epochs

#### Show Paper Results
- Download the [pretrained weights](https://drive.google.com/file/d/1GJNq4R3046bXkm7EXJAJ8L0PzRRQZDPg/view?usp=sharing)
 and extract them into the project folder
- Modify the `conf/pretrained.yaml` configuration file specifying the path to the JTA dataset directory
     - `JTA_PATH: <your_jta_path>`
- run `python show.py --exp_name=pretrained` (python >= 3.6)

## Citation

We believe in open research and we are happy if you find this data useful.   
If you use it, please cite our work.

```latex
@inproceedings{fabbri2020compressed,
   title     = {Compressed Volumetric Heatmaps for Multi-Person 3D Pose Estimation},
   author    = {Fabbri, Matteo and Lanzi, Fabio and Calderara, Simone and Alletto, Stefano and Cucchiara, Rita},
   booktitle = {Conference on Computer Vision and Pattern Recognition (CVPR)},
   year      = {2020}
 }
```
