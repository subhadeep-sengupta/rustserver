# Multi-Threaded Web Server

A concurrent web server built in Rust, developed as part of the final project in "The Rust Programming Language" book. This project demonstrates core Rust concepts including ownership, concurrency, and thread pools.

## Overview

This web server handles multiple client connections simultaneously using a thread pool pattern. It processes HTTP requests, serves responses, and gracefully handles client connections without blocking. Perfect for understanding how production web servers manage concurrent requests.

## Key Features

- Multi-threaded Architecture - Processes multiple client connections concurrently using a thread pool

- HTTP Request Handling - Parses and responds to basic HTTP GET requests

- Connection Management - Gracefully handles client disconnections

- Configurable Thread Pool - Adjustable worker threads for different workloads

- Graceful Shutdown - Cleanly terminates all threads on server shutdown

## Prerequisites

Rust 1.56+ - Install Rust

Git - For cloning the repository

A terminal/command prompt - To run the server

Installation
Clone the Repository
bash

# Clone the repository to your local machine

git clone <https://github.com/subhadeep-sengupta/rustserver.git>

# Navigate into the project directory

cd multithreaded-web-server

### Building the Project

```bash
cargo build
```

### Build the optimized release version (recommended for production)

cargo build --release
Running the Server
bash

# Run the development build

cargo run

# Or run the optimized release build

cargo run --release
The server will start and listen on 127.0.0.1:7878 (localhost on port 7878).

Testing the Server
Once running, you can test it in another terminal:

bash

# Test with curl

curl <http://127.0.0.1:7878/>

# Or open in your browser

# Navigate to: <http://localhost:7878/>

Expected responses:

/ - Returns a success page (HTML)

/sleep - Simulates a slow request (sleeps for a few seconds)

Any other path - Returns a 404 Not Found page

Stopping the Server
Press Ctrl + C in your terminal to gracefully shutdown the server.

Project Structure
text
multithreaded-web-server/
├── src/
│ ├── main.rs # Entry point, server initialization
│ └── lib.rs # ThreadPool implementation and utilities
├── Cargo.toml # Project manifest and dependencies
└── README.md # This file
How It Works
Main Server Loop - Accepts incoming TCP connections

Request Parsing - Reads HTTP request from client

Thread Pool - Assigns request to available worker thread

Response Generation - Builds appropriate HTTP response

Connection Closure - Properly closes connection after response

Configuration
You can adjust the number of worker threads in src/main.rs:

rust
let listener = TcpListener::bind("127.0.0.1:7878").unwrap();
let pool = ThreadPool::new(4); // Change 4 to your desired thread count
Recommended values:

2-4 threads - Development/testing

8-16 threads - Small production workloads

System CPU count - Production deployments
