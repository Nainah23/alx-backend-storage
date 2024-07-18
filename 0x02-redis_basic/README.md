# ALX Backend Storage - Redis Basics

## Project Overview

This project is designed to familiarize you with Redis, a powerful in-memory data structure store used as a database, cache, and message broker. You will implement several functionalities using Redis in Python, such as storing and retrieving data, counting method calls, storing function call history, and implementing a web cache with expiration tracking.

## Tasks

### Task 0: Writing Strings to Redis

- **Objective**: Create a `Cache` class to interact with Redis.
- **Key Points**:
  - Initialize a Redis client and flush the database.
  - Implement a `store` method to save data with a random key.
  - Ensure the method supports data types: `str`, `bytes`, `int`, and `float`.
  
### Task 1: Reading from Redis and Recovering Original Type

- **Objective**: Retrieve stored data from Redis and convert it back to its original type.
- **Key Points**:
  - Implement a `get` method that accepts a key and an optional callable for data conversion.
  - Create `get_str` and `get_int` methods for automatic type conversion.

### Task 2: Incrementing Values

- **Objective**: Track the number of times methods are called.
- **Key Points**:
  - Create a `count_calls` decorator to count method invocations using Redis.
  - Use the method's qualified name as the key for counting.
  - Decorate the `store` method with `count_calls`.

### Task 3: Storing Lists

- **Objective**: Maintain a history of inputs and outputs for a function.
- **Key Points**:
  - Create a `call_history` decorator to store inputs and outputs in Redis lists.
  - Append ":inputs" and ":outputs" to the method's qualified name to form Redis keys.
  - Decorate the `store` method with `call_history`.

### Task 4: Retrieving Lists

- **Objective**: Display the history of calls for a particular function.
- **Key Points**:
  - Implement a `replay` function to print the history of function calls.
  - Use `lrange` and `zip` to retrieve and display inputs and outputs.

### Task 5: Implementing an Expiring Web Cache and Tracker (Advanced)

- **Objective**: Implement a caching system for web pages with expiration tracking.
- **Key Points**:
  - Create a `get_page` function to fetch and cache HTML content of a URL.
  - Track access counts for each URL.
  - Cache the content with a 10-second expiration time.

## Repository Structure

- **GitHub repository**: `alx-backend-storage`
- **Directories**:
  - `0x02-redis_basic`: Contains tasks 0 to 4.
  - `File: exercise.py`: Main implementation file for tasks 0 to 4.
  - `File: web.py`: Implementation file for task 5.

## Usage

1. **Setting Up Redis**:
   - Ensure you have Redis installed and running on your system.
   - Install the `redis` Python package using `pip install redis`.

2. **Running the Project**:
   - Implement the classes and methods as per the tasks.
   - Use the provided `main.py` scripts to test your implementations.
   - For task 5, use an external URL to test caching and expiration.

## Conclusion
