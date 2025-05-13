
- Recommend tools for data ingestion, storage, transformation, and analysis.
- Define data pipelines and caching strategies.
- Recommend back-end database systems and intermediary systems.
- Advise on the most suitable cloud platform for the solution.

- Provide architectural diagrams for developer execution.
- Map data flows and determine data sourcing, storage, and processing strategies.
- Deliver a flowchart detailing data sources and flows.

⇒ data sources — recommended sources for the data for sales data, imaging, historical sales data; need to be highly reliable (ebay, if there is a way to get that data)
⇒ modelling — obtaining that data from the APIs, best way to process and store it in the application (a diagram that would show that)
⇒ backend architecture for the app (node, and DB most important)
⇒ recommendation on caching
⇒ frontend recommendation — aiming at React



## Preface

Proof-of-Concept / MVP level approach to the tech stack


## Data Ingestion Pipeline

Dagster vs. Airflow vs. cronjobs & scripts discussion
(also Python vs. probably Node.js to match the rest of the stack)


## Database

For the prototyping phase, a flexible database solution in the form of MongoDB may be considered, up until the data model becomes clear and solid. MongoDB can be utilized in a way that is very similar to a relational database, allowing for an easy switch later on, while still retaining the schema flexibility of a document database allowing for easier prototyping.

MongoDB comes as an open-source self-hosted option, but also as a commercial cloud offering in the form of MongoDB Atlas. With the latter, the cost and effort of database maintenance, backups, and overall availability is offloaded to the MongoDB's cloud service. It allows for faster development iterations due to increased flexibility.

Once the application's data model matures, a switch to a more robust and rigid relational type of database may/will be considered. The strongest pretendent for that role would be PostgreSQL. With PostgreSQL, there's also a self-hosting option, as well as leverating the cloud providers for a fully managed solutions, including AWS Aurora, but also Supabase.

Of course, PostgreSQL can be selected from the beginning. There is a bit of an overhead with a strict schema, and the need to do database migrations as the data model will be evolving, affecting the layout of the data on the storage level. That may incur a slight performance penalty in the long run as the single table data gets scattered at different physical locations, although with solid state disks, that is probably way less of an issue than in the past with spinning drives.

PERSONAL TAKE: I've had good experiences running MongoDB in production for about three years on a similar type of project, where we were ingesting companies and stock market data, presenting those to customers. I've heard many people having had bad experiences with MongoDB at a larger scale, thus I'm being a bit careful here.

SUMMARY: As MongoDB, unlike many other NoSQL solutions, can be used in a way that very much resembles the relational DB models, that makes it a great option for prototyping for sure. On the other hand, PostgreSQL introduced the non-structured data type (JSON) in their database years ago, where it allows for some flexibility alongside a strict schema. That move cemented its spot as one of the leading database solutions out there for all kinds of applications. If the aim is to build a solid database foundation from the start, adding the schema management overhead early on in the PoC/MVP stage, rather than paying the cost of migration later, PostgreSQL is definitely a recommended choice in that case.


## Backend Stack

As discussed in our initial call, there is a stong preference towards Node.js based backend. For this kind of application, Node.js is a great choice as it can support a lot of concurrent traffic with its unique event-loop and non-blocking I/O model.

There are two possible approaches to building the backend for this solution - (1) a standard API, (2) leveraging "Backend for Frontend" (BFF) Pattern as a backend instead of a separate API.

The former is how most of the applications are built nowaday, and is ready for building different frontends (mobile, web, etc.), as well as opening up to third parties to communicate with the system using the API.

The first approach is building a standard, full-fledged API (whether it's a REST or a GraphQL API), and having a frontend that utilizes that API.


With the latter, the frontend and the backend would be bundled together - similar how web applications were built in the early days where everything was server-side rendered, but with a modern touch of client-side and server-side separation possible with the advancements in the both frameworks and browser technology.

The benefits of the BFF approach are faster development time for the PoC/MVP, as the BFF would be talking to the database, and deliver data fully tailored for the screens of the web application, voiding the need for a general purpose API implementation, and then web application integration with that API. Having things bundled together will make development somewhat simpler, and therefore quicker. The drawbacks are that, in the long run, this solution might not be enough. In case a mobile app will need to be built, it can't talk to the BFF, it would require a separate, standalone API, which we would have been skipped if using the BFF approach.


The alternative, more MVP/proof-of-concept approach that will cut some corners, but yield faster results, is to build the backend using the "Backend for Frontend" (BFF) pattern which is available in the two leading React frameworks today, Next.js and React Router v7.


For the MVP phase, a simple backend can be built using React Router v7 with server-side rendering. That is, technically, a "Backend for Frontend" (BFF) pattern. At a later stage, a full-fledged API can be built, where this BFF backend would be re-wired towards that API, rather than directly accessing the database.


_TODO: REST vs. GraphQL discussion -- GraphQL when use patterns are unknown, REST when they are known_

_Note: Alternative Node.js runtimes, like Deno or Bun, may be considered in case performance becomes an issue at later stages. TODO: which of the offered frameworks have the runtime support on either or both of these?_



## Frontend Stack

A preferred frontend tech stack for this kind of application in 2025 would be any of the major contemporary frontend Frameworks.

React-based, RRv7 vs Next vs TanStack

Two of them rely on the React technology, while Vue.js and Svelte are separate

Alternatives to consider: Vue.js, Svelte


## Caching

none-at-start; redis/memcached-at-scale - NodeJS can handle a lot
⇒ still, maybe caching from the start, if we consider many read-only users accessing in a short period of time, maybe being ready is beneficial and to be built-in into the backend API to go through the API layer, even if it's disabled - GOAL: architecture in place

## Cloud Hosting Platform

TODO: IaaS vs PaaS discussion

When it comes to cloud hosting platforms, there are two major classes of such platforms - Infrastructure as a Service (IaaS) and Platform as a Service (PaaS) solutions. In a nutshell, IaaS provides access to compute, storage, and networking resources as building blocks for building your own infrastructure; while PaaS provides an application deployment platform and execution environments as an integrated solution.

In case of IaaS, the user is responsible for the operating system and any data, applications, middleware, and runtimes, while a provider gives access to and management of the network, servers, virtualization, and storage needed. PaaS allows developing, running, and managing the applications without having to build and maintain the infrastructure or platform - the environment to build and deploy is provided for you.

The benefits of taking the IaaS route is full flexibility in organizing the whole environment, starting from networking and security, to the application compute and storage services, with the added cost of setting up and maintaining that infrastructure, similar to operating your own data center, except for this one being virtual and components available instantly on-demand. The drawbacks are mainly the cost associated with running your own cloud infrastructure, requiring qualified system/cloud engineer on-borad who will design and ensure the platform is running, and, generally speaking, higher initial cost compared to a PaaS at an early stage of the application life where there aren't many requirements regarding security and access protocols, compliance, etc.

The benefits of taking the PaaS route is a deployment-ready platform where the vendor takes care of providing the compute, storage, and services in the form of pre-fabricated blocks of common sizes, while making sure the whole platform is operational without any involvement of the end-customer. Depending on the provider, different levels of isolation from other tenants are possible, and usually come with a price, but still don't require a system/cloud engineer on board, as those platforms are being structured to be developer-friendly, so even a slight increase in the platform cost is offset by not needing another engineer on board. The drawbacks of PaaS platforms is less flexibility compared to running your own infrastructure, and at some level the limits are hit when it comes to isolation, security, and compliance, even though the most advanced platforms have built their solutions to the level where they can offer very high levels of isolation and even satisfy compliance reuqirements. That last part comes with a cost, where it's advisable to reassess the IaaS vs Paas approach.

EXAMPLES OF IaaS PLATFORMS: AWS, Azure, Google Cloud Platform (GCP), Oracle Cloud Infrastructure (OCI)

EXAMPLES OF PaaS PLATFORMS: [Heroku](https://www.heroku.com/), [Fly.io](https://fly.io/), [Railway](https://railway.com/), [Render](https://render.com/), [Netlify](https://www.netlify.com/), [Digital Ocean Droplets](https://www.digitalocean.com/products/droplets), Engine Yard, Vercel, Google App Engine, Cloudflare Pages + Workers, etc. On a side-note, even MongoDB Atlas and Supabase are dedicated database solutions PaaS platforms, as they offer database as a service to the customer, while the platform is managed by the vendor.

With PaaS platforms, application deployment boils down to preparing a Docker container and handing it over to the platform to run, or as an alternative, allowing the platform to connect to the github repository and making the build and deployment by themselves. With either of those approaches, testing out the platforms, and moving from one to another is not much of a pain. The only detail to pay attention to is database migration, if choosing the PaaS provider to be the database provider as well, with the change of the provider, the DB needs to be moved as well.

That can be mitigated by selecting a separate database provier, like the Atlas Cloud for MongoDB, or Supabase for Postgres, where the database remains separated. The drawback of such an approach is that there will be a higher latency between the application and the database, and that the data traffic, although encrypted, will be travelling via the public internet. There could be that some kind of private connections exist in certain scenarios with certain PaaS providers through partnerships, but that needs to be further explored.

SUMMARY: For the MVP stage of a consumer grade application, and into the first several years of building a business around it, PaaS is a simpler, cheaper, and an overall better-suited solution. That remains the case up until the business reaches a stage where a clear need for the infrastructure scale, or isolation and privacy is required, and the cost of such a setup justified and covered by the growing business.
