Forked from kasvith/simple-microservices-example

https://github.com/jibril101/simple-microservice-example

Go to the following ip to see the application(DNS currently not working properly(most liekly because no ingress is used))
http://34.94.37.97/

The CI/CD pipeline was built using Github Actions

It builds 3 different services
FrontendApplication(htmls,javacript) using npm served on nginx 
Gateway(just a simple gateway application using express)
QuoteService(python flask application) that serves quotes

When you push to master, dev(branches set for now) 
- runs necessary builds for application
- builds the docker images
- pushes to quay.io/jibril101/$(repo)
- deploys to GKE 

The frontend service is currently exposed by service loadbalancer type. 
I had some issues with setting up my ingresss resources so I used a lb type
for a quick fix for the time being.

I am having some issues with DNS aswell since lb service type doesnt do https by default, I need ingress

Go to the following IP as my dns is messed up atm

http://34.94.37.97/

Go to https://github.com/jibril101/simple-microservice-example
- add a change to FrontendApplication/src/index.html and push to see changes
