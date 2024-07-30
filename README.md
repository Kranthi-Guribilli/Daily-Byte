## Software Architecture Patterns

### Event-Driven Architecture
- **Components:** Event Producer, Event Broker, Event Consumers.
- **Flow:**
  - The Event Producer generates events.
  - Events are sent to the Event Broker, which categorizes them into topics.
  - Event Consumers subscribe to specific topics and process the events.
- **Use Cases:** Real-time applications, microservices communication.

### Layered (N-Tier) Architecture
- **Layers:**
  - **Presentation Layer:** User interface.
  - **Business/Application Layer:** Business logic.
  -  **Data Access Layer:** Data access logic.
  - **Persistence Layer:** Data storage.
  - **Infrastructure Layer:** Underlying infrastructure and system services.
- **Flow:** Data flows from the user interface through each layer, and responses flow back up.
- **Use Cases:** Enterprise applications, web applications.

### Monolithic Architecture
- **Components:** Single application containing multiple functional modules (User Posts, User Comments, Groups, Photo Storage, Live Streaming).
- **Flow:** All modules are tightly coupled and run as a single service.
- **Use Cases:** Simple applications, early-stage startups.

### Microservices Architecture
- **Components:** Independent services (Catalog, Shopping Cart, Discount, Ordering) communicating through an API Gateway.
- **Flow:** Users interact with the API Gateway, which routes requests to the appropriate microservice.
- **Use Cases:** Large-scale enterprise applications, applications requiring independent deployment of services.

### Model-View-Controller (MVC) Architecture
- **Components:**
  - **Model:** Manages data and business logic.
  - **View:** Presents data to the user.
  - **Controller:** Handles user input and updates the model.
- **Flow:** User actions are handled by the controller, which updates the model. The view then updates to reflect the new data.
- **Use Cases:** Web applications, desktop GUI applications.

### Master-Slave Architecture
- **Components:** Master database, Slave databases, Servers.
- **Flow:**
  - The master database handles write and read requests.
  - Updates are replicated to slave databases.
  - Slave databases handle read requests.
- **Use Cases:** Data replication, load balancing, read-heavy applications.
