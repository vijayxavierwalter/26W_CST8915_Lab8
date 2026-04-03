Vijay Xavier Walter.     
041276252.     
CST8915 Full-stack Cloud-native Development.      
Winter 2026.      

---

## Demo Video

🎥 [Watch Demo Video] (https://youtu.be/OqkhgxNFrHE)


# Task 2 – Written Explanation

## MongoDB high availability and persistence
MongoDB was updated to improve availability and data persistence. The StatefulSet was changed from 1 replica to 3 replicas so multiple MongoDB pods run in the cluster. A `volumeClaimTemplates` section was added so each MongoDB pod gets its own PersistentVolumeClaim (PVC). This ensures database data is stored on persistent storage and is not lost when a pod restarts.

The MongoDB service was also changed to a **headless service** using `clusterIP: None`. This gives stable DNS names such as `mongodb-0.mongodb`, `mongodb-1.mongodb`, and `mongodb-2.mongodb`, which is required for replica-based deployments and improves availability.

## RabbitMQ persistence
RabbitMQ was updated so queue data and messages are stored persistently. A persistent volume was mounted at `/var/lib/rabbitmq`, which is the directory RabbitMQ uses to store its data. A `volumeClaimTemplates` block was added to create a PVC for the RabbitMQ pod.

The existing ConfigMap mount for RabbitMQ plugins was kept, so the container still loads the required configuration while also storing queue data on persistent storage.

## Azure managed services
A good Azure-managed replacement for self-hosted MongoDB is **Azure Cosmos DB for MongoDB**. Its purpose is to provide a fully managed MongoDB-compatible database service. It is a good fit because it offers built-in scalability, backups, and high availability without managing database pods manually.

A good Azure-managed replacement for RabbitMQ is **Azure Service Bus**. Its purpose is to provide reliable message queuing and messaging between services. It is a good fit because it supports scaling, durability, and availability, while removing the need to manage RabbitMQ infrastructure inside Kubernetes.
