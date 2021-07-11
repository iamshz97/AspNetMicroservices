# Docker X MongoDb set up 

- [Docker X MongoDb set up](#docker-x-mongodb-set-up)
    - [1. List running containers](#1-list-running-containers)
    - [2. Specify mongo container `shopping-mongo` for under port `27017` locally as well as under docker image in detatched mode `-d` .](#2-specify-mongo-container-shopping-mongo-for-under-port-27017-locally-as-well-as-under-docker-image-in-detatched-mode--d-)
    - [3. Check logs for created mongo container](#3-check-logs-for-created-mongo-container)
    - [4. Execute created mongo container w/ interactive terminal  `-it`  w/ bash `/bin/bash`](#4-execute-created-mongo-container-w-interactive-terminal---it--w-bash-binbash)
    - [5. Run mongo shell](#5-run-mongo-shell)
    - [5.1. Show databases under mongo container](#51-show-databases-under-mongo-container)
    - [5.2 Create mongo database](#52-create-mongo-database)
    - [5.2 Create collection inside database](#52-create-collection-inside-database)
    - [5.3 Add data](#53-add-data)
    - [5.4 View data](#54-view-data)
    - [5.5 Delete products](#55-delete-products)
    - [5.6 Show databases](#56-show-databases)
    - [5.7 Show collections](#57-show-collections)

### 1. List running containers
   ```bash
   docker ps
   ```

### 2. Specify mongo container `shopping-mongo` for under port `27017` locally as well as under docker image in detatched mode `-d` .
   ```bash
   docker run -d -p 27017:27017 --name  shopping-mongo mongo
   ```

### 3. Check logs for created mongo container
   ```bash
   docker logs -f shopping-mongo
   ```

### 4. Execute created mongo container w/ interactive terminal  `-it`  w/ bash `/bin/bash`
   ```bash
   docker exec -it shopping-mongo /bin/bash
   ```

### 5. Run mongo shell
    ```bash
    mongo
    ```

   ### 5.1. Show databases under mongo container
    ```bash
    show dbs
    ```

   ### 5.2 Create mongo database
    ```bash
    use CatalogDb
    ```

   ###  5.2 Create collection inside database
    ```bash
    db.createCollection('Products')
    ```

   ###  5.3 Add data
    ```bash
    db.Products.insertMany([{ 'Name':'Asus Laptop','Category':'Computers', 'Summary':'Summary', 'Description':'Description', 'ImageFile':'ImageFile', 'Price':54.93 }, { 'Name':'HP Laptop','Category':'Computers', 'Summary':'Summary', 'Description':'Description', 'ImageFile':'ImageFile', 'Price':88.93 } ])
    ```

   ###  5.4 View data
    ```bash
    db.Products.find({}).pretty()
    ```

   ###  5.5 Delete products
    ```bash
    db.Products.remove({})
    ```

   ###  5.6 Show databases
    ```bash
    show databases
    ```

   ###  5.7 Show collections
    ```bash
    show collections
    ```

6. Docker compose file
   ```bash
   docker-compose -f .\docker-compose.yml -f .\docker-compose.override.yml up -d
   ```

7. 6. Docker compose down
   ```bash
   docker-compose -f .\docker-compose.yml -f .\docker-compose.override.yml down
   ```