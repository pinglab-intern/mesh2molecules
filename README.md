# A mapping of  Cardiovascular Disease to Molecular Mechanism with Graph Neural Network 

## Introduction
Cardiovascular disease is one of the most important diseases in the world. People are trying to explore it deeper and deeper for a long time. With the development of big data explosion and artificial Intelligence method, now we have more strategies to help us explore the disease. For medicine data, more and more graph data is produced, which is better to draw the relationship map between entities. The aim of this paper is to explore the cardiovascular diseases related molecular mechanisms following MeSH descriptors using the graph neural network (GNN).

Until now, there are no open source pathway data related to cardiovascular diseases. As a result, we collected them by ourselves. Reactome database is a pathway database which provides intuitive bioinformatics tools for research. As a result, we used the API on the website and applied web crawler strategy to collect the data we needed. Also, we use the Neo4j database, which is a graph database management system, to transfer the data format into what we want. Then we utilize the Cypher query to explore the relationship inside the data we collected and finally set the dataset successfully.

It is well known that the entities, such as pathway, reaction, protein and so on, inside our body are connected with each other tightly. As a result, traditional text data is hard to draw enough information inside the data. On the contrary, graph data is best suitable for this job. Therefore, we apply GNN on our graph data. Based on the various relation types within the pathway, reactions and MeSH descriptors, we utilize heterogeneous graph structure and Relation Graph Convolutional Network (Relational-GCN) to do the prediction job. 

We have two prediction model. Model 1 can predict the high level MeSH descriptor class for each pathway belong to. Model 2 can predict the most possible MeSH descriptors for the pathway belong to. This result can help us identify what kind of disease the exact pathway will affect.

It is the first time for researchers to apply GNN method on pathway data prediction. Not only for the cardiovascular data, with more data and experiments, we can also utilize our model on other important diseases such as cancer in the future. 

## Data Preparation
**1.** Collect all the MeSH Descriptors related to Cardiovascular Disease from MeSH Tree and load the graph data from Reactome website. The related codes can be found at /neo4j.

**2.** Use those MeSH Descriptors to do the web crawler by advanced search from Reactome website to collect all the pathway data belong to each MeSH Descriptors. The related codes can be found at /AdvancedSearch.

**3.** Apply Cypher query to collect reactions and proteins data related to each pathway on Neo4j graph database. And also extract the preceding event reactions information. The related codes can be found at /relationshipExplore.

## Model Build, Train and Test
**1.** Use DGL library to construct the heterogeneous graph on our graph data due to the various edge and node types.

**2.** Use relational Graph Convolutional Networks which information passing functions concludes both edge and node information.

**3.** Build two models, one that can predict the high level MeSH descriptor class for each pathway belong to and the other that can predict the most possible MeSH descriptors for the pathway belong to.

**4.** Cut our dataset into 8:1:1 as train dataset, validation dataset and test dataset. 

**5.** For our prediction result, we achieve 92% and 75% accuracy on our test dataset for model 1 and model 2 respectively.

All the related codes can be found at /DGL

## Overall Pipeline
![png](https://github.com/pinglab-intern/mesh2molecules/tree/master/images/pipeline.png)

## Model Workflow
![png](https://github.com/pinglab-intern/mesh2molecules/tree/master/images/workflow.png)
