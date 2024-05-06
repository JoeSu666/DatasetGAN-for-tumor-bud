# DatasetGAN pipeline


## DatasetGAN

1. Make training data. Here, it will generate a few sample images for human to annotate:
```shell
python ./make_training_data2.py --exp <CONFIG FILE> --sv_path <SAVING DIR> --num_sample <# of FEW SHOT IMAGES GENERATED FOR ANNOTATION>
```

Example: `--exp ./experiments/tb512.json --sv_path ./tbsf_512 --num_sample 40` \
Please annotate the generated images and save in .json files. I recommend using LabelMe.

2. Train DatasetGAN: 
```shell
python train_interpreter2.py --exp <TRAINING CONFIG FILE>
```
Example: `--exp experiments/tb512.json`

3. Generate segmented data using your DatasetGAN:
```shell
python train_interpreter2.py --generate_data True --exp <TRAINING CONFIG FILE> --resume <MODEL WEIGHT DIR> --num_sample <# OF IMAGES>
```

Example: `--exp experiments/tb512.json --resume ./model_dir/tbsf_512 --num_sample 20`