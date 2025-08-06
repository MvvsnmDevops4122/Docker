
=====================================================================================================================

                                                   Docker Compose

======================================================================================================================                                         
# Docker Compose
=================

👉 Docker Compose is a tool used to define and run multi-container Docker applications.

👉 It is written in **YAML** (Yet Another Markup Language) format.

## ✅ Default Compose File Names:

- `docker-compose.yaml`  
- `docker-compose.yml`  
- `compose.yaml`  
- `compose.yml`  

## 🧪 Example: Spring Boot App with MongoDB (Without Compose)

docker network create jio

docker run -d --name mongo -v jiovolume:/data/db --network jio \
-e MONGO_INITDB_ROOT_USERNAME=devdb \
-e MONGO_INITDB_ROOT_PASSWORD=dev@123 \
mongo

docker run -d --name springapp --network jio -p 8080:8080 \
-e MONGO_DB_HOSTNAME=mongo \
-e MONGO_DB_USERNAME=devdb \
-e MONGO_DB_PASSWORD=dev@123 \
springimage


💡 **Interview Q:**
====================

**Q:** App or DB - which one do we bring down first?
**A:** ✔️ App


## 📝 How to Write a Docker Compose File?
===========================================

Basic structure:
----------------

version:
services:
volumes:
networks:

## 🧾 Example Docker Compose File
======================================

```yaml
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
      - jiovolume:/data/db   # ✅ Persistent data volume

networks:
  jio:
    driver: bridge

volumes:
  jiovolume:
```

---

## 💾 How to Save the File?
===========================

Save it as any of the following (most commonly `docker-compose.yaml`):

docker-compose.yaml

## 🔍 How to Check Docker Compose Version?
===========================================

docker-compose version

## 🔧 How to Install Docker Compose?
=====================================

sudo apt install docker-compose -y

## ✅ How to Validate the Compose File?
========================================

docker-compose config

## 🚀 How to Start Services with Compose?
==========================================

docker-compose up -d

## ⛔ How to Stop/Remove All Services?
======================================

docker-compose down

## 📋 How to View Running Containers?
=====================================

docker-compose ps -a

## 📦 How to See Used Docker Images?
=====================================

docker-compose images
