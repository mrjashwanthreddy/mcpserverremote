# Spring AI MCP Server (HTTP/SSE)

![Java](https://img.shields.io/badge/Java-21-orange?style=flat-square&logo=openjdk)
![Spring AI](https://img.shields.io/badge/Spring%20Boot-3.5.9-green?style=flat-square&logo=spring)
![Spring AI](https://img.shields.io/badge/Spring%20AI-1.1.2-green?style=flat-square&logo=spring)
![MCP](https://img.shields.io/badge/Protocol-MCP-blue?style=flat-square)

This repository contains a **Model Context Protocol (MCP) Server** implemented using Spring AI. Unlike standard local servers, this implementation uses **Server-Sent Events (SSE)** over HTTP, allowing it to be accessed remotely or across a network.

## 👤 Author

**Jashwanth Reddy**

* **GitHub**: [@mrjashwanthreddy](https://github.com/mrjashwanthreddy)
* **LinkedIn**: [@jashwanth-java-developer](https://www.linkedin.com/in/jashwanth-java-developer/)
* **Instagram**: [@mrjashwanthreddy](https://www.instagram.com/mr.jashwanthreddy/)

## 📖 Overview

This server exposes tools and resources over a standard web port (default: 8080). This architecture is ideal for distributed systems where your LLM Client (the "brain") runs on one machine (or container) and needs to access tools hosted on a different machine/microservice.

* **Transport**: HTTP (Server-Sent Events)
* **Connection**: Network-based (e.g., `http://localhost:8080`)

## 🚀 Features

* **Remote Accessibility**: Can be deployed as a standard web service/microservice.
* **Asynchronous Communication**: Uses SSE for efficient, streamable communication with the client.
* **Spring Boot Web**: Built on the robust Spring Web MVC stack.
* **Tool Exposure**: (Add description of tools here, e.g., *Exposes remote APIs, database lookups, etc.*)

## 🛠️ Prerequisites

* **Java 21**
* **Spring Boot 3.5.9**
* **Spring AI 1.1.2**
* **Maven**

## ⚙️ Installation & Setup

1.  **Clone the Repository**
    ```bash
    git clone [https://github.com/mrjashwanthreddy/mcpserverremote.git](https://github.com/mrjashwanthreddy/mcpserverremote.git)
    cd mcpserverremote
    ```

2.  **Build the Application**
    ```bash
    ./mvnw clean package
    ```

3.  **Run the Server**
    ```bash
    ./mvnw spring-boot:run
    ```

    The server will start (typically on port `8080`).

## 🔌 How to Connect (Client Configuration)

To use this server, you need an **MCP Client** configured to point to this server's URL.

### Client Configuration Example
If you are using the [Spring AI MCP Client](https://github.com/mrjashwanthreddy/mcpclient), configure it as follows:

**`application.properties` (in your Client App):**

```properties
# Enable HTTP Client
spring.ai.mcp.client.type=http

# Point to this server's running URL
spring.ai.mcp.client.http.base-url=http://localhost:8080(use your port here)
spring.ai.mcp.client.http.timeout=10s