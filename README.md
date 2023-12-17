# Classifying Injury Reports Using Transformer-Based Models
This repository demonstrate how to use **a transformer-based deep learning model** to **classify injury narratives into 48 event types of injury reports**. The **baseline model** for performance comparison is **Naïve Bayes**. The **BERT**(Bidirectional Encoder Representations from Transformers)**-based deep learning model** achieved a test accuracy of **86.8 percent** and the **Naïve Bayes** model achieved a **test accuracy of 73.1 percent**. @[halfmoonliu](https://github.com/halfmoonliu) (**Yun-Chung Liu**) contributed to **dataset preparation** and **BERT-based model training and evaluation**, @[Keonnartey](https://github.com/Keonnartey) contributed to **Naïve Bayes model training and evaluation**

## Background

## Dataset
The dataset used is from a competition organized by NASA-Tournament Lab and National Institute for Occupational Safety & Health (NIOSH). The goal is to automate the processing of data in occupational safety and health (OSH) surveillance systems. Specifically, given a free text injury report, such as "*worker fell from the ladder after reaching out for a box.*” , the task is to **assign a injury code** from the Occupational Injuries and Illnesses Classification System (OIICS). The details of the task and competition can be found in a [blogpost](https://blogs.cdc.gov/niosh-science-blog/2020/02/26/ai-crowdsourcing/) by CDC (Center for Disease Control). The dataset is downloaded from [hugging face](https://huggingface.co/datasets/mayerantoine/injury-narrative-coding). The winning solutions can be found on [NASA Tournament Lab's Github Page](https://github.com/NASA-Tournament-Lab/CDC-NLP-Occ-Injury-Coding).

## Examples

| Text | Event |
| 30YOF AT WORK DOING UNSPECIFIED LIFTING AND STRAINED NECK | 71 (Overexertion Involving Outside Sources) |
| 31YOM AT WORK USING A NAIL GUN AND SHOT SELF IN THE FINGER WITH A NAIL PW FINGER | 62 (Struck by Object or Equipment) |
| 35YOM FELL BACK WHILE FIGHTING A FIRE DX SHOULDER DISLOCATION SUSPECTED ULNAR ARTERY INJ | 30 (Fire or explosion, unspecified) |


