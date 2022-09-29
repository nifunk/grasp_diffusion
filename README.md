# Pytorch implementation of Diffusion models in SE(3) for grasp and motion generation

This library provides the tools for training and sampling diffusion models in SE(3),
implemented in PyTorch. 
We apply them to learn 6D grasp distributions. We use the learned distribution as cost function
for grasp and motion optimization problems.
See reference [1] for additional details.

[[Website]](https://sites.google.com/view/se3dif/home)      [[Preprint]](https://arxiv.org/pdf/2209.03855.pdf)

<img src="assets/grasp_diffusion.gif" alt="diffusion" style="width:200px;"/><img src="assets/grasp_diffusion_01.gif" alt="diffusion" style="width:200px;"/><img src="assets/grasp_diffusion_02.gif" alt="diffusion" style="width:200px;"/><img src="assets/grasp_diffusion_03.gif" alt="diffusion" style="width:200px;"/>


## Installation

Create a conda environment
```python
conda env create -f environment.yml
```
Activate the environment and install the library
```python
conda activate se3dif_env && pip install -e .
```

## Preproccessed Acronym [2] and Shapenet dataset [3]

We define the source of the dataset and trained models in ```se3dif/utils/directory_utils.py```
Originally, the data root folder is set in the folder in which the repository is (one folder before the repository). 
Nevertheless, you can change it by changing ```root_directory``` and  ```root_directory``` in ```se3dif/utils/directory_utils.py```.


Download the preprocessed dataset and unzip the folder in the before the ```root_directory```
1. Mugs (Grasps, Meshes, SDF, Pointcloud) [data](https://drive.google.com/file/d/1fURx7bTutANvOFvbKeo8XahT-R3A_vxH/view?usp=sharing)


## Trained Models

Download the trained models and unzip the folder in the before the ```root_directory```
1. Pointcloud conditioned SE(3) GraspDiffusion model [PointGraspDif](https://drive.google.com/file/d/1Y0ZWAhs0GSL7A-J3yA7ts3N8TnQTGHon/view?usp=sharing)


## Sample examples

Generate SE(3) grasp poses 
```azure
python scripts/sample/generate_6d_grasp_poses.py --n_grasps 10 --obj_id 15
```

## Train a new model

Train no-pointcloud model
```azure
python scripts/train/train_6d_grasp_diffusion.py
```

Train pointcloud conditioned model
```azure
python scripts/train/train_pointcloud_6d_grasp_diffusion.py
```


## References

[1] Julen Urain*, Niklas Funk*, Georgia Chalvatzaki, Jan Peters. 
"SE(3)-DiffusionFields: Learning smooth cost functions for joint grasp and motion optimization through diffusion" 
*Under review* 2022.
[[arxiv]](https://arxiv.org/pdf/2209.03855.pdf)

```
@article{urain2022se3dif,
  title={SE(3)-DiffusionFields: Learning smooth cost functions for joint grasp and motion optimization through diffusion},
  author={Urain, Julen and Funk, Niklas and Chalvatzaki, Georgia and Peters, Jan},
  journal={https://arxiv.org/pdf/2209.03855.pdf},
  year={2022}
```

[2] Eppner Clemens, Arsalan Mousavian, Dieter Fox. 
"Acronym: A large-scale grasp dataset based on simulation." 
*IEEE International Conference on Robotics and Automation (ICRA)*. 
2021 [[arxiv]](https://arxiv.org/abs/2011.09584)


[3] Chang Angel X., et al. 
"Shapenet: An information-rich 3d model repository." 
*arXiv preprint arXiv:1512.03012*. 2015 [[arxiv]](https://arxiv.org/abs/1512.03012)

### Contact

If you have any questions or find any bugs, please let me know: [Julen Urain](http://robotgradient.com/) julen[at]robot-learning[dot]de
