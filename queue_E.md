# Queue

- A **Queue** is a linear data structure that follows the **First-In-First-Out (FIFO)** principle. In a queue, the first element added is the first one to be removed, similar to a line of people waiting where the person who comes first is served first.

### Characteristics of Queue
- **FIFO Order**: Elements are added at the end (rear) and removed from the front.
- **Operations**:
  - **Enqueue**: Adds an element to the rear of the queue.
  - **Dequeue**: Removes an element from the front.
  - **Peek/Front**: Returns the front element without removing it.
  - **IsEmpty**: Checks if the queue is empty.
  - **Size**: Returns the number of elements in the queue.

### Applications of Queues
Queues are commonly used in:
1. **Task Scheduling**: For example, in operating systems to manage processes.
2. **Data Buffering**: For handling data streams, such as IO buffers.
3. **Breadth-First Search (BFS)** in graph traversal.
4. **Print Spooling**: Managing the order of printing documents.

---
## Example:

A classic real-world problem that can be solved using a queue is the **customer service system** at a bank or support center. Here, customers arrive, wait in line, and are served in a first-come, first-served order. Using a queue data structure, we can simulate this behavior efficiently.

### Problem Statement
Simulate a **customer service system** where customers arrive at different times and join the queue. The system serves each customer in the order they arrived. When a customer is done, the next one in line is served. For simplicity, we assume each customer requires a random time to be served.

### Python Implementation

Here’s a Python program that simulates a customer service queue using the `queue` module. We'll use the `Queue` class from Python’s standard library to handle the FIFO structure.

```python
import queue
import time
import random

# Customer class to represent each customer with an ID and service time
class Customer:
    def __init__(self, customer_id):
        self.customer_id = customer_id
        self.service_time = random.randint(1, 5)  # Random service time between 1-5 seconds

    def __str__(self):
        return f"Customer {self.customer_id} (Service time: {self.service_time}s)"

# CustomerServiceSystem to manage the queue and serve customers
class CustomerServiceSystem:
    def __init__(self):
        self.queue = queue.Queue()  # FIFO queue for customers
        self.customer_id = 1  # Initialize customer ID counter

    def new_customer(self):
        """Add a new customer to the queue."""
        customer = Customer(self.customer_id)
        self.queue.put(customer)
        print(f"New {customer} added to the queue.")
        self.customer_id += 1

    def serve_customer(self):
        """Serve the customer at the front of the queue."""
        if not self.queue.empty():
            customer = self.queue.get()
            print(f"Serving {customer}")
            time.sleep(customer.service_time)  # Simulate service time
            print(f"{customer} served.")
        else:
            print("No customers in the queue.")

    def run_service(self, num_customers):
        """Run the simulation with a given number of customers."""
        for _ in range(num_customers):
            self.new_customer()  # New customer joins the queue
            self.serve_customer()  # Serve the next customer in line

# Run the simulation with 5 customers
if __name__ == "__main__":
    service_system = CustomerServiceSystem()
    service_system.run_service(5)
```

### Explanation
1. **Customer Class**: Represents each customer with a unique ID and a randomly assigned service time.
2. **CustomerServiceSystem Class**:
   - The `new_customer` method creates a new customer and adds them to the queue.
   - The `serve_customer` method removes a customer from the front of the queue and serves them (simulated by `time.sleep()` for the service duration).
   - The `run_service` method manages adding and serving a predefined number of customers.

3. **Simulation Execution**: The program runs by creating five customers and serving them one by one.

### Output
The output will show each customer being added to the queue and then served in the order they arrived, with their service time printed accordingly.

This simple queue-based system could be further expanded to handle additional scenarios, such as handling multiple queues for different priority levels or setting up conditions for new customers joining the queue dynamically.