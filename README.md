# hardml_final


Overview
QA Search is a Question-Answer search system designed to elevate your search experience using techniques in Learning to Rank (LTR) with KNRM model. This system goes beyond traditional search methods, combining the power of machine learning with specialized natural language processing to deliver highly relevant and context-aware results

System
Indexes: The Indexes service forms the backbone of QASearch, managing and organizing the vast repository of question-answer pairs

Gateway: The Gateway service serves as the entry point for user queries, orchestrating communication between different services

Ranker: The Ranker service leverages KNRM model to prioritize search results

Embedder: The Embedder service is responsible for create vectorized samples, using use-large model from tf-serving

Service Registry The Service Registry, powered by Redis, acts as a dynamic catalog of index services

