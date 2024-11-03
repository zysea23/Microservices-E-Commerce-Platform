
# 🌐 Spring Boot Microservices Architecture 🌐

## 🛠️ Services Overview 🛠️

- 📦 **Product Service**
- 🛒 **Order Service**
- 📦 **Inventory Service**
- ✉️ **Notification Service**
- 🚪 **API Gateway** (Spring Cloud Gateway MVC)
- 🛍️ **Shop Frontend** (Angular 18)

## ⚙️ Tech Stack ⚙️

- ☕ **Spring Boot**
- 🖼️ **Angular**
- 🗄️ **MongoDB**
- 🗄️ **MySQL**
- 📬 **Kafka**
- 🔑 **Keycloak** (Authentication & Authorization)
- 🧪 **Test Containers** with Wiremock
- 📈 **Grafana Stack** (Prometheus, Grafana, Loki, and Tempo)
- 🔗 **API Gateway** using Spring Cloud Gateway MVC
- 🐳 **Kubernetes**

## 🏛️ Application Architecture

![image](https://github.com/user-attachments/assets/d4ef38bd-8ae5-4cc7-9ac5-7a8e5ec3c969)

## 🚀 Run the Frontend Application

To start the frontend application, use the following commands:

```shell
cd frontend
npm install
npm run start
```

## 🏗️ Build the Backend Services

Build and package the backend services into a Docker container with:

```shell
mvn spring-boot:build-image -DdockerPassword=<your-docker-account-password>
```

This command builds the services, packages them into Docker containers, and pushes them to your Docker Hub account.

## 🖥️ How to Run the Backend Services

### Prerequisites

- Java 21
- Docker
- Kind Cluster - [Installation Guide](https://kind.sigs.k8s.io/docs/user/quick-start/#installation)

### 🌀 Start Kind Cluster

Run the following script to create a kind Kubernetes cluster:

```shell
./k8s/kind/create-kind-cluster.sh
```

This will create a kind cluster and pre-load the required Docker images into the cluster, saving time when deploying the application.

### 🏗️ Deploy the Infrastructure

Use the following command to deploy infrastructure components:

```shell
kubectl apply -f k8s/manifests/infrastructure.yaml
```

### 📦 Deploy the Services

Deploy the application services with:

```shell
kubectl apply -f k8s/manifests/applications.yaml
```

### 🌐 Access the API Gateway

To access the API Gateway, port-forward the gateway service to your local machine:

```shell
kubectl port-forward svc/gateway-service 9000:9000
```

### 🔑 Access the Keycloak Admin Console

To access the Keycloak admin console, port-forward the Keycloak service to your local machine:

```shell
kubectl port-forward svc/keycloak 8080:8080
```

### 📊 Access the Grafana Dashboards

For Grafana dashboards, port-forward the Grafana service:

```shell
kubectl port-forward svc/grafana 3000:3000
```
