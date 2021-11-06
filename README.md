# HopAI Math2Latex 
HopAI Innovations presents a novel handwriting to latex service for the easy and convenience of the user

Development stage: Prototype

HopAIProofOfConcept.ipynb:
Small CNN trained for 10 epochs and 75% of the data from https://www.kaggle.com/xainano/handwrittenmathsymbols and tested on 25% 
Achieved 83% Accuracy on 82 labels on test set
Achieved peak 91% Accuracy on train set

Running Notebook locally:\
***Warning: YOU NEED A GPU IN ORDER TO RUN THIS FAST***\
1. To set up your GPU please install CUDA 11.1 from https://developer.nvidia.com/cuda-11.1.0-download-archive\
2. Create a conda env (download conda from https://www.anaconda.com/products/individual)\
3. Download ```pytorch for CUDA 11.1, numpy, pandas, ipykernel```\
Use this command for pytorch
```
conda install pytorch torchvision torchaudio cudatoolkit=11.1 -c pytorch
```
4. Either Use VSCode, Jupyter Notebook, or whatever python development env that supports jupyter notebooks
5. Add your conda env to a jupyter kernel with this command
```
python -m ipykernel install --user --name=<NAME GOES HERE OF CONDA ENV>
```
6. You are able to run the notebook with GPU acceleration 

Running Notebook on Colab:\
***THIS IS PROBABLY EASIER FOR PEOPLE WHO HAVE NOT WORKED WITH CUDA OR DO NOT HAVE A GPU***\
***GENERAL TIP: Remember that you only have a certain amount of GPU time on Colab. Use it wisely***
1. Download the gitrepo to your google drive
2. Open the notebook through google drive through colab
3. Download the files using 
```
!wget https://www.kaggle.com/xainano/handwrittenmathsymbols/download
```
4. unzip the files with 
```
unzip <name_of_zip>.zip
```
5. set the file paths in the notebook correctly because google drive has a weird way of doing file paths