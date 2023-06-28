# Analysis using the YOLOX framework

## Product owner
Orange: Jaroslaw.Legierski@orange.com 

## Project description
Create and validate a model which will detect and classify objects based on image analysis using the YOLOX framework (https://github.com/Megvii-BaseDetection/YOLOX). The model should detect whether people entering a construction area wear a proper safety gear. Specifically, it should detect objects like: person, helmet, head, vest. Special attention should be given to false positives (a bald person or a person with a hat resembling a helmet). The following public data set can be used for training:  Hard Hat Workers Dataset https://public.roboflow.com/object-detection/hard-hat-workers created by Northeastern University - China (it contains more objects than listed above).  LIterature: https://github.com/Megvii-BaseDetection/YOLOX   
https://aigeekprogrammer.com/pl/yolo-szybka-detekcja-klasyfikacja-obiektow/
https://public.roboflow.com/object-detection/hard-hat-workers


## Manual

### YOLOX Code & Repository
The original repository was forked to [YOLOX-data-science-workshop](https://github.com/marneusz/YOLOX-data-science-workshop) and is used as a submodule in `libs/` directory. There are all the necessary changes and adjustments for our dataset.

### Dataset Paths and Structure

Our split dataset and final model are located in [Google Drive](https://drive.google.com/drive/folders/1KufKNQjidhyof_Y2MBmjcDlDlXcvlCCj) should be placed in `libs/YOLOX-data-science-workshop/datasets/`. The structure of the dataset's directory `dsw` should be following

```
├── libs                    
│   ├── YOLOX-data-science-workshop          # Forked YOLOX repository with our original changes
│   │   ├── datasets                         # All datasets should be placed here
|   |   |   ├── annotations                  # Consists of two files: "train_annotations.coco.json" & "val_annotations.coco.json"
|   |   |   ├── train                        # Training images
|   |   |   ├── val                          # Validation images
```

### Test Experiment with WandB Support
Visit [wandb.ai](wandb.ai) to see the metrics, artifacts, and experiments' details.

You can run the test experiment by running the following command
```bash
python tools/train.py -f exps/dsw/yolox_s_dsw.py \            # chosen experiment
                      -d 1 \                                  # number of GPUs available
                      -b 32 \                                 # batch size
                      --fp16 \                                # float precision
                      -o \                                    # occupy GPU for training
                      -c ../../models/yolox_s.pth \           # path to chosen model (adjust to your own paths
                      --logger wandb \                        # Weights & Biases configuration
                               wandb-project test-dsw \       # project name
                               wandb-entity 2023l-dsw-orange \ 
                               wandb-name test_run \          # adjust the run name
                               wandb-save_dir logs \
                               wandb-num_eval_images 5 \
                               wandb-log_checkpoints True 
```

### Memory Leak 

- https://github.com/Megvii-BaseDetection/YOLOX/issues/103
- https://github.com/Megvii-BaseDetection/YOLOX/pull/216
- https://github.com/Megvii-BaseDetection/YOLOX/issues/114


### Useful Materials
- [Fast inference](https://dicksonneoh.com/portfolio/how_to_10x_your_od_model_and_deploy_50fps_cpu/#-modeling-with-yolox)
