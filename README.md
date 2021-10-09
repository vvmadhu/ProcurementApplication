# ProcurementApplication
Here is the flow of procurement Application

![image](https://user-images.githubusercontent.com/4353354/136660769-cfbe0bd6-71de-47bb-b41e-3df7cf5da647.png)

### Technical Components
1. Postgre is a relational database to persist data
2. Springboot application with spring data will provide REST APIs for accessing data to perform CRUD operation
3. Java AWT/Swing application as client application to feed data access REST APIs hosted in AWS

### API Flow (Server Component)
1. APIs will be developed with REST standards using springboot application
2. It will be a single deployment component having CRUD operations for each data model defined in procurement system
3. Each model will be havng 4 APIs to support CRUD action
4. Aggregation layer will be added for any kind of aggregation functionality
5. Spring data will be used for data access layer, helps to decouple the tight bounding with underlying database 
6. These APIs can be exposed either through a API Gate or can be directly exposed

### Client Flow
1. Client application is a standalone application, and it needs to be installed as a library in each client system (be it online or offline system)
2. This applicaton can be java swing based application, will make REST calls to server component for a data-day business activities
3. Application will maintain local copy of the data for a offline functionality, using <b>in</b> directory and an <b>out</b> directory for offline updates. Details of this functionality provided below
![image](https://user-images.githubusercontent.com/4353354/136665269-1121bd71-2c00-4911-b014-e9c3919de17e.png)
powered by mermaid


<graph TD> 
<A[client request] --> B{online?} B --> |Yes| C[Online]  C --> D{action?} D --> |read| >E1[Update data from outfile to server if any] E1 --> E2[Refresh from server to local copy/infile] E2 --> E3[read from local copy/infile and display] E3 --> Z[END] D --> |update| F1[Update data from outfile to server if any] F1 --> F2[followed by current requested data] F2 --> F3[Refresh from server to local copy/infile] F3 --> Z B --> |No| G[Offline] G --> H{action?} H --> |read| I[read from local copy/infile and display] I --> Z H --> |update| J[Update/append data to outfile data] J --> Z>
