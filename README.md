# Classifying Injury Reports Using Transformer-Based Models
This repository demonstrate how to use **a transformer-based deep learning model** to **classify injury narratives into 48 event types of injury reports**. The **baseline model** for performance comparison is **Naïve Bayes**. The **BERT**(Bidirectional Encoder Representations from Transformers)**-based deep learning model** achieved a test accuracy of **86.8 percent** and the **Naïve Bayes** model achieved a **test accuracy of 73.1 percent**. @[halfmoonliu](https://github.com/halfmoonliu) (**Yun-Chung Liu**) contributed to **dataset preparation** and **BERT-based model training and evaluation**, @[Keonnartey](https://github.com/Keonnartey) （Keon Nartey) contributed to **Naïve Bayes model training and evaluation**

## Background

## Methods

#### Dataset
The dataset used is from a competition organized by NASA-Tournament Lab and National Institute for Occupational Safety & Health (NIOSH) to automate data processing in the occupational safety and health (OSH) surveillance systems. Specifically, **given a free text injury report**, such as "*worker fell from the ladder after reaching out for a box.*” , the task is to **assign an event type code** from the Occupational Injuries and Illnesses Classification System (OIICS). The details of the task and competition can be found in a [blogpost](https://blogs.cdc.gov/niosh-science-blog/2020/02/26/ai-crowdsourcing/) by CDC (Center for Disease Control). The dataset is downloaded from [hugging face](https://huggingface.co/datasets/mayerantoine/injury-narrative-coding). The winning solutions can be found on [NASA Tournament Lab's Github Page](https://github.com/NASA-Tournament-Lab/CDC-NLP-Occ-Injury-Coding).

#### Examples

| Text | Event |
|---|---|
| 30YOF AT WORK DOING UNSPECIFIED LIFTING AND STRAINED NECK | 71 (Overexertion Involving Outside Sources) |
| 31YOM AT WORK USING A NAIL GUN AND SHOT SELF IN THE FINGER WITH A NAIL PW FINGER | 62 (Struck by Object or Equipment) |
| 35YOM FELL BACK WHILE FIGHTING A FIRE DX SHOULDER DISLOCATION SUSPECTED ULNAR ARTERY INJ | 30 (Fire or explosion, unspecified) |

#### Preprocessing and Model Evaluation

The texts were turned into **lowercase** and **tokenized** using a BERT tokenizer. Pretrained **BERT-based model** provided by Hugging Face was used for the **injury report classification task**. The **baseline model** used for performance comparison is **Naïve Bayes**, which **classifies documents based on event probabilities and token probabilities given an event**. **The dataset was randomly split into training, development, and test dataset at a 8:1:1 ratio**.  BERT-based model is **finetuned on the training dataset**, **hyperparameters were optimized** using the **development set** and model **performance was evaluated on the test dataset**. For the Naïve Bayes model, model accuracy was evaluated both on the development and test dataset. 

## Results

#### Dataset Overview

The dataset used contains **222,980 injury reports and 48 different event types**. The median count of labels is 724.5 (Interquartile range: 51.3-5100). Both datasets were split into training, development and testing datasets at a ratio of 8:1:1, resulting in 183,856, 22,982, 22,982 rows of dataset respectively. Figure 1 shows the distribution of event count in the real dataset, with over 30 thousand reports of event 71 and less than 100 reports for 18 labels. 

<img width="661" alt="Event Distribution" src="https://github.com/halfmoonliu/InjuryNoteLabel/assets/46064664/ca8bc831-1ead-466c-a4ed-90a2d5f728bf">


#### Model Parameters

The **pretrained uncased BERT model** was used for the injury report classification task. The length of the **hidden state** was 786. A **dropout rate** of .3 was applied to the output state and a fully connected layer was added to output classification results. Each injury report was padded to the **max document length** of 150 tokens. **Batch size** was set at 16, with a **learning rate** of .00002 for model training. The learning rate was set to decrease linearly during the training stage, across training epochs and. **Cross entropy** was used as the loss function and **Adam** was used for model optimization. The BERT-based-model was trained for 10 epochs. For the Naïve Bayes model, the smoothing parameter of alpha was set to be 1. 

#### Model Performance

| Dataset | BERT-Based | Naïve Bayes | 
|---|---|---|
| Test Set Accuract (%) | 86.79 | 73.14 |
| Development Set Accuracy (%) | 86.99 | 73.13 |
| Training Set Accuracy (%) | 95.83 | 75.26  |
