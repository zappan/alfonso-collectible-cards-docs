# Card Flipping App - Technical Architecture Overview

## Introduction

This document provides a high-level overview of the technical architecture for the Card Flipping App. It covers key elements of data ingestion, technical documentation, and future architectural considerations.

## Application Structure

The Card Flipping app consists of two major subsystems, the “back office” where the trading cards data is gathered, and the “front office” which greets customers with well-organized, contextualized data on trading cards

The back office takes care of integrating with the data sources, whether through APIs, or scraping the websites that contain data of interest. Collected data needs to be organized into a common data model required by the Card Flipping app to support its operational goals. All of this is part of the data collection and structuring process that takes place in the back office. Such tasks are commonly handled by data orchestration tools, which encapsulate and orchestrate these processes.

The front office consists of the application interface for customers, its supporting API, and the data store. This interface allows customers to interact with the gathered data and utilize the features and functionality provided by the product. Implementation of the front office will rely on common web technologies — a user interface in the browser, and the backend on a server.

The backend components of the system, the front office backend and the back office data orchestrator, require hosting on a server. The easiest way to start is to leverage public cloud services that come pre-configured for specific types of services (data orchestrators, backend API, database hosting, etc.).

In the case of the Card Flipping app, the system architecture can be outlined as follows:

**\[TODO: an architecture diagram here\]**

-----

## Application Hosting Platform and Infrastructure

In early-stage startups, there’s a balance between using lightweight tools and fully future-proofing the setup. For cloud hosting, it’s easy to think that one of the big three Infrastructure as a Service (IaaS) platforms (AWS, Azure, GCP) is the best choice for both current and future needs.

Choosing one comes with a cost. Those platforms provide building blocks to create your own cloud infrastructure, from networking and storage to compute resources. But building it right takes time and expertise. Sure, it can be built in a simpler form initially, and redone later, but then there isn’t much difference between IaaS and Platform as a Service (PaaS) providers. With PaaS providers, the entire infrastructure can be set up in just a few clicks, whereas IaaS requires someone on the team to configure and maintain even the most basic infrastructure.

It’s recommended to start with one of the PaaS providers. This can save time and resources early on, when the focus is on validating the concept and finding product-market fit. Even if particular PaaS services seem relatively expensive, the overall operating cost will be significantly lower than that of managing your own cloud infrastructure. That remains the case until the business reaches a stage where owning infrastructure is justified, whether due to security, compliance, or scaling needs.

-----

## Application Stack

For this kind of application, there’s a strong preference towards a TypeScript/JavaScript stack for developing the whole application — Node.js on the backend, and React-based technologies on the frontend.

### Backend Stack

While JavaScript is the _lingua franca_ for contemporary frontend web applications, Node.js for the backend is a great choice as it can support a lot of concurrent traffic with its unique event-loop and non-blocking I/O model. It’s not the only platform that provides such efficiency benefits, but it unifies the backend and the frontend stack under the same language umbrella, allowing the dev team to participate in both frontend and backend development efforts, which is important for a small-scale startup environment.

Among the leading frameworks, **NestJS** offers the most comprehensive, enterprise-grade structure, heavily influenced by Angular. It's ideal for large teams and complex applications requiring scalability and maintainability. NestJS is based on top of **Express.js**, which itself remains a widely-used, battle-tested option, though it’s considered somewhat dated in design compared to more modern frameworks like Fastify or NestJS. Finally, **Fastify** is a modern, performance-oriented alternative to Express, ideal for high-throughput services and teams that prefer a minimalistic yet efficient approach.

All three are solid frameworks, and there’s no “bad” choice among them. Ultimately, the best choice depends on the team's experience, even though frameworks more modern than Express.js have better support for adding a data caching layer if that becomes relevant. Thus, a recommendation goes towards either Fastify, if swiftness and minimalism are crucial, or NestJS, if solid structure is preferred from the start.

### Frontend Stack

Similar to the backend, any of the major contemporary frontend frameworks is suitable for this kind of application. We identified a preference for React-based frameworks during our research phase, and there are a few contenders in this space: React Router v7, Next.js and TanStack.

Out of those three, it's hard to make a mistake. It boils down to what the dev team is most experienced with and comfortable using. Developer expertise matters the most when it comes to moving fast and delivering, as all of them are more than suitable for this type of application.

-----

## Database

Generally speaking, this type of application requires a rather standard data store. However, some flexibility is highly desirable, as data will be coming from different sources and is expected to contain varying sets of attributes, some of which may be valuable but not consistently present across all sources. A flexible database helps manage such variability.

There are two general paths to consider — a relational database or a document-oriented database. The leading candidates are PostgreSQL for the relational approach, and MongoDB for the document-based model.

PostgreSQL, while being a relational database, also supports unstructured data through its built-in JSON data type. This allows it to offer flexibility while retaining the benefits of a strictly defined schema enforced at the database level. MongoDB, by contrast, is a highly flexible document database that can still mimic a relational structure using collections and documents as equivalents to tables and rows.

For the data ingestion part of the system, a flexible solution like MongoDB offers significant advantages. It allows raw data of varying structure to be stored with minimal effort and little to no changes on the database side. With PostgreSQL, a flexible schema can be designed, but it requires intentional planning. This introduces some technical overhead in managing migrations at the database level, in addition to the application layer.

Both databases have mature public cloud offerings, which are more than sufficient for an early-stage startup. Offloading database engine maintenance and backups to a trusted provider removes one significant burden from the business and technical team. Supabase is a strong option for PostgreSQL, while MongoDB Atlas is the official cloud offering for MongoDB. PaaS providers offering hosted PostgreSQL can also be considered.

If the project begins with a scrapable proof-of-concept for fetching and processing data from different sources, MongoDB’s flexibility makes it a great choice for faster iterations. It may even serve as a longer-term production option, especially if the development team is comfortable with it. On the other hand, if the aim is to establish a solid foundation with strict schema enforcement from the start, PostgreSQL may be the better choice — unless it turns out that the ingested data is inherently better suited to a document-based model.

The final decision will be made once there is more familiarity with the nature and structure of the ingested data.

-----

## Data Ingestion Strategy

Data ingestion can be implemented using approaches that vary in complexity. At the simplest end are manually orchestrated cron-job scripts. More advanced solutions include serverless workflows using AWS Lambda and Step Functions, which offer cloud resilience but limited built-in observability. At the higher end, workflow orchestration tools coordinate complex pipelines and provide native observability dashboards.

Common workflow orchestration tools include Apache Airflow, Dagster, Prefect, and Temporal. These are not particularly difficult to learn, but each follows a distinct paradigm, so team members will need to become familiar with the selected tool. Most of them are Python-based.

The aim is to keep the development environment simple by relying on a robust cloud-hosted solution, minimizing operational overhead. Dagster or Airflow are likely the best candidates unless the team has experience with another tool. The final decision will depend on which platform offers the most cost-effective hosting for production.

Beyond ingestion strategy, it's equally important to consider the nature and stability of the data sources themselves.

### API Integration vs. Web Scraping

API integration is preferred over web scraping, as it provides a structured interface and data format that is easily consumed by software. In contrast, web scraping extracts data from interfaces intended for human consumption, where the structure is optimized for presentation rather than automation.

APIs offer greater consistency and reliability compared to web scraping. Web scraping should be used only when no API is available for the required data.

### Operational Risks of Web Scraping

Web scraping poses long-term risks, as websites may change their presentation layer over time, whether through design updates or structural changes. These shifts can disrupt data extraction, so scraped sources must be closely monitored, and scrapers must be promptly adjusted to maintain uninterrupted workflows.

Web scraping must be implemented separately for each data source, as it depends on the specific structure of each website to extract information. These scrapers can be executed as containerized tasks via a data orchestrator, either as directly deployed orchestrator task scripts, or packaged into containers for isolation and encapsulation. The latter is preferred, as all the required dependencies get packaged into a container for a seamless run, simplifying task distribution and enabling each scraper to run as a self-sufficient unit of work.

### Use of AI in Web Scraping

A recently viable alternative is using AI models for web scraping. Modern AI systems can parse web content, identify patterns, and extract information in defined formats. Unlike traditional scrapers, this approach relies on high-level instructions describing the desired data and output format, rather than coding a dedicated scraper for each site.

However, this technique is still emerging, and accuracy is not yet guaranteed. Because of the possibility of AI hallucinations, the extracted data may contain inaccuracies. Furthermore, far fewer engineers have the expertise to build such solutions, and their services tend to be more expensive than those of developers skilled in conventional web scraping, which has matured significantly over the past decade.

-----

## Team Structure

#### **RECOMMENDED: 3-Person Team**

A sustainable and efficient approach involves a small, focused 3-person team:

- **2x Full-Stack Engineers (JavaScript/TypeScript)**: One stronger in UI/frontend, the other in API/backend and database modeling, but both capable of working independently and owning features end-to-end to minimize bottlenecks. The more experienced team member can support final optimizations in their area of expertise.
- **1x Data Engineer (Python)**: Responsible for data ingestion from APIs and web scraping, managed via a workflow orchestration platform such as Dagster or Airflow.

This team structure enables parallel development while maintaining the flexibility to iterate quickly and delivering production-ready features efficiently.

#### **COMPACT: 2-Person Team**

A more compact 2-person team is feasible, but demanding. It requires both individuals to be highly efficient, well-coordinated, and comfortable with overlapping responsibilities.

- **1x Full-Stack Engineer**: Primarily responsible for the web application. Equally strong in frontend/UI, backend API design, and database modeling. Highly proficient in JavaScript/TypeScript.
- **1x Backend/Data Engineer**: Responsible for data ingestion from source APIs and web scraping, managing orchestration pipelines, and ideally capable of implementing backend API endpoints for data ingestion. Proficiency in both Python and JavaScript/TypeScript is required.

This compact setup minimizes headcount in the early stages, but demands above-average engineers with broad expertise and the ability to take full ownership of their respective areas.

#### Additional Roles

In addition to the core roles above, some degree of project management and quality assurance (QA) is required. Both can be handled by the founders, provided they have the necessary skills to manage a software project and perform functional testing of features during development and after completion.

Engineers in a startup are also expected to partially assume these responsibilities, making sure they validate their own work, coordinate with the founders on priorities, help break down functional requirements into actionable items, and maintain the product development backlog.

Automated QA is highly beneficial if the budget allows for it. Writing automated tests using Playwright or a similar end-to-end testing tool increases confidence in each release and contributes to overall system stability. BDD-style testing further ensures that backend functionality consistently aligns with expected specifications. While it may be difficult for early-stage startups to dedicate resources to QA automation initially, it’s a valuable role to prioritize as the product and team grow.

-----

-----

## Technical Documentation

The technical documentation for the Card Flipping App architecture will include:

- High-level system diagrams illustrating the key components and data flows
- Detailed integration workflows showing how the different services and systems connect

These artifacts will provide a comprehensive view of the overall technical architecture.

## Data Ingestion

The data ingestion strategy for the Card Flipping App will support both batch and real-time data processing approaches. The architectural design includes the following components:

- Batch ingestion pipeline using Apache Spark to handle large volumes of historical data
- Real-time ingestion stream using Apache Kafka to capture and process events as they occur
- Hybrid model that combines both batch and real-time approaches to provide a comprehensive data processing solution

The document will compare the trade-offs and considerations for each ingestion model to help guide the implementation.

## Future Considerations

As the product evolves, additional technical documentation will be needed, including:

- Detailed data models and naming conventions
- API contract definitions for integrating with external systems
- Alignment of the technical architecture with the application UI and business requirements

The timeline for these future deliverables will depend on the required level of detail and ongoing alignment needs.

## Team Structure Recommendations

To successfully deliver the technical architecture for the Card Flipping App, the following team structure is recommended:

- Project Manager: To oversee the overall project timeline, resource allocation, and stakeholder coordination
- Technical Architect: To lead the design of the data ingestion strategy, integration workflows, and system diagrams
- Data Engineer: To implement the batch and real-time data pipelines using Apache Spark and Kafka
- Software Engineers: To build the application services and APIs that will integrate with the data platform
- Quality Assurance: To test the end-to-end functionality and performance of the technical architecture

The specific roles and number of team members can be adjusted based on the size and complexity of the project. However, this core team structure should provide the necessary expertise to deliver the technical documentation and future considerations outlined in this document.
