# FleetBook – Serverless Vehicle Booking System

## Overview

FleetBook is a serverless vehicle booking application built with Microsoft Azure services. It demonstrates an event-driven architecture using Azure Service Bus, Logic Apps, and Azure Functions to process vehicle booking requests asynchronously.

Customers submit booking requests through a web application. The requests are placed into an Azure Service Bus Queue, processed by an Azure Logic App, evaluated by an Azure Function, and then routed based on the booking result. Confirmation or rejection emails are sent automatically, and the booking result is published to a Service Bus Topic.

---

## Demo Video Link
https://youtu.be/MoQng3bBdhg

---

## Architecture

```text
FleetBook Web App
        │
        ▼
Service Bus Queue (booking-queue)
        │
        ▼
Azure Logic App
        │
        ▼
Azure Function (check-booking)
        │
        ▼
Condition
   ┌─────────────┐
   │             │
Confirmed     Rejected
   │             │
Send Email   Send Email
   │             │
   └──────┬──────┘
          ▼
Service Bus Topic (booking-results)
          │
   ┌──────┴──────┐
confirmed-sub  rejected-sub
```

---

## Azure Services Used

- Azure Service Bus
  - Queue (`booking-queue`)
  - Topic (`booking-results`)
  - Subscriptions (`confirmed-sub`, `rejected-sub`)
- Azure Logic Apps (Consumption)
- Azure Functions (Python)
- Outlook Connector
- Azure Storage Account

---

## Workflow

1. A customer submits a vehicle booking request using the FleetBook web application.
2. The booking request is sent to the **booking-queue**.
3. Azure Logic Apps automatically receives the queue message.
4. The Logic App decodes and parses the booking request.
5. The Logic App calls the **check-booking** Azure Function.
6. The Azure Function checks vehicle availability and calculates the estimated price.
7. The Logic App evaluates the returned booking status.
8. A confirmation or rejection email is sent to the customer.
9. The booking result is published to the **booking-results** topic.
10. Topic subscriptions receive messages based on their labels (`confirmed` or `rejected`).

---

## Project Structure

```text
FleetBook/
│
├── client.html
├── function_app.py
├── test-function.http
├── requirements.txt
├── local.settings.example.json
└── README.md
```

---

## Technologies

- Python 3.11
- Azure Functions
- Azure Logic Apps
- Azure Service Bus
- HTML
- JavaScript

---

## Screenshots

Add screenshots of the following:

- FleetBook Web Application
- Azure Function
- Azure Logic App Workflow
- Successful Booking
- Confirmation Email
- Azure Service Bus Queue and Topic

---

## Learning Outcomes

This lab demonstrates:

- Serverless application development
- Event-driven architecture
- Azure Service Bus Queue and Topic
- Azure Logic Apps workflow orchestration
- Azure Functions integration
- Conditional branching
- Email notifications
- Publish/Subscribe messaging pattern

---

## Author

**Jingjing Duan**

CST8917 – Serverless Applications

Algonquin College