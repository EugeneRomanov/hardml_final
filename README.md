# hardml_final


# Introduction

QA Search System is a powerful tool for finding relevant documents quickly and efficiently. It uses advanced matematical and ml algorithms to analyze the text of documents and match them to your search queries, ensuring that you get the most accurate results possible.

When using QA Search System, it is important to enter your search query in a clear and concise manner. This will help the system to understand what you are looking for and return the most relevant results. You can also use advanced search options to narrow down your results by date, author, or other criteria.

Once you have entered your search query, QA Search System will begin scanning through its database of documents to find matches. It will rank the results based on their relevance to your query, with the most relevant documents appearing at the top of the list.

Overall, QA Search System is an invaluable tool for anyone looking to find relevant documents quickly and efficiently. Its advanced algorithms and user-friendly interface make it easy to use, even for those who are not tech-savvy. 

However, the construction and system design of such a system is not a simple matter. This repository is an example of what it might look like

# Requirements for starting the system
- A few virtual machines with Docker.
- The host machine.
- Tool for deployment and update scenarios.

# System

1. Gateaway: service through which all user requests pass.
2. Ranker: ml moder for ranking search results. 
3. Embedder: ml moder for embedding users requests. 
4. Indexes: service for managing and organizing the vast repository of question-answer pairs 
5. Service Registery: service holds URLs, port numbers, and cluster centers for each index.

Each component of such a system can be deployed using Docker Swarm for easy scaling and use.

![image](https://github.com/EugeneRomanov/hardml_final/assets/72860505/4df8e619-3cb5-45e5-a210-c68c29ef3ea4)


# System parameters

1. Environment Variables.
To start the system, you first need to add environmental variables to the config file.
* Swarm manager: IP adressess of Docker Swarm Managers. 
* Redis parameters: host, port and password for Redis. 
* Docker registry: IP adressess for the Docker registry.
* Ports: unique port values for embedder, ranker, index and gateaway.
* Hosts: available IP adresses for nodes
* Data and сlusters parameters: generated current information per user request and total number of clusters

2. Data and nodes preparation.
* Preparation QA dataset for system.
* Deffintion settings for nodes and data format.
* Delivery final dataset to nodes.


# Deployment

After preparing the system settings, you can start deploying the system.

* Build images: building images using the Docker registry.
* Indexes depoyment: creating a Docker Swarm service for each cluster using Redis settings adn data and clusters parameters from enviroment variables (config file).
* Services deployment: deployment embedder, ranker and gateaway using parameters from enviroment variables (config file).

Some restrictions may be placed on the operation of this system so that the system operates efficiently and does not become overloaded.
For example, a limit on the number of messages to the service per minute, restrictions on storing information in the index depending on activity.


# Working system pipeline

1. User make a question request in QA search system.
2. The gateway sevice checks the availability of indexes and data.
3. The gateway sevice sends a request to the embedder service and receives the result back.
4. The gateway sevice operates using the system infrastructure as follows:
* Depending on the location of the cluster index from the original question, a search is performed.
* If the cluster is too far away, the search is not performed.
* If the cluster is close, then a search is performed taking into account the restrictions on the available clusters.
* The cosine distance metric can be used as a cluster and question index metric.
5. The gateway sevice uses a ranker model for ranking and gets the ranked result. Different ML models can be used as a ranker: DSMM, DRMM, K-NRM, Conv-KNRM
6. The user receives the result of the QA system's operation.


# Indexes update

Each index cluster is updated one at a time. The duration of the update process should not affect system downtime. 
Each individual index cluster update occurs as follows: the new version is started first, and then the old version is shut down.

This can also be represented as follows:

1. Launching a new version of the index cluster and registering in the service registry.
2. Two cluster indexes have been working for some time. When a user makes a request, the gateway service selects the closest available cluster index.
3. Checking the stability of the new index cluster. Disabling the old cluster and deleting all data from service registry.


# CI/CD

Sample CI/CD pipeline:

1. Build QASearch Docker Images: Builds Docker images for QASearch services (ranker, embedder, gateway, indexes) based on Dockerfiles
2. Execute build and deploy scripts from utils directory: Navigates to the utils directory and executes any custom build and deploy scripts
3. Run QASearch Tests: Executes tests to ensure the quality and functionality of QASearch services

   ![image](https://github.com/EugeneRomanov/hardml_final/assets/72860505/f5348f30-279c-4ba6-90f8-5ef187808783)


