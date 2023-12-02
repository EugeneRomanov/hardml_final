# hardml_final


# Introduction

Searching for relevant documents to a given query is a well-known problem in the field of machine learning and information retrieval.
QA Search is a Question-Answer search system designed to elevate your search experience. 

This repository is an example of a system that solves this problem.


# System

1. Indexes: The Indexes service forms the backbone of QASearch, managing and organizing the vast repository of question-answer pairs

2. Gateway: The Gateway service serves as the entry point for user queries, orchestrating communication between different services

3. Ranker: The Ranker service leverages KNRM model to prioritize search results

4. Embedder: The Embedder service is responsible for create vectorized samples, using use-large model from tf-serving

5. Service Registry The Service Registry, powered by Redis, acts as a dynamic catalog of index services


![image](https://github.com/EugeneRomanov/hardml_final/assets/72860505/ba0c0ead-efb9-4950-aab7-9dafbf1ed5e5)


# Indexes update

![image](https://github.com/EugeneRomanov/hardml_final/assets/72860505/810c785a-f643-4911-aae0-0db7fe13ae78)



# CI/CD*

1. Build QASearch Docker Images: Builds Docker images for QASearch services (ranker, embedder, gateway, indexes) based on Dockerfiles
2. Execute build and deploy scripts from utils directory: Navigates to the utils directory and executes any custom build and deploy scripts
3. Run QASearch Tests: Executes tests to ensure the quality and functionality of QASearch services

   ![image](https://github.com/EugeneRomanov/hardml_final/assets/72860505/f5348f30-279c-4ba6-90f8-5ef187808783)


