# EnsembleAI2024 - Overfitters
- Albert Ściseł
- Mateusz Staniszewski
- Łukasz Staniszewski
- Bartosz Cywiński


### Setup
* Create environment with python 3.9
* Install requirements from requirements.txt
* Install and [setup Wandb](https://docs.wandb.ai/quickstart) (pipreqs does not add it to requirements)
```bash
pip install wandb
```
* Install NASA repo
```
pip install git+https://github.com/nasa/pretrained-microscopy-models
```
* Make sure you have access to project given by `<wandb_entity>/<wandb_project>` from [config](config)
* Set [src](src) directory as PYTHONPATH
```bash
export PYTHONPATH=${PYTHONPATH}:./src
```
* Download SimSiam ResNet50 checkpoint pretrained on ImageNet from https://dl.fbaipublicfiles.com/simsiam/models/100ep/pretrain/checkpoint_0099.pth.tar and place in ./end2end_stealing/pretrained_weights
* Download DINO VitS16 pretrained on ImageNet from https://dl.fbaipublicfiles.com/dino/dino_deitsmall16_pretrain/dino_deitsmall16_pretrain_full_checkpoint.pth and place in ./end2end_stealing/pretrained_weights


## Running end2end experiments

### Run model stealing
Put `images.pt` and `features.pt` in `args.data`. Features should be of shape `[N,512]` and images `[N,3,32,32]`.

Stealing an ResNet50 encoder
```bash
./bash_scripts/steal_model_hackathon.sh
```
