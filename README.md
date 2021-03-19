## Construction and Application of Materials Knowledge Graph Based on Author Disambiguation: Revisiting the Evolution of LiFePO<sub>4</sub>

#### **Zhiwei Nie, Yuanji Liu, Luyi Yang, Shunning Li, Feng Pan**

doi: [[10.1002/aenm.202003580](https://doi.org/10.1002/aenm.202003580)]



### <u>About The Work</u>

Due to the recent innovations in computer technology, the emerging field of materials informatics has now become a catalyst for a revolution of  the research paradigm in materials science. Knowledge graphs, which  provide support for knowledge management, are able to collectively  capture the scientific knowledge from the vast collection of research  articles and accomplish the automatic recognition of the relationships  between entities. In this work, a materials knowledge graph, named  MatKG, is constructed, which establishes a unique correspondence between subjects and objects in the materials science area. An emphasis is  placed on the disambiguation of authors, addressed by a deduplication  model based on machine learning and matching dependencies algorithms.  Specifically, MatKG is applied to perform tracking on research trends in the study of LiFePO4 and to automatically chronicle the  milestones achieved so far. It is believed that MatKG can serve as a  versatile research platform for amalgamating and refining the scientific knowledge of materials in a variety of subfields and intersectional  domains.



### <u>Data collection and processing</u>  

1. More than 2.9 million abstracts of articles, as well as their author information, are collected in the field of materials science through the APIs (application  programming interfaces) of Elsevier's Scopus, Science Direct, and Web of  Science. 

2. After processing through regular expression matching, about 1.05 million records of author information are gathered,  including the author's first name (FN), last name (LN), Open Researcher  and Contributor ID (ORCID), email, and affiliation. The  semantic information from the titles, abstracts, and keywords of the  articles are used for author deduplication. Term Frequency-Inverse Document Frequency (TF-IDF) was used to encode the text information of scientific literature by evaluating the importance of a word to a document set or a corpus. The importance of a word is directly proportional to the number of times it appears in the article, and inversely proportional to the number of times it appears in the corpus. We adopted the TfidfVectorizer library in Scikit-learn to implement the TF-IDF algorithm.



### <u>Modules of MatKG</u> 

Machine learning and matching dependencies algorithms are used in MatKG. There are four modules in MatKG: ML‐based pre‐training  (module I), MD‐based collective blocking (module II), ML‐based  classification (module III), and breadth‐first search (module IV).  Modules I, II, and III correspond to the deduplication process.        

**Module I**:  ML‐based pre‐training.  Naïve Bayes Classifier has stable classification efficiency, ability to handle multiple classification tasks, and insensitivity to missing data, which make this algorithm especially suitable for text classification. We have randomly selected 100,000 documents from the corpus and use F1-score to evaluate the performance of different classification algorithms. The performance of Naïve Bayes Classifier, Support Vector Machines and Decision Tree in text classification task is compared. We find that the performance of Naïve Bayes Classifier is better than that of Support Vector Machines and Decision Tree. Therefore, Naïve Bayes Classifier was employed as the classification algorithm in this study. In the learning process of Naïve Bayes classifier, 1150 records of author information were randomly chosen from the database as the sample data set, and further split into training set (80%) and test set (20%) via the hold-out rule. This model can reach a classification accuracy of about 90%. The original data is classified into several broad categories to facilitate the next step of processing.

**Module II**: MD‐based collective blocking. Matching dependencies is a duplicate detection method based on dependencies and similarity to handle data sources with errors. Based on functional dependencies, similarity predicates were used to define matching dependencies. A similarity threshold of 0.8 was set, upon which the record pairs will be grouped into clusters.

**Module III**: ML‐based  classification. 800 record pairs from different blocks were randomly selected as the sample data set, divided into training set (80%) and test set (20%). Labels (±1) were assigned to the record pairs to denote whether they are duplicates. After training, this model can reach an accuracy of more than 96%. 

**Module IV**:  Breadth‐first search.  In order to reduce the time complexity and cope with the increasing  amount of data, a pruning algorithm is carried out during the CTANE. The candidate set, that is, the search space, is pruned, which yields a  large leap in the search speed. The improved algorithm is named  Pruned‐CTANE. 



### <u>Detailed Steps of Text Classification Task</u>

Based on TF-IDF algorithm and Naïve Bayes Classifier, the text classification can be accomplished as follows: 

**1)Accomplish word segmentation.** We used the NLTK package for word segmentation, which is one of the most widely used toolkits containing stop words, word segmentation and labeling methods. 

**2)Load stop words list.** Irrelevant words were filtered out by loading the stop words list.

**3)Calculate the weight of words.** The TfidfVectorizer class was created, and then the fit_transform method was used to obtain the TF-IDF feature space.

**4)Generate Naïve Bayes Classifier.** Naïve Bayes Classifier was trained based on the feature space of the training set and the corresponding classification.

**5)Use the classifier to make predictions.** The trained classifier was employed to make predictions from the feature matrix of the test set.

**6)Calculate the accuracy.** The predicted results were compared with the actual values to provide the accuracy of the model on the test set.



### <u>Ongoing Follow-up Work</u>

We are adding more material characteristic information to MatKG to build a material reasoning and prediction system, which will open up a new paradigm for material research and design.



### <u>Issues?</u>

You can either report an issue on github or contact one of us directly. Try zhiweiNie@pku.edu.cn, [lisn@pku.edu.cn](mailto:lisn@pku.edu.cn) or panfeng@pkusz.edu.cn.









