## About

This is example of **Product Catalog Search Project**, was build using `React.js` `Springboot 2.7` `Spring Cloud Gateway` `Eureka Discovery` `Spring Security` `Redis` `MySql` `RabbitMq` `Elastic Search` `Docker` `Github Action` `VPS Ubuntu` `Docker compose` `Portainer`


## Context Diagram

## Container Diagram
![image](https://github.com/elastic-search-product-catalog/.github/assets/11941308/3c94b7a8-5159-4987-9787-69de2fb7c207)

- **Web**
  - **Web Seller**
    ```
    - this is a frontend (web) for manage all seller data likes (category, brand, product, selling price, stock, seller, customer)
    ```
  - **Web Customer**
    ```
    - this is a front end (web) for searching product catalog
    ```
  - **Eureka Discovery Service**
  ```
  - this is an service registry, build using eureka discovery service (springcloud)
  - this service used for automate register all services
  - this service used when all services want to communicates each others 
  ```
- **Spring Cloud Gateway**
  ```
  - this is an API Gateway, build using spring cloud
  - used for routing the endpoints to spesifiect service
  - used for validate & middleware the api request
  - used for limmiting the api request    
  ```
- **Redis**
  ```
  - this is an memory cache, build using redis
  - redis will integrated to (gateway service and auth service) 
  - redis will save the tokens when login apis was requested
  - redis will drop all keys (datas) when the life times was expired
  - redis will used on authenticate & authorization process  
  ```  
- **Auth Service**
  ```
  - this is an authorizartion & authentication service, build using springboot, spring security  
  - this service will integrated to MySql, for crud data (user, role, permission, access menus)
  - this service will integrated to redis, for store and read datas when authenticate & authorization process
  - this service will integrated to discovery service as client  
  ```
- **Main Service**
  ```
  - this is an main service, build using springboot
  - this service had modules like (category, brand, product, stock, seller, customer)
  - this service will integrated to MySql for CRUD datas (category, brand, product, stock, seller, customer)
  - this service will integrated to RabbitMq for publishing the datas (category, brand, product, stock, seller)
  ```
- **Search Service**
  ```
  - this is an search service, build using springboot
  - this service will integrated to RabbitMq for consume the datas (category, brand, product, stock, seller)
  - this service will integrated to elastic search for CRUD data (product catalog)
  - the product catalog is an data combination of (category, brand, product, selling price, stock, seller)
  - this service will consume by customer, when customer hit api, for search the product catalog
  ```
- **MySql**
  ```
  - this is RDBMS database, build using MySql
  - this database for storing datas (category, brand, product, selling price, stock, seller, customer) 
  ```
- **Rabbit MQ**
  ```
  - this is an Message Broker, build using Rabbit MQ
  - rabbit mq, had features queue for storing data from publisher (main service)
  - the consumer service (search service) will consume / get data to queue
  - this service will integrated to (main service & search service)
  ```    
- **Elastic Search**
  ```
  - this is search engine, build using Elastic Search
  - this service, used for storing product catalog data
  - this service will integrated to search service 
  ```

## Component Diagram  



