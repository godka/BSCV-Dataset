# BSCV-Dataset
<!-- 
<p align="left">
    <a href=''>
      <img src='https://img.shields.io/badge/Paper-arXiv-green?style=plastic&logo=arXiv&logoColor=green' alt='Paper arXiv'>
    </a>
    <a href=''>
      <img src='https://img.shields.io/badge/Paper-PDF-red?style=plastic&logo=adobeacrobatreader&logoColor=red' alt='Paper PDF'>
    </a>
</p> -->

<!-- This repo contains code for our paper:

[Bitstream-corrupted Video Recovery: Benchmark Dataset and Method]()

[Tianyi Liu](), [Kejun Wu](), [Yi Wang](), [Wenyang Liu](), [Kim-Hui Yap](), [Lap-Pui Chau]() -->

(This page is under construction)

## Dataset

![Tesear](teaser_v6_00.png)

### Property
- Flexible video resolution setting (240P, 480P, 720P)
- Realistic video degradation caused by bitstream corruption.
- Various unpredictable error pattern in different degree.
- With over 17K video clips and 2M frames, 50% frames have corruption.
- ...

### Download
For dataset downloading, please check this [link](https://entuedu-my.sharepoint.com/:f:/g/personal/liut0038_e_ntu_edu_sg/Egn7Xygv7UJBilL9z3nFo_4Bm5LdeoXCv-uiDo3qANsmTw?e=fMU9gZ) (Upload in progress).

### Extraction
We have seperated the dataset into training and testing set and for each branch. 
After downloading the .tar.gz files, please firstly run the following .sh file for restoring the original .tar.gz files, unzipping the archives and formatting the folders by
```
$ bash format.sh
```

After the data preparation, ffmpeg encoded orignial (GT) video bitstream is provided in the ``_144096`` branch with folder name ``GT_h264`` and its decoded frame sequence with corruption is provided in the folder named ``GT_JPEGImages``.
We also provide the h264 bitstreams of each video and their decoded frame sequence as commonlu used video dataset.
Additionally, the mask sequence which is used for corruption region indication is provided in the ``masks`` folder in each branch

### Extension
The proposed parameter model for generating bitstream corruption and therefore causing arbitrarily corrupted videos and additional branches. 
You can use the provided program with your parameter combination to generate your own branches based on the GOP size 16 as our setting, by the following commands, e.g.
```
python corrpt_Gen.py --prob 1/16 --pos 0.4 --size 4096 
```
If you want to adjust the GOP size, please refer to FFmpeg's instruction to recoding the frame sequence ``GT_JPEGImages`` in branch ``_144096``.

## Experimental Setup
### FFmpeg Installation
We adopt FFmpeg as our video codec, please refer to the official guide line for your ffmpeg installation.

PS: It seems the working principle is different between Linux and Windows version of Linux since we have some lost-frame error in decoding on Linux but the same bitstream is fine on Windows. So we recommend using Windows FFmpeg to repair the frame loss issue if you are generating new branches. 

### Environmental Setting
We provide all environment configurations in ``requirements.txt``.

```bash
$ conda create -n BSCVI python=3.7
$ pip install -r requirements.txt
```

<!-- Similar CUDA version should also be acceptable with corresponding version control for ``torch`` and ``torchvision``.
We refer the authors to [Generation](generation/README.md) and [Experiment](baselines/README.md) for details on quetsion-answer
generation, balancing, data split, and baseline experiments. For these two functionalities, please checkout the corresponding
sub-directory for code and instructions. -->

## Citation
If you find our paper and/or code helpful, please consider citing:
```
@inproceedings{,
    title = {},
    author = {},
    booktitle = {},
    year = {}
}
```

## Acknowledgement
