# A mapping of  Cardiovascular Disease to Molecular Mechanism with Graph Neural Network 

## Introduction
This is an GCN(Graph Convoluted Network) project to classify every pathway related to cardiovascular diseases into different sub-class diseases. Because entities, such as pathway, reaction, protein and so on, inside our body are connected with each other tightly, we could build a graph dataset to store them and use the information inside the graph to give the right class for every pathway. It is a supervised learning model. We need class labels for part of the pathways and use them and the graph to predict the rest of the pathways. This project will be helpful to precision medicine. When a pathway damage is detected, we can know what kind of precise diseases the patient has. 

### Node Classification
We have two prediction model. Model 1 can predict the high level sub-class diseases for each pathway belong to. Model 2 can predict the most possible precise diseases for the pathway belong to. This result can help us identify what kind of disease the exact pathway will affect.

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
