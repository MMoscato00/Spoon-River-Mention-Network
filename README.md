# Spoon-River-Mention-Network
This repository contains all datasets created for the character network analysis of the Spoon River Anthology, conducted as part of a Master’s thesis project in Digital and Public Humanities titled “Analysing and Reaccessing Texts through Character Interaction Networks: The Interpoetic Narrative of the Spoon River Anthology" written by Mattia Moscato (Hi!). 

The three datasets are as follows:
1. Sentiment Analysis Data: Data obtained from the sentiment analysis of poems that reference characters/poems from the anthology, inspired by residents of Lewistown.
2. Interaction Data: Data concerning mention interactions between characters/poems, represented as network edges with attributes including Source and Target Poem, Edition, whether the referenced poem is inspired by a Lewistown resident, Recorded Sentiment Value, and Type of Mention.
3. Poem Data: Data concerning poems in the form of network nodes, with the same attributes as above, plus an ID indicating the poem's position in the anthology's index.

To load the node and edge data into a directed network using NetworkX, you can use the following Python code:

```python
import pandas as pd
import networkx as nx

nodes_df = pd.read_excel('nodes_attributes.xlsx')
edges_df = pd.read_excel('edges_attributes.xlsx')

G = nx.DiGraph()

for _, row in nodes_df.iterrows():
    G.add_node(row['Poems'], 
               Id=row['Id'], 
               Inspiration=row['Inspiration'], 
               Edition=row['Edition'])

for _, row in edges_df.iterrows():
    G.add_edge(row['Source'], 
               row['Target'], 
               Source_Mention_Type=row['Source_Mention_Type'], 
               Edition_Source=row['Edition_Source'], 
               Sentiment_value=row['Sentiment_value_Lewistown_From Source toTarget'])

```
If you are using Google Colab, you can use the following code:

```python
import pandas as pd
import networkx as nx
from google.colab import files

uploaded = files.upload()

nodes_df = pd.read_excel('nodes_attributes.xlsx')
edges_df = pd.read_excel('edges_attributes.xlsx')

G = nx.DiGraph()

for _, row in nodes_df.iterrows():
    G.add_node(row['Poems'], 
               Id=row['Id'], 
               Inspiration=row['Inspiration'], 
               Edition=row['Edition'])

for _, row in edges_df.iterrows():
    G.add_edge(row['Source'], 
               row['Target'], 
               Source_Mention_Type=row['Source_Mention_Type'], 
               Edition_Source=row['Edition_Source'], 
               Sentiment_value=row['Sentiment_value_Lewistown_From Source toTarget'])

```

At this point, you can use libraries for data visualization or extract data from the directed network. 
Below, I have included the libraries used and links to their official documentation:
- NetworkX:https://networkx.org/documentation/stable/reference/index.html
- Pyvis: https://pyvis.readthedocs.io/en/latest/
- Matplotlib.pyplot: https://matplotlib.org/3.5.3/api/_as_gen/matplotlib.pyplot.html
- Numpy: https://numpy.org/doc/stable/
- Pandas: https://pandas.pydata.org/docs/

If you encounter issues using these libraries, I recommend the following valuable YouTube videos:
- Network of The Witcher | Relationship Extraction & Network Analysis with Spacy & NetworkX: https://www.youtube.com/watch?v=fAHkJ_Dhr50&t=1234s    by Thu Vu data analytics
- Introduction to Network Analysis by Analyzing Characters in Harry Potter Fanfiction - Sara Jakša: https://www.youtube.com/watch?v=UYxX4c97iAc     by Python Italia

To return to the project web page click this link: https://mmoscato00.github.io/MentionNetworkSpoonRiver/
