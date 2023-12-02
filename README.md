# hardml_final


**Introduction**

Searching for relevant documents to a given query is a well-known problem in the field of machine learning and information retrieval.
QA Search is a Question-Answer search system designed to elevate your search experience using techniques in Learning to Rank (LTR) with KNRM model. 

This repository is an example of a system that solves this problem.


**System**

1. Indexes: The Indexes service forms the backbone of QASearch, managing and organizing the vast repository of question-answer pairs

2. Gateway: The Gateway service serves as the entry point for user queries, orchestrating communication between different services

3. Ranker: The Ranker service leverages KNRM model to prioritize search results

4. Embedder: The Embedder service is responsible for create vectorized samples, using use-large model from tf-serving

5. Service Registry The Service Registry, powered by Redis, acts as a dynamic catalog of index services



![image](https://github.com/EugeneRomanov/hardml_final/assets/72860505/111e7ef2-f6e8-49e0-b7f9-d2f900d45ec2)


