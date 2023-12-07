# hardml_final


# Introduction

QA Search System is a powerful tool for finding relevant documents quickly and efficiently. It uses advanced matematical and ml algorithms to analyze the text of documents and match them to your search queries, ensuring that you get the most accurate results possible.

When using QA Search System, it is important to enter your search query in a clear and concise manner. This will help the system to understand what you are looking for and return the most relevant results. You can also use advanced search options to narrow down your results by date, author, or other criteria.

Once you have entered your search query, QA Search System will begin scanning through its database of documents to find matches. It will rank the results based on their relevance to your query, with the most relevant documents appearing at the top of the list.

Overall, QA Search System is an invaluable tool for anyone looking to find relevant documents quickly and efficiently. Its advanced algorithms and user-friendly interface make it easy to use, even for those who are not tech-savvy. 

However, the construction and system design of such a system is not a simple matter. This repository is an example of what it might look like


# System

1. Indexes: The Indexes service forms the backbone of QASearch, managing and organizing the vast repository of question-answer pairs

2. Gateway: The Gateway service serves as the entry point for user queries, orchestrating communication between different services

3. Ranker: The Ranker service leverages KNRM model to prioritize search results

4. Embedder: The Embedder service is responsible for create vectorized samples, using use-large model from tf-serving

5. Service Registry The Service Registry, powered by Redis, acts as a dynamic catalog of index services


![image](https://github.com/EugeneRomanov/hardml_final/assets/72860505/ba0c0ead-efb9-4950-aab7-9dafbf1ed5e5)


# Indexes update

![image](https://github.com/EugeneRomanov/hardml_final/assets/72860505/49ac2a4f-739e-4a68-a3ad-3e8a6a96b61b)


# CI/CD

1. Build QASearch Docker Images: Builds Docker images for QASearch services (ranker, embedder, gateway, indexes) based on Dockerfiles
2. Execute build and deploy scripts from utils directory: Navigates to the utils directory and executes any custom build and deploy scripts
3. Run QASearch Tests: Executes tests to ensure the quality and functionality of QASearch services

   ![image](https://github.com/EugeneRomanov/hardml_final/assets/72860505/f5348f30-279c-4ba6-90f8-5ef187808783)


