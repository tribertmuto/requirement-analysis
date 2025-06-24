# Requirement Analysis in Software Development

This repository is dedicated to exploring the process of requirement analysis in software development. It provides insights into gathering, documenting, and managing software requirements to ensure the successful delivery of software projects. Whether you're a student, developer, or project manager, this repository aims to support your understanding of best practices in requirement engineering.
# What is Requirement Analysis?

Requirement Analysis is a critical phase in the Software Development Lifecycle (SDLC) where the needs and expectations of stakeholders are identified, documented, and analyzed to define what a software system must achieve. This process ensures that all parties involved developers, clients, users, and business analysts have a shared understanding of the softwares objectives and constraints before any actual development begins.

# Importance of Requirement Analysis in SDLC

1.Clarity and Alignment: It bridges the gap between stakeholders and developers, ensuring everyone is aligned on the project scope and goals.
2.Reduces Rework: Well-defined requirements help prevent costly changes and rework during later stages of development.
3.Improves Quality: Clear and validated requirements contribute to building software that meets user expectations and functions correctly.
4.Facilitates Planning: Accurate requirements provide a solid foundation for estimating time, cost, and resources.
5.Risk Mitigation: Identifying potential issues early allows teams to address risks proactively rather than reactively.
6.Basis for Testing: Requirements form the basis for creating test cases, which ensures the system is verified against original expectations.

# Key Activities in Requirement Analysis

- Elicitation: Gathering requirements from stakeholders using techniques like interviews, surveys, and workshops.
- Documentation: Creating clear and comprehensive requirement specifications.
- Validation: Ensuring that documented requirements accurately represent stakeholder needs.
- Management: Tracking and updating requirements as the project evolves.

Effective requirement analysis leads to better project outcomes, greater stakeholder satisfaction, and more efficient development processes.
# Why is Requirement Analysis Important?
Requirement Analysis plays a foundational role in the success of any software development project. It ensures that the final product aligns with the expectations and needs of stakeholders. Here are three key reasons why it is critical in the Software Development Lifecycle (SDLC):

# 1. Prevents Miscommunication and Misunderstanding
Requirement analysis facilitates clear communication between stakeholders and the development team. By thoroughly documenting what the software should do, it eliminates ambiguity and ensures that everyone involved has a shared understanding of the project goals and deliverables.

# 2. Reduces Cost and Time Overruns
Identifying and addressing potential issues or changes early in the project helps avoid costly rework later in development. Well-defined requirements allow for better project planning, more accurate time and budget estimates, and efficient resource allocation.

# 3. Enhances Product Quality and User Satisfaction
Accurate and validated requirements ensure that the developed software meets the actual needs of users. This leads to a higher-quality product that performs as expected, ultimately improving user satisfaction and reducing the need for post-deployment fixes.

Understanding the importance of requirement analysis is essential for building reliable, efficient, and user-focused software systems.
# Key Activities in Requirement Analysis

Requirement Analysis involves several essential activities that ensure software requirements are accurately captured and well-understood. Below are the five key activities, each playing a critical role in the process:

- Requirement Gathering  
  This involves collecting high-level requirements from stakeholders, clients, and end users. The goal is to understand what problems the software needs to solve and what objectives it must fulfill.

- Requirement Elicitation  
  Elicitation is a more structured and detailed process of extracting information through techniques such as interviews, questionnaires, observation, brainstorming sessions, and workshops. It focuses on uncovering hidden, implied, or unclear requirements.

- Requirement Documentation  
  This activity involves formally recording the gathered and elicited requirements in a clear, consistent, and understandable format. Common documents include Software Requirement Specifications (SRS), use cases, and user stories.

- Requirement Analysis and Modeling  
  Once documented, the requirements are analyzed to identify dependencies, inconsistencies, ambiguities, and conflicts. Modeling techniques like data flow diagrams (DFDs), entity-relationship diagrams (ERDs), and UML models may be used to visualize and structure the requirements.

- Requirement Validation  
  This step ensures that the documented requirements accurately reflect stakeholder needs and are feasible, testable, and complete. Validation is typically done through reviews, walkthroughs, and prototype evaluations with stakeholders.

Each of these activities contributes to building a strong foundation for successful software design, development, and delivery. 
#  Hotel Booking System Architecture

This document outlines the system design architecture for a hotel booking application similar to Airbnb, Booking.com, or OYO. The architecture is based on a microservices model to ensure scalability, availability, and maintainability.



#  Types of Requirements

In designing a robust hotel booking system, it's critical to distinguish between Functional and Non-functional Requirements. These requirements help define what the system should do and how well it should perform.


# Functional Requirements

These describe specific features and behaviors the system must support.

Hotel Management Service:
- Allow hotel managers to create, update, or delete hotel listings.
- Sync hotel details across master-slave DB architecture.
- Push updates to CDN and messaging queue (Kafka, RabbitMQ) for downstream services.

Customer Service (Search + Booking):
- Enable users to search for hotels by location, price, availability, etc.
- Let users view hotel details, reviews, and photos (fetched from CDN).
- Process hotel bookings and interact with third-party payment gateways.
- Update booking status in Redis and Booking DB.
- Sync booking data with Cassandra for archival.

View Booking Service:
- Provide users and hotel managers with historical and recent booking data.
- Fetch recent bookings via Redis and older records via Cassandra.

Notification System:
- Notify users about booking confirmations, cancellations, and promotional offers.
- Notify hotel managers upon new bookings.

Streaming & Analytics:
- Stream event data to Hadoop for business intelligence and user behavior analysis.

---

# Non-functional Requirements

These define the quality attributes of the system  how well it performs, rather than what it does.

Scalability:
- Use of microservices and load balancers ensures the system can handle high user traffic.
- ElasticSearch enables high-performance search under heavy load.

Availability & Reliability:
- Use of master-slave DBs ensures read/write separation, increasing fault tolerance.
- Redis caching provides high availability for frequently accessed data.
- Messaging queue (Kafka) helps decouple services, preventing system-wide failure.

Performance:
- CDN delivers fast access to static content (images, descriptions).
- Redis and Elasticsearch optimize query response times.
- Cassandra efficiently handles archival data at scale.

Data Consistency:
- Database synchronization from master to slave ensures consistency between reads and writes.
- Kafka ensures that updates flow correctly across services asynchronously.

Security:
- Secure APIs with authentication for both hotel managers and customers.
- Payment processing through secure third-party services.

Maintainability:
- Microservices architecture allows independent deployment and updates.
- Logging and monitoring via Kafka and Hadoop enable better system diagnostics.



# Notes

This architecture provides a scalable and resilient backbone for a large-scale booking system and can be extended further for advanced use cases like personalized recommendations, machine learning integration, or dynamic pricing models.

# Use Case Diagrams

Use Case Diagrams are part of the Unified Modeling Language (UML) and are used to visually represent the interactions between users (actors) and a system. They help clarify what a system is supposed to do and who interacts with it.

# Benefits of Use Case Diagrams:
- Simplify communication between stakeholders, developers, and designers.
- Clearly define functional boundaries of a system.
- Help in identifying system functionalities and external interactions.
- Serve as a foundation for writing user stories and testing scenarios.

# Actors:
- Customer: Searches, books, and views bookings.
- Hotel Manager: Manages hotel listings, views bookings.
- Payment Gateway: Processes payment transactions.
- System Admin (optional): Manages users and oversees system health.

# Use Cases:
- Search Hotel
- View Hotel Details
- Make Booking
- View Bookings
- Cancel Booking
- Update Hotel Info (Manager)
- Process Payment (External System)
- Send Notification
## Use Case Diagram

![ALX Booking Use Case Diagram](C:\Users\tribert\Documents\GitHub\requirement-analysis\alx-booking-uc.png)








