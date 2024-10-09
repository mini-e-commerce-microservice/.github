# Mini E-Commerce MicroService

This Mini E-Commerce MicroService project is designed to demonstrate a scalable and modular e-commerce platform using microservices architecture. It includes core functions such as user management, product catalog, order processing, payment integration, and notification services. The project uses **choreography** for inter-service interactions, where each service operates independently and communicates through events that are published and consumed, reducing direct dependencies between services. using terraform infra as code, using docker for container, and using debezium for cdc(change data capture). implement distributed observability. using vault secret for easy management secret and secure

## Services

### 1. User Service
   - **Description**: Manages user registration, profile management, and verification. Ensures secure handling of user data and provides endpoints for users to manage their accounts.
   - **Responsibilities**:
     - **User Registration**: Create and validate new user accounts.
     - **Profile Management**: Allow users to view and update their profile information.
     - **User Verification**: Implement verification processes such as email or phone verification.
   - **Technology**: 
     - **Go**: Implements service logic and APIs.
     - **PostgreSQL**: Stores user data and credentials securely.

### 2. Product Service
   - **Description**: Handles the product catalog, including operations to add, update, and delete products. Provides endpoints for accessing product details and managing inventory.
   - **Responsibilities**:
     - **Catalog Management**: Add, update, and delete products in the catalog.
     - **Inventory Management**: Track and manage product inventory levels.
   - **Technology**:
     - **Go/Java**: Implements service logic and APIs.
     - **MongoDB**: Stores product details and inventory data.

### 3. Order Service
   - **Description**: Manages order creation, updating, and tracking. Handles the lifecycle of customer orders from creation to fulfillment.
   - **Responsibilities**:
     - **Order Management**: Create and update orders, and track order status.
     - **Order Tracking**: Provide endpoints to track the status and history of orders.
   - **Technology**:
     - **Go/Java**: Implements service logic and APIs.
     - **PostgreSQL**: Stores order details and transaction history.

### 4. Payment Service
   - **Description**: Integrates with various payment gateways (e.g., Stripe, PayPal, Xendit, Midtrans) to process financial transactions securely.
   - **Responsibilities**:
     - **Payment Processing**: Handle transactions and integrate with payment gateways.
     - **Transaction Management**: Manage payment-related operations and records.
   - **Technology**:
     - **Go**: Implements service logic and APIs.
     - **Redis**: Caches payment data and improves performance.
     - **PostgreSQL**: Stores transaction records and payment details.

### 5. Shipment Service
   - **Description**: Manages shipment tracking, including creating, updating, and tracking shipments from the warehouse to the customer.
   - **Responsibilities**:
     - **Shipment Management**: Create and update shipment records.
     - **Tracking**: Provide endpoints to track the status of shipments.
   - **Technology**:
     - **Go**: Implements service logic and APIs.
     - **Redis**: Caches shipment data for faster access.
     - **PostgreSQL**: Stores shipment records and tracking information.

### 6. Notification Service
   - **Description**: Sends notifications via various channels such as email, SMS, or push notifications to keep users informed about order statuses and other updates.
   - **Responsibilities**:
     - **Notification Delivery**: Send notifications through email, SMS, or push notifications.
     - **Notification Management**: Manage and track notification statuses and history.
   - **Technology**:
     - **Go**: Implements service logic and APIs.
     - **RabbitMQ**: Manages message queues for reliable delivery of notifications.

### 7. Auth Service
   - **Description**: Manages authentication and authorization, including the issuance and validation of JWT tokens for secure access to services.
   - **Responsibilities**:
     - **Authentication**: Verify user credentials and issue JWT tokens.
     - **Authorization**: Validate JWT tokens and enforce access control policies.
   - **Technology**:
     - **Go**: Implements authentication and authorization logic.
     - **Redis**: Caches authentication tokens and user sessions.

### 8. API Gateway
   - **Description**: Acts as a single entry point for all microservices, handling routing, load balancing, and aggregation of responses from multiple services.
   - **Responsibilities**:
     - **Routing**: Direct incoming requests to the appropriate microservices.
     - **Load Balancing**: Distribute traffic evenly across service instances.
   - **Technology**:
     - **Go**: Implements API gateway logic.
     - **Go-Kit** or **Kong**: Provides gateway functionalities such as routing and load balancing.

## Monitoring and Logging

1. **Monitoring**: 

    - **Prometheus**:
        - **Time-Series Database**: Prometheus is designed to collect and store metrics as time-series data, with each data point marked with a timestamp and a set of labels.
        - **Powerful Query Language (PromQL)**: PromQL allows for flexible and accurate querying of collected time-series data.

    - **Grafana**:
        - **Visualization**: Grafana is a powerful tool for visualizing metrics from Prometheus (and other data sources). It provides interactive and customizable dashboards.
        - **Alerts**: Grafana can create alerts based on metric data and send notifications to various channels (such as Slack, Email, etc.).

    **Why Prometheus and Grafana?**:
    - **Scalability**: They can efficiently handle large amounts of data.
    - **Flexibility**: Suitable for a variety of use cases, from simple monitoring to complex data visualization and alerting.
    - **Community and Support**: Both are widely adopted and have strong community support, with extensive documentation and numerous integrations.

2. **Logging**: 

    - **ELK Stack**:
        - **Elasticsearch**:
            - **Search and Analysis**: Elasticsearch is a distributed search engine that allows for advanced full-text search, as well as structured and unstructured data analysis.
            - **Scalability**: Designed to scale horizontally, Elasticsearch can handle large volumes of log data.
            - **Real-Time Data**: It supports real-time data ingestion and search, making it ideal for monitoring and logging purposes.
        
        - **Logstash**:
            - **Data Processing Pipeline**: Logstash is a server-side data processing pipeline that ingests data from multiple sources simultaneously, transforms it, and sends it to a "stash" like Elasticsearch.
            - **Flexible Configuration**: It supports a wide range of input, filter, and output plugins to transform and transport log data.
        
        - **Kibana**:
            - **Data Visualization**: Kibana provides visualization capabilities over the data stored in Elasticsearch. It can quickly create and share dynamic dashboards.
            - **Real-Time Insights**: It allows users to explore and visualize log data in real-time, aiding in quick diagnosis and insights.

    - **OpenTelemetry**:
        - **Unified Observability**: OpenTelemetry enables the collection and correlation of metrics, logs, and traces, providing a comprehensive view of your system's performance and behavior.
        - **Vendor-Neutral**: OpenTelemetry is vendor-agnostic, meaning it can integrate with various backends like Prometheus, Grafana, ELK Stack, and more.
        - **Standardization**: OpenTelemetry provides a standardized way to collect telemetry data across services and platforms.

    **Why ELK Stack and OpenTelemetry?**:
    - **Comprehensive Solution**: Provides a complete solution for collecting, processing, storing, and visualizing log data.
    - **Powerful Search and Analysis**: The powerful search capabilities of Elasticsearch combined with Kibana's visualization make it easy to gain insights from log data.
    - **Flexibility and Extensibility**: The ability to integrate with various data sources and the flexibility to transform data using Logstash makes the ELK Stack a versatile tool for logging.

## Deployment

1. **Containerization**: Docker is used for containerizing the services.

2. **CI/CD**: GitHub Actions is used for continuous integration and continuous deployment.

## Getting Started

### Prerequisites

- **Docker**: Ensure Docker is installed for containerization.
- **Kubernetes (Optional)**: For local development, you can use Minikube or Kind.
- **Database**: Set up a PostgreSQL or MongoDB instance as required by the services.
- **Terraform**: for infra as code

### Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/mini-ecommerce-microservice.git
   cd mini-ecommerce-microservice
