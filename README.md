# StructCoder
Official implementation of [StructCoder: Structure-Aware Transformer for Code Generation](https://arxiv.org/abs/2206.05239)

## Setup the conda enviroment
conda create -n structcoder --file structcoder.yml <br>
conda activate structcoder <br>
For running preprocessing notebooks, add the created structcoder conda enviroment to jupyter notebook using these commands. <br>
conda install -c anaconda ipykernel <br>
python3 -m ipykernel install --user --name=structcoder

## Data Preprocessing
All datasets are loaded from Huggingface's Datasets library except for concode which can be obtained from https://github.com/microsoft/CodeXGLUE/tree/main/Text-Code/text-to-code/dataset/concode. Edit the path to Concode dataset in finetune_preprocess.ipynb in line "with open('../datasets/concode/'+split+'.json') as f:"

Run the cells in pretrain_preprocess.ipynb and finetune_preprocess.ipynb. This should create a folder data/ with subfolders for each dataset used for experiments. You can skip pretrain_preprocess.ipynb if you choose to run our finetuning codes with the provided pretrained checkpoint.

## Download pretrained checkpoint:
mkdir -p saved_models/pretrain/ <br>
Download the pretrained model weights from [here](https://drive.google.com/drive/folders/1cyvtmZjaLc1OwlnU0_N_GwC_eAs5snf9?usp=sharing) and place it under saved_models/pretrain/checkpoint-12000/

## Training commands:
Pretraining: python pretrain_main.py <br>
Java-C# translation: python finetune_translation_main.py --source_lang java --target_lang cs <br>
C#-Java translation: python finetune_translation_main.py --source_lang cs --target_lang java <br>
Concode: python finetune_generation_main.py <br>
APPS: python finetune_apps_main.py

## Citation
If you find the paper or this repo useful, please cite

    @article{tipirneni2022structcoder,
    title={StructCoder: Structure-Aware Transformer for Code Generation},
    author={Tipirneni, Sindhu and Zhu, Ming and Reddy, Chandan K},
    journal={arXiv preprint arXiv:2206.05239},
    year={2022}
    }
