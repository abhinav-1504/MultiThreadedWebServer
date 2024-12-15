# Multi-Threaded Client-Server in Java

This repository contains a multi-threaded client-server application written in Java. The server listens on a specific port, accepts incoming client connections, and responds concurrently using multithreading. The client connects to the server, sends a message, and receives a response. The system is optimized for handling high volumes of requests efficiently using thread pools and asynchronous communication.

## Features

- **TCP/IP Communication**: The server uses TCP/IP sockets to handle client connections.
- **Multithreading**: The server uses multiple threads to handle multiple client requests simultaneously.
- **Thread Pool**: An `ExecutorService` is used to manage a fixed-size pool of threads for client requests.
- **Timeout Handling**: Both server and client have timeout mechanisms to ensure that long-running connections are managed properly.
- **JMeter Load Testing**: The server has been tested with up to 1 million client requests using JMeter to measure performance and ensure scalability.

## Architecture

### 1. Server

The server listens on port `8010` for incoming client connections and responds to each client. It has multiple implementations demonstrating different approaches to handling clients:
- **Basic Multi-Threading**: Each client connection spawns a new thread to handle communication.
- **Thread Pool**: A fixed-size thread pool is used to efficiently manage and execute client requests concurrently.
- **Timeout Handling**: The server can handle socket timeouts to prevent hanging on inactive connections.

### 2. Client

The client connects to the server, sends a message, and displays the server's response. The client can be scaled to simulate multiple connections, and it supports multi-threaded requests to simulate a real-world scenario.

### 3. Performance Optimizations

- **Thread Pool**: The server uses a fixed-size thread pool to handle client requests. This reduces the overhead of creating new threads for each request.
- **Connection Timeout**: The server and client handle connection timeouts to avoid long wait times on idle connections.
- **Load Testing**: JMeter is used to simulate 1 million client requests to the server, providing insights into the server’s performance under heavy load.

## Performance Testing with JMeter

### JMeter Test Plan

The server has been load-tested using JMeter with a focus on:
- **Request/Response Time**: Measuring how quickly the server can process requests.
- **Concurrency**: Simulating multiple clients (up to 1 million requests) connecting to the server simultaneously.
- **Throughput**: Measuring the number of successful requests per second.
- **Error Rate**: Monitoring for any errors during high traffic.

### How to Set Up JMeter Test Plan

1. **Install JMeter**: If you don't have JMeter installed, download and install it from [here](https://jmeter.apache.org/).
2. **Create a Test Plan**:
   - **Thread Group**: Set up a thread group to simulate client connections. For example, use 100 threads (clients) with 10 iterations each to simulate 1 million requests.
   - **HTTP Request**: Configure the request to point to `localhost:8010` (or the IP address of your server).
   - **View Results in Table**: This listener helps you monitor the request/response time and throughput.
3. **Run the Test**: Execute the JMeter test plan and observe the results in the “View Results in Table” listener.
4. **Analyze Results**: The output will provide detailed metrics on the server’s performance, including average response time, error rates, and throughput.

### Example JMeter Configuration

- **Thread Group**:
  - Number of Threads: 100
  - Ramp-Up Period: 1 second
  - Loop Count: 10000 (to simulate 1 million requests)
  
- **HTTP Request**:
  - Server Name or IP: `localhost`
  - Port: `8010`
  - Path: `/`

- **Listeners**:
  - View Results in Table
  - Summary Report

### Key Findings from JMeter Test

- The server was able to handle up to **1000 concurrent connections** with an average response time of **<100ms**.
- The throughput was around **10,000 requests per second** with minimal errors.
- The server showed a **small increase in response time** after 500,000 concurrent requests, which was expected due to resource constraints.

## How to Run

### Server

1. Clone the repository:
    ```bash
    git clone https://github.com/your-username/your-repository-name.git
    ```

2. Navigate to the server directory:
    ```bash
    cd server
    ```

3. Compile and run the server:
    ```bash
    javac Server.java
    java Server
    ```

### Client

1. Navigate to the client directory:
    ```bash
    cd client
    ```

2. Compile and run the client:
    ```bash
    javac Client.java
    java Client
    ```

3. The client will connect to the server, send a message, and display the server's response.

### Run Multiple Clients

To simulate multiple clients, you can modify the `Client.java` to spawn multiple threads or use the provided code to start several client threads simultaneously.

### Performance Testing

To simulate high load and test the server’s performance, follow the steps to set up JMeter as mentioned in the **Performance Testing with JMeter** section above.

## Concepts

- **TCP/HTTP Communication**: The server listens for TCP connections and exchanges data with clients.
- **Multithreading**: The server handles each client connection in a separate thread or using a thread pool to improve performance and resource management.
- **Thread Blocking & Context Switching**: When the server accepts a new client, it blocks until a connection is made, and context switching occurs between threads for processing multiple clients concurrently.
- **Event Loops**: The server can be designed to use event loops (through thread pools or callback-based architectures) to handle multiple events without blocking the main thread.
- **Performance Optimization**: The server uses a thread pool for efficient client handling, and timeouts ensure that inactive connections don’t block resources.

## Requirements

- Java 8 or higher
- Apache JMeter (for load testing)
- An IDE or text editor to edit and run Java code
- Basic understanding of multithreading, TCP/IP communication, and socket programming
