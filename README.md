# kubernetes-handson
In this handson, I will demonstrate a simple public web application that interacts with its database
1) MongoDb
2) Mongo express
   
![image](https://github.com/Babaji42O/kubernetes-handson/assets/80086380/3505a698-9ece-4438-8335-c9e752f7846a)

# Codeplan:
 1) Create mongodb deployment. 
 2) In order to talk to this pod, create an internal service (only components in same cluster can talk to it)
 3) Create MongoExpress deployment.
 4) Create Configmap that would require by MongoExpress Deployment (step 2) to talk with MongoDB pod. It will store ENV variables and MongoDB URL
 5) Create Secret to store DB user, DB password
 6) External service in order to make mongo express accessible from external web browser. External URL : "http://< IP address of the Node >: port of external service "
 ![image](https://github.com/Babaji42O/kubernetes-handson/assets/80086380/f6643290-de62-4523-a902-f5552063c448)

So with this setup, the request flow will look like this -
![image](https://github.com/Babaji42O/kubernetes-handson/assets/80086380/4632541a-9ad7-4e91-85d5-b439e1736513)

A) Request comes from the browser and 
B) it goes to external service of Mongo Express which will then 
C) forward it the Express pod. 
D) The pod will then connect to internal service of MongoDB that's basically the DB URL and 
E) it will forward it to Mongo DB 
F) where it will authenticate the request using credentials in the secret 
