System-Design Perspective:
- Statement: Kafka is faster and beats Rabbit MQ when multiple customers need independent log traversal. Explain exactly why and how??
- Explanation:
### Kafka vs. RabbitMQ for Independent Log Traversal by Multiple Consumers

#### Event Hubs and Service Bus Performance
- **Event Hubs:** Supports over 1 million messages per second.
- **Service Bus:** Supports up to 16,000 messages per second.
- Both use the same log storage infrastructure but differ significantly in performance.

#### Key Differences Between Kafka (Event Hubs) and RabbitMQ (Service Bus)

1. **Cursor Model**
    - **Queues (RabbitMQ, Service Bus):**
      - Manage a shared cursor for all consumers.
      - Ensure each message is delivered to one consumer at a time.
      - Track locks on messages to manage "out for delivery" status.
      - Remove messages once acknowledged or unlock them for redelivery.
    - **Ingestors (Kafka, Event Hubs):**
      - Do not manage a shared cursor.
      - Clients manage their own cursors by providing offsets.
      - No lock management.

2. **Compute Work**
    - **Message Brokers (RabbitMQ, Service Bus):**
      - Offer features like filtering, deduplication, scheduling, and expiration.
      - Require indexing and additional compute work for these features.
    - **Ingestors (Kafka, Event Hubs):**
      - Focus on providing chunks of messages based on offsets.
      - Minimal compute work beyond basic log management.

#### Pub/Sub Model

- **Message Brokers (RabbitMQ, Service Bus):**
  - Use topics/exchanges with subscriptions to support multiple consumers.
  - Each subscription acts like a queue, managing cursors for consumers.
  - Can scale out to groups of individual consumers sharing a cursor.

#### Performance Bottlenecks

1. **Cursor Management:**
   - Creates a bottleneck around the log's head for cursor and lock management.
   - Limits throughput in message brokers.

2. **Extra Compute Work:**
   - Features like filtering, deduplication, and scheduling add layers of work.
   - Further limits throughput compared to ingestors.

#### Implications

- **Message Brokers:** Best suited for dispatching discrete work items.
- **Ingestors:** Better for real-time event processing with multiple consumers needing to traverse the log independently.

### In a Nutshell

- The significant performance difference is due to cursor management and compute work, not just zero copy and sequential I/O.
- Enhancing a message broker's speed would require shedding features or increasing costs.
