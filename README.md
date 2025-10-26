# ProxyCLIP+
Proxy Attention Improves CLIP for Open-Vocabulary Segmentation+


<div align="center">

<h1>ProxyCLIP: Proxy Attention Improves CLIP for Open-Vocabulary Segmentation+</h1>




## Dependencies and Installation


```
# git clone this repository
git clone https://github.com/mc-lan/ProxyCLIP.git
cd ProxyCLIP

# create new anaconda env
conda create -n ProxyCLIP python=3.10
conda activate ProxyCLIP

# install torch and dependencies
pip install -r requirements.txt
```

## Datasets
We include the following dataset configurations in this repo: 
1) `Semantic Segmentation`: OpenEarthMap
2) `Building Extraction`: 
4) `Road Extraction`: 
5) `Water Extraction`: 

Please refer to [dataset_prepare.md](https://github.com/likyoo/SegEarth-OV/blob/main/dataset_prepare.md) for dataset preparation.

## Quick Inference
```
python demo.py
```


## Model evaluation
Please modify some settings in `configs/base_config.py` before running the evaluation.

For SAM and MAE, please download the checkpoints from [SAM](https://github.com/facebookresearch/segment-anything#model-checkpoints) and [MAE](https://github.com/facebookresearch/mae).



Single-GPU:

```
python eval.py --config ./config/cfg_DATASET.py --workdir YOUR_WORK_DIR
```

Multi-GPU:
```
bash ./dist_test.sh ./config/cfg_DATASET.py
```

Evaluation on all datasets:
```
python eval_all.py
```
Results will be saved in `results.xlsx`.
