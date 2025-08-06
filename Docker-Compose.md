
=====================================================================================================================

                                                   Docker Compose

======================================================================================================================                                         
# docker compose
-----------------

👉 Docker Compose is a tool used to define and run multi-container Docker applications.

👉 It is written in **YAML** (Yet Another Markup Language) format.

👉 Default file names:  
-----------------------
  
   ✔️ docker-compose.yaml  

   ✔️ docker-compose.yml 

   ✔️ compose.yaml  

   ✔️ compose.yml


🧪 Example: Spring Boot App with MongoDB
------------------------------------------


docker run -d --name springapp --network jio -p 8080:8080 \
-e MONGO_DB_HOSTNAME=mongo \
-e MONGO_DB_USERNAME=devdb \
-e MONGO_DB_PASSWORD=dev@123 \
springimage

docker run -d --name mongo -v jiovolume:/data/db --network jio \
-e MONGO_INITDB_ROOT_USERNAME=devdb \
-e MONGO_INITDB_ROOT_PASSWORD=dev@123 \
mongo


💡 **Interview Q:** App or DB - which one do we bring down first?
✔️ **Ans:** App


📝 How to write a Docker Compose file?
=======================================

version:
services:
volumes:
networks:



🧾 Example Docker Compose File
------------------------------

version: "3"
services:
  spring-boot-app:
    image: springimage
    ports:
      - 8080:8080
    depends_on:
      - mongo
    networks:
      - jio
    environment:
      - MONGO_DB_HOSTNAME=mongo
      - MONGO_INITDB_ROOT_USERNAME=devdb
      - MONGO_DB_PASSWORD=dev@123

  mongo:
    image: mongo
    networks:
      - jio
    environment:
      - MONGO_INITDB_ROOT_USERNAME=devdb
      - MONGO_INITDB_ROOT_PASSWORD=dev@123
    volumes:
      - jiovolume:/data/db   # ✅ FIXED here

networks:
  jio:
    driver: bridge

volumes:
  jiovolume:





💾 How to save the file?
-------------------------

Save as: docker-compose.yaml


🔍 How to check the version?
----------------------------

docker-compose version


🔧 How to install Docker Compose?
--------------------------------

sudo apt install docker-compose


✅ How to validate the syntax?
------------------------------

docker-compose config


🚀 How to run/up Docker Compose?
------------------------------

docker-compose up -d


⛔ How to stop/down?
---------------------

docker-compose down


📋 How to view running containers?
---------------------------------

docker-compose ps -a


📦 How to see the images?
-------------------------

docker-compose images



