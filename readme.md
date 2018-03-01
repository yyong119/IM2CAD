# IM2CAD

It's a repository trying to achieve the idea in paper <a href = "https://homes.cs.washington.edu/~izadinia/im2cad.html">IM2CAD</a>. The main goal of this paper is to reconstruct a scene that is similar to the given photo of a room.

## Datasets used in the paper

- <a href = "http://tigress-web.princeton.edu/~fy/lsun/public/release/">LSUN</a> is needed in pixel-level labeling task to estimate the room geometry.

- <a href = "http://www.image-net.org/challenges/LSVRC/2012/nonpub-downloads">imagenet2012</a> dataset is used to detect the objects in the room(pre-trained model was used in the paper).

- <a href = "https://www.shapenet.org/">ShapeNet</a> 3D models are the objects will appear in the reconstructed scene. (an account may needed to download data)

## Main Process to achieve the result

#### Room geometry estimation

The lsun indoor dataset can be downloaded from the above link, or you can fork the official GitHub repository <a href = "https://github.com/fyu/lsun">lsun</a> and follow the instructions there.

The FCN is modified from the repo <a href = "https://github.com/shekkizh/FCN.tensorflow">FCN.tensorflow</a>. Note: The format of lsun indoor dataset is different a bit from the ADEChallengeData2016 dataset which is used in the origin repository.

To train the network, just running the following command:

```shell
python FCN.py --mode=train
```

It can also visualize the part of results by replacing the "train" with "visualize".

#### Object detection

According to the paper, the Faster-RCNN is used to detect the objects occured in the indoor scene.