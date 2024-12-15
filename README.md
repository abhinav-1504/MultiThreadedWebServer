# Multi-Threaded Client-Server in Java

This repository contains examples of implementing client-server communication using Java sockets. It demonstrates various techniques, such as multithreading, thread pooling, and event-driven architectures, to handle concurrent client connections efficiently.

## Key Features

- **Basic Client-Server Communication**: Demonstrates a simple message exchange between a client and a server.
- **Multithreaded Server**: Handles multiple client connections by spawning a new thread for each connection.
- **Thread Pool Server**: Optimized server implementation using a fixed thread pool to manage resources efficiently.
- **Single-Threaded Server**: Example of a basic, single-threaded server for minimal use cases.
- **Event-Driven Design**: Illustrates the use of functional interfaces (e.g., `Consumer`) to manage client handling logic.

## Files

### Server Implementations
- **`Server.java`**: 
  - Multithreaded implementation with each client connection handled in its own thread.
  - Thread-pool based implementation for optimized resource management.
  - Basic single-threaded implementation for simple setups.

### Client Implementations
- **`Client.java`**: 
  - Example client programs for connecting to the server and exchanging messages.
  - Demonstrates single-threaded and multi-threaded client implementations.

## Concepts Covered

- **Java Sockets**: Basics of TCP socket programming.
- **Multithreading**: Creating and managing threads for handling concurrent tasks.
- **Thread Pooling**: Using `ExecutorService` to optimize thread usage.
- **Blocking vs Non-blocking I/O**: Understanding thread blocking during I/O operations.
- **Event Loops**: Using functional programming to define event-driven client handling logic.

## Getting Started

### Prerequisites

- Java Development Kit (JDK) 8 or higher.
- Basic understanding of Java programming and multithreading.
- Apache JMeter for performance testing (optional).

### Running the Examples

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/java-sockets-multithreading.git
   cd java-sockets-multithreading
   ```

2. Compile the code:
   ```bash
   javac *.java
   ```

3. Start the server:
   ```bash
   java Server
   ```

4. Run the client:
   ```bash
   java Client
   ```

5. (Optional) Adjust the number of threads in the thread pool or the number of clients in the client program for testing scalability.

6. Use **Apache JMeter** to simulate a high number of client requests and analyze the server's performance. Create a test plan in JMeter to send multiple concurrent requests to the server and measure metrics such as latency, throughput, and error rate.

## Usage

- Experiment with different server implementations to understand the trade-offs between single-threaded, multithreaded, and thread-pooled designs.
- Modify the client code to test various message formats and communication patterns.
- I tested 1 million client requests and conducted performance testing using **Apache JMeter** to showcase the scalability and robustness of the implementations.

## Key Points

- **Port**: The server listens on port `8010`. Ensure this port is open on your machine.
- **Timeouts**: Some server implementations include a timeout (`setSoTimeout`) for inactive connections.
- **Thread Safety**: The examples highlight the importance of managing threads in a multi-client scenario.
- **Performance Testing**: Leverage JMeter to validate the server's ability to handle a large number of concurrent requests efficiently.

## Screenshots

### Server Output Example
```
Server is listening on port 8010
Connected to /127.0.0.1
```

### Client Output Example
```
Response from Server Hello from server /127.0.0.1
```

## Acknowledgments

- Inspired by the foundational concepts of socket programming and multithreading in Java.
- Designed to provide hands-on examples for learning and experimentation.
- Performance testing insights were gained using **Apache JMeter**.

---

Feel free to contribute by submitting issues or pull requests!
