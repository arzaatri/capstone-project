# capstone-project

Code from our capstone project, *Multimodal Self-Supervised Deep Learning with Chest X-Rays and EHR Data.*

This implementation combines three modalities of data (image, text, and tabular EHR) from MIT's MIMIC-IV and MIMIC-CXR datasets to learn a model for diagnosing various lung ailments. Our approach was to first pretrain a model using self-supervised learning among the three modalities, using contrastive loss between image-text and image-EHR pairings. 

In short, the model attempts to embed all 3 modalities into the same space; for a given patient, each embedding should be the same. Training in this method allows the model to leverage information in the other modalities when learning how to embed a single one, e.g. to leverage a doctor's notes to create more informative image embeddings. We then took the image component of this model and finetuned its embeddings in a supervised manner to perform two downstream tasks: disease diagnosis and morality prediction.

Many different model structures, preprocessing techniques, and dataloading methods were experimented with to determine which configuration yielded a superior balance of performance and training speed. At the cost of messiness, code from all experiments is left in the repository for future reference. The final pretraining method is the one used in src/train_v2.py and its relevant modules; the final methods for downstream tasks are likewise shown in src/train_diagnosis.py, src/test_diagnosis.py, src/train_mortality.py, and src/test_mortality.py. All other modules should be considered irrelevant to final results.
