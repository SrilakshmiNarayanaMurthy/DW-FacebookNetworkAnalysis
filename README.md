# DW-FacebookNetworkAnalysis
The primary goal of this project is to perform meaningful analytics on the Facebook 
ego-network data using graph NoSQL databases. Social network datasets, such as 
ego-Facebook, contain a rich structure of user connections and metadata that are ideal for 
multi-model analysis. Each user not only has a set of features that describe their interests, 
behaviors but also belongs to social circles that represent community structures. 
In practical scenarios like friend recommendation systems, targeted advertising, or analysis of 
influence spread, the graph-based models can yield valuable insights. Conventional relational 
databases frequently struggle to efficiently manage complex and interlinked data architectures, 
which makes this project an ideal opportunity to investigate the advantages of NoSQL 
databases. Employing Cypher queries in Neo4j, we investigate which users possess comparable 
feature sets, how users are spread across social networks, what the predominant features are 
within a particular group, community intersections, and network motifs that indicate clustering 
tendencies. 
This initiative aims not just to showcase technical skills but also to create a 
learning environment that: 
1.Contrasts NoSQL models with conventional relational database management systems. 
2.Presents graph theory ideas via Neo4j. 
By achieving these objectives, we demonstrate a comprehensive data engineering and analytics 
pipeline that transitions from raw data to insights, constructed entirely with open-source 
technologies and contemporary best practices. 


Creating circles and edges with cypher 
QUERY 
LOAD CSV WITH HEADERS FROM 
'https://raw.githubusercontent.com/ArpanaSinghSJSU/DataWarehouse/refs/head
 s/main/facebook_107circles_reformatted.csv' AS row 
MERGE (ego:user1 {id: 107}) 
MERGE (u:user2 {id: toInteger(row.friend_id)}) 
MERGE (c:Circle {name: row.circle_name, owner: 107}) 
MERGE (u)-[:IN_CIRCLE]->(c) 

<pre> ```cypher LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/ArpanaSinghSJSU/DataWarehouse/refs/heads/main/107.featnames_csvI.csv' AS row WITH DISTINCT row.feature_num AS featnum, row.feat_name AS featname MERGE (:Feature {number: featnum, name: featname}) ``` </pre>


![Screenshot (1472)](https://github.com/user-attachments/assets/85b315d8-f1e6-4d8e-8981-45d261562e9c)

