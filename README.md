# ProxyCLIP+
Proxy Attention Improves CLIP for Open-Vocabulary Segmentation+


<div align="center">

<h1>ProxyCLIP: Proxy Attention Improves CLIP for Open-Vocabulary Segmentation+</h1>

<div>
    <a href='https://mc-lan.github.io/' target='_blank'>Mengcheng Lan</a><sup>1</sup>&emsp;
    <a href='https://chaofengc.github.io/' target='_blank'>Chaofeng Chen</a><sup>1</sup>&emsp;
    <a href='https://keyiping.wixsite.com/index' target='_blank'>Yiping Ke</a><sup>2</sup>&emsp;
    <a href='https://scholar.google.com.hk/citations?user=q4lnWaoAAAAJ&hl=en&inst=8669986779262753491&oi=ao' target='_blank'>Xinjiang Wang</a><sup>3</sup>&emsp;
    <a href='https://scholar.google.com.hk/citations?user=PnNAAasAAAAJ&hl=en' target='_blank'>Litong Feng</a><sup>3</sup>&emsp;
    <a href='https://www.statfe.com/' target='_blank'>Wayne Zhang</a><sup>3,4</sup>&emsp;
</div>
<div>
    <sup>1</sup>S-Lab, Nanyang Technological University&emsp; 
    <sup>2</sup>CCDS, Nanyang Technological University&emsp; 
    <sup>3</sup>SenseTime Research&emsp;
</div>
<div>
    <sup>4</sup>Guangdong Provincial Key Laboratory of Digital Grid Technology&emsp;
</div>

<div>
    <strong>Accepted to ECCV 2024</strong>
</div>

<div>
    <h4 align="center">
        • <a href="https://arxiv.org/abs/2408.04883" target='_blank'>[arXiv]</a> •
    </h4>
</div>

<img src="assets/framework.jpg" width="700px"/>

</div>


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
1) `With background class`: PASCAL VOC, PASCAL Context, PASCAL Context 459 (PC459), Cityscapes, ADE20k, ADE847, and COCO-Stuff164k, 
2) `Without background class`: VOC20, Context59 (i.e., PASCAL VOC and PASCAL Context without the background category), and COCO-Object.

For PASCAL Context 459 and ADE847, please follow the [CAT-Seg](https://github.com/KU-CVLAB/CAT-Seg/tree/main/datasets) to prepare the datasets.
For the other datasets, please follow the [MMSeg data preparation document](https://github.com/open-mmlab/mmsegmentation/blob/main/docs/en/user_guides/2_dataset_prepare.md) to download and pre-process the datasets. 
The COCO-Object dataset can be converted from COCO-Stuff164k by executing the following command:

```
python datasets/cvt_coco_object.py PATH_TO_COCO_STUFF164K -o PATH_TO_COCO164K
```

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
