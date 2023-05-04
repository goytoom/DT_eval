# Introduction
This is the repository for the project "Evaluating Decision Transformers on Challenging Environments". This project is based on the Decision Transformers' original authors: https://github.com/kzl/decision-transformer/tree/master/atari

## Implementation
This implementation for solving Atari games follows the original authors'. The models are based on [minGPT](https://github.com/karpathy/minGPT).
All benchmarks are based on the [DQN-replay](https://github.com/google-research/batch_rl) dataset. 

## Installation

Dependencies can be installed with the following command:

```
conda env create -f conda_env.yml
```

## Downloading datasets

Create a directory for the dataset and load the dataset using [gsutil](https://cloud.google.com/storage/docs/gsutil_install#install). Replace `[DIRECTORY_NAME]` and `[GAME_NAME]` accordingly (e.g., `./dqn_replay` for `[DIRECTORY_NAME]` and `Breakout` for `[GAME_NAME]`)
```
mkdir [DIRECTORY_NAME]
gsutil -m cp -R gs://atari-replay-datasets/dqn/[GAME_NAME] [DIRECTORY_NAME]
```

## Replication

To replicate the project results, run the following code:

```
python run_dt_atari.py --seed 123 --epochs 5 --model_type 'reward_conditioned' --num_steps 500000 --num_buffers 50 --game 'Montezuma_Revenge' --batch_size 128
```

and for the robustness check:

```
python run_dt_atari.py --seed 123 --epochs 5 --model_type 'reward_conditioned' --num_steps 500000 --num_buffers 50 --game 'Crazy_Climber' --batch_size 128
```

## Installing Atari Games / Additional Notes

This project requires the package atari_py which installs all neccessary code and data to run atari games. However, external software (ROMS to run atari games) need to be downloaded and installed. 
This is relatively simple. After setting up the conda environment, download the ROMS (zip file) from http://www.atarimania.com/rom_collection_archive_atari_2600_roms.html. 
Then run:
```
python -m atari_py.import_roms <path to folder>
```

See the full instructions for atari_py at: https://github.com/openai/atari-py