# land_classif_satellite

## Dataset

The dataset downloaded from Kaggle (https://www.kaggle.com/datasets/apollo2506/eurosat-dataset) is pre-split into train:validation:test = 7:2:1. 

Might merge everythign together as to produce a different split. 

## Comments

### Current (as of 2023/04/11)
- As proof of concept, currently only used first 1,000 images out of 24,300. 
- Batch size = 32, Epoch = 10. Data augmentation incorporated. 
- Current train accuracy already at 95%, validation at 85%. Can probably go higher when all images are used. 
- On my laptop, GPU utilization ~6%, and 5.5/19.8 GPU memory used (4G of dedicated GPU fully utilized, and 1.6G of shared memory utilized). 
- Note that `dir_test`, which contains 2,700 labeled images, are left untouched until the very end, when we presumably have multiple models and need to pick one to submit/present. 

### Next steps
- So far only fed on 1000 images to the model (800 train + 200 validation). Will move on to use the full 24,300 dataset later. 
- Instead of a single model, separate feature extraction (pre-trained model) into a separate chunk so that fitting the model can be done quicker, hopefully. 

### Model / Architecture
- While I don't remember how I settled around ConvNeXt and BEiT, I think there's a risk that we might have committed ourselves to the wrong architecture.
- Based on what I found regarding [ConvNeXt](https://tfhub.dev/sayakpaul/collections/convnext/1), I think it might be some final project / PhD / conference [paper](https://arxiv.org/pdf/2201.03545.pdf), with limited impact. This might mean that it is NOT actually a good model. At least not one of the best. 
- I watched the [youtube video](https://www.youtube.com/watch?v=QzCjXqFnWPE) of the paper's author introducing the model. It seems like they just repurposed one of the older methods and added some new spices. It is not one of these newfangled BERT/Transformer-based models. Not sure if that's a concern. 
- Another thing that annoys me is that I can't seem to find a nice visual illustration of the model architecture. I know what the individual blocks are, but not the overall architecture. God forbid I have to sit down and actually read and understand the original paper? 
- BEiT is based on BERT, which sounds exciting until you realize it is only availiable in PyTorch. ConvNeXt's TF implementation can be found [here](https://github.com/sayakpaul/ConvNeXt-TF)
