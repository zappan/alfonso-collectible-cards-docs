
## Preface

Proof-of-Concept / MVP approach to building the tech stack - Work in Progress


## Frontend Stack

Any of the major contemporary frontend frameworks is suitable for this kind of
application in 2025. We identified a preference for React-based frameworks
during our initial conversation, and there are a few contenders in this space:
React Router v7, Next.js and TanStack. Aside of those, Svelte and Vue are
independent frameworks NOT based on React.

Here's a breakdown:

#### 1) React Router v7 / Remix

React Router v7 (RRv7) introduces modern concepts typically found in full-stack
frameworks, such as route-based data loading and error boundaries, while
remaining lightweight and flexible. It provides primitives for routing and data
fetching that support SSR and BFF architectures, but developers are responsible
for implementing backend runtimes, form submission handling, and error boundary
logic beyond the provided abstractions.

In contrast, Remix is a full-stack React framework with an integrated runtime,
opinionated conventions, and built-in tooling for routing, data loading,
server-side form handling, error boundaries, caching, and performance
optimizations. It abstracts backend concerns and offers a seamless developer
experience with minimal configuration.

Both RRv7 and Remix are well-suited for teams that want to build React-based
applications with fine-grained control and flexibility while avoiding vendor
lock-in—Remix providing a more opinionated, end-to-end framework experience,
and React Router offering a modular, backend-agnostic approach. They are
maintained by the same core team, which joined Shopify following its
acquisition of Remix Software in 2022, and both benefit from ongoing
development and institutional support under Shopify’s umbrella.


#### 2) Next.js

Next.js is a widely adopted React framework, used by many companies around the
world. It supports a range of use cases for businesses of different sizes and
has grown significantly in complexity over time, thus leveraging its full
capabilities is a substantial learning investment. The framework is an
open-source product of Vercel, a cloud PaaS provider, where it benefits from
tight integration with Vercel’s hosting platform, and some features are more
seamless on their infrastructure.

A key advantage of Next.js is the large pool of developers experienced with it,
making hiring relatively accessible. However, many developers may still be
familiar only with older versions and paradigms, as Next.js introduced a major
shift with the App Router and React Server Components in the last two years,
drawing inspiration from broader trends in the React ecosystem and innovations
introduced mostly by Remix.


#### 3) TanStack

The most recent and independent of the three, TanStack carries no legacy
constraints, making it a popular choice among independent developers for its
innovative approaches and modern design. TanStack Router is a modern,
lightweight, and highly type-safe routing solution focused on modularity and
developer experience. It integrates closely with TanStack Query to provide
powerful data fetching and caching capabilities.

While it supports SSR patterns through manual integration with React Query’s
hydration APIs, TanStack Router itself does not include built-in
Backend-for-Frontend (BFF) capabilities and remains backend-agnostic and
unopinionated about backend runtimes or rendering strategies. That said, the
experimental TanStack Start project introduces `createServerFn()`, a utility
for defining server-side logic and exposing it to the client via type-safe
RPC-style calls. This brings optional BFF-like behavior to TanStack
applications, without imposing a specific backend structure or runtime,
preserving the framework’s modular, flexible nature.

TanStack Router’s small bundle size and incremental adoption path make it an
attractive choice for teams seeking a lightweight, high-performance routing
solution with fine-grained control over all aspects of an application, rather
than committing to an opinionated full-stack framework.

One point to consider is that TanStack is primarily driven by Tanner Linsley,
its original creator and main maintainer. While it benefits from active
development and community support, there is no clear evidence of stable funding
or institutional backing to ensure its sustained maintenance.


#### 4) Others

Beyond the top three, two additional frameworks are worth mentioning:

* **Svelte**: A standalone JavaScript framework with its own compiler-based
approach. Instead of using a virtual DOM like React, Svelte compiles code to
highly optimized vanilla JavaScript at build time, resulting in a smaller
runtime and often better performance.

* **Vue**: A progressive JavaScript framework inspired partly by Angular and
React, but built from the ground up. It uses a virtual DOM like React, but has
its own templating system, reactivity model, and ecosystem.


### Conclusions

In summary, frameworks like Next.js, Remix, React Router, and TanStack Router
are built directly on top of React, relying on its component model and
rendering lifecycle. Svelte and Vue are independent frameworks with their own
architectures not based on React.

_PERSONAL TAKE: I've had good experiences prototyping with Remix, using it as a
full-stack framework that leverages server-side action patterns for direct
access to the data store, omitting the need to build a separate API layer. I
haven’t yet had the opportunity to try TanStack, but its paradigm looks
promising and well worth exploring. I'm less of a fan of Next.js due to its
tight coupling with Vercel hosting platform, and major paradigm shifts._

SUMMARY: Out of the three React-based frameworks, it's hard to make a mistake.
It boils down to what the dev team is most experienced and comfortable with,
and in case of Next.js making sure they're on the latest version of the
framework. Developer expertise matters more than a personal preference here, as
all of them are more than suitable for the type of application being built.


----

## Backend Stack

As discussed in our initial call, there is a stong preference towards Node.js
based backend. For this kind of application, Node.js is a great choice as it
can support a lot of concurrent traffic with its unique event-loop and
non-blocking I/O model.

### Standalone API vs. BFF as a Backend

The standalone API backend component, whether it's REST or GraphQL, enables
full flexibility for the future, but requires more work, as it's an application
component with its own life-cycle, maintenance requirements, etc. An
alternative to a standalone API at the PoC/MVP stage could be leveraging
"Backend-for-Frontend" (BFF) for all the backend purposes, building an
integrated full-stack application, similar in simplicity to how web
applications were built in the early days.

The benefits of development time reduction and deployment simplicity with the
BFF-only approach are countered by the inability to expand to additional
frontends in the future (think mobile apps, API clients like agents and similar
machine-to-machine use cases) without migrating the architexture to include the
standalone API.

_DISCUSSION: Using the BFF as the only backend logic is a feasible option to
consider, if shorter development time to the initial PoC/MVP is a priority,
acknowleding that a significant revamp will need to be done once the concept is
proven, and the application needs to build to a more robust architecture. It's
good enough for the early stages in the lifecycle of the product, but as soon
as another frontend (let's say a mobile app) would come into play, it would
need an API to talk to, which BFF will not provide, this architecture breaks._

BFF pattern is available in all three suggested React frameworks, should a
choice be made to build the initial MVP with that approach. At a later stage, a
full-fledged standalone API would need to be built, and the BFF backend
re-wired towards that API. That is quite a significant refactoring at that
point in time which needs to be counted in for with the timeline/planning.


### Standalone API Backend Frameworks

When building an API using Node.js, there are several frameworks worth
considering:

#### 1) Express.js

Express is the most popular and long-standing Node.js framework, with over a
decade of active use. It provides robust routing, an extensive middleware
ecosystem, and a minimal core, making it well-suited for building RESTful APIs,
microservices, and scalable web applications. While it's not the most modern in
design, its stability and wide adoption make it a reliable choice.

#### 2) Fastify

Fastify is a modern, high-performance Node.js framework designed for speed and
developer productivity. It offers high throughput, a powerful plugin
architecture, and JSON schema-based validation. It’s especially well-suited for
building fast, low-latency APIs and microservices, and is increasingly popular
as a performance-focused alternative to Express.

#### 3) NestJS

NestJS is a full-featured, opinionated framework built on top of Express or
Fastify (uses Express or Fastify as the underlying HTTP server). Inspired by
Angular’s architecture, it embraces modular organization and dependency
injection. It comes with built-in support for GraphQL, WebSockets,
microservices, and more, making it particularly well-suited for
enterprise-grade APIs, and large and complex backend applications.

#### 4) Others

Beyond the top three, two additional frameworks are worth mentioning:

* **Hapi.js**: Once a popular choice, Hapi.js remains technically relevant,
with a clear structure and built-in support for caching, authentication,
authorization, and input validation. While it's now considered more niche or
legacy, it's still a solid option for API-centric backends.

* **Hono**: A relatively new but fast-growing framework, Hono is designed for
ultra-lightweight API servers and excels in edge and serverless environments.
It supports Deno, Bun, and Node runtimes, and favors modern web standard APIs,
making it a strong candidate for projects targeting modern deployment
platforms, including edge and serverless.


### Summary

Among the leading frameworks, **NestJS** offers the most comprehensive,
enterprise-grade structure, heavily influenced by Angular. It's ideal for large
teams and complex applications requiring scalability and maintainability.
**Express.js** remains a widely-used, battle-tested option, though it’s
considered somewhat dated in design compared to Fastify or NestJS. Finally,
**Fastify** is a modern, performance-oriented alternative to Express, ideal for
high-throughput services and teams that prefer a minimalistic yet efficient
approach.

Ultimately, the best choice depends on the team's experience - all three are
solid frameworks, there’s no “bad” choice among them.

_Note: When it comes to caching, frameworks more modern than Express.js have
better support for adding a data caching layer (see below for details)_

----

## Database

For the prototyping phase, a flexible database solution in the form of MongoDB
may be considered, up until the data model becomes clear and solid. MongoDB can
be utilized in a way that is very similar to a relational database, allowing
for an easy switch later on, while still retaining the schema flexibility of a
document database allowing for easier prototyping.

MongoDB comes as an open-source self-hosted option, but also as a commercial
cloud offering in the form of MongoDB Atlas. With the latter, the cost and
effort of database maintenance, backups, and overall availability is offloaded
to the MongoDB's cloud service. It allows for faster development iterations due
to increased flexibility.

Once the application's data model matures, a switch to a more robust and rigid
relational type of database may/will be considered. The strongest pretendent
for that role would be PostgreSQL. With PostgreSQL, there's also a self-hosting
option, as well as leverating the cloud providers for a fully managed
solutions, including AWS Aurora, but also Supabase.

Of course, PostgreSQL can be selected from the beginning. There is a bit of an
overhead with a strict schema, and the need to do database migrations as the
data model will be evolving, affecting the layout of the data on the storage
level. That may incur a slight performance penalty in the long run as the
single table data gets scattered at different physical locations, although with
solid state disks, that is probably way less of an issue than in the past with
spinning drives.

_PERSONAL TAKE: I've had good experiences running MongoDB in production for
about three years on a similar type of project, where we were ingesting
companies and stock market data, presenting those to customers. A colleague of
mine has been running MongoDB Atlas in production for a product for over 8
years without issues. On the other hand, I've heard about people having had bad
experiences with MongoDB at a larger scale, thus I'm being a bit careful here.
My preference for prototyping is, very often, exaclty MongoDB due to its
flexibility, but for the production system the choice may be different,
depending on the actual structure of the data and the access patterns._

As MongoDB, unlike many other NoSQL solutions, can be used in a way that very
much resembles the relational DB models, that makes it a great option for
prototyping, allowing for a lot of flexibility. On the other hand, PostgreSQL's
support for the non-structured data type (JSON) allows for some flexibility
alongside a strict schema.

SUMMARY: If the aim is flexibility and speed of prototyping, MongoDB is a solid
choice, at least until the data model is explored and settled. Depending on the
data model and overall performance, it may also serve as a longer-term option
for production. On the other hand, if the goal is to build a solid database
foundation from the start, with a strict schema enforced at the database
instead of the application level, and to accept the overhead of schema
management early in the PoC/MVP stage rather than face a potential migration
later, PostgreSQL is the preferred choice. This holds unless the data model
ultimately proves better suited to a document database.


_NOTE: The final choice will be made after discussing the other aspects of the
application and figuring out how the data looks like._


----

## Caching

When considering caching, if a large amount of customers is expected, it makes
sense to establish a caching layer in the backend architecture from the start.
Caching layer should be a transparent layer built into the API such that all
data access go through the caching layer before hitting to the database, and
configurable set of rules need to be provided for each data point on whether
that data is cached, and for how long till the data is considered to be stale.

#### Infrastructure

As for the caching infrastructure, there's an option for simple in-memory cache
and caching supported by the cache-store in the back. The former allows for a
simple approach to caching without the cost of the extra infrastructure. The
drawback is that data is cached on each node in a load-balanced environment
separately, and, in case of a node restart, all cached data will need to be
repopulated. That's acceptable in the early life of the product.

Caching supported by the cache-store involves either Redis or Memcached as the
most common caching storage options. The general consensus is that Redis is
better suited for complex data models (think API data responses), and Memcached
is better suited for high-throughput, string-based caching scenarios (think
website pages). Thus, Redis is probably a better suited option here.

Support for cache-store can be a part of the hosting platforms, whether IaaS or
PaaS solutions (see below). Many of those offer either Redis or Memcached or
both as a part of their offering. Alternatively, running either of those tools
in a containerized environment allows for easy cache storage setup in case a
cloud provider without a managed caching option is chosen.


#### API Codebase

In addition to the infrastructure, caching needs to be supported/implemented in
the codebase as well. Some of the backend frameworks do provide caching support
out-of-the-box, [like NestJS](https://docs.nestjs.com/techniques/caching)
for instance, with both, in-memory and cache-store, caching strategies
supported.

Other frameworks have extra plugins that can be imported and configured for
caching, like [catbox for Hapi.js](https://hapi.dev/tutorials/caching/), or
[fastify-caching for Fastify](https://github.com/fastify/fastify-caching),
while Express.js apparently favours caching on the front of the request, using
Varnish or Nginx content caching, which is a different approach to caching,
looking to serve the cached content from the cache server in front of the API,
avoiding hitting the API completely. That is similar to the in-memory caching
strategy explained above, with the same downsides. There are no clear strategies
for server-side caching behind the API, aside of manually implementing a cache
layer in Express.

With Node.js based frameworks, hitting the API is not huge of a cost, and using
API-level caching is a preference between the two, as it allows flexibility
of the cache-store supported caching strategy. Caching at the front of the API
may be considered if deemed necessary down the road, but only as an additional
caching layer, rather than the primary one.


#### Backend-for-Frontend caching

BFF pattern is more oriented towards supporting the frontend (client-side), so
there should be noted they support client-caching, as well as server-caching.
For our use-case, server-caching is what we're interested in, to reduce the
strain on the servers from many customers fetching the same data, where we
experience stress on our servers. Client-caching is way less important, if not
completely irrelevant, as we don't want to show cusotmers data that is minutes
or hours of age.

BFF frameworks are expected to have less out-of-the-box support for caching,
compared to a full-fledged API frameworks. Implementing server-side caching
in them is doable, but the architecture is more manual rather than supported
by the framework.


#### Frontend caching

Although the primary concern with caching is server-side caching to keep the
pressure on the servers low, if a client-side caching requirement comes up, the
frontend framework of choice needs to support it nicely.

With React Router v7, caching feature is out of scope, but with Remix as a
framework tightly based on RRv7, there is a `remix-client-cache` library,
advertised as _"a powerful and lightweight library made for react-router v7 framework mode to cache your server loader data on the client using clientLoaders. ([source](https://remix.run/resources/remix-client-cache))"_

Next.js has client caching at a route level as one of the [several caching
mechanisms](https://nextjs.org/docs/app/deep-dive/caching) available.

TanStack has caching built-in into the TanQuery part of the stack, via the
[`QueryCache`](https://tanstack.com/query/latest/docs/reference/QueryCache)
storage mechanism, which nicely sits at the API call (query) level, where
it decides whether to serve the cached data or query the API. This is one
of the most elegant implementations, and puts TanStack as a serious contender
for the frontend framework, if it turns out fronted caching will be important.


### Summary

In the early phases of any application development, the customer number is
relatively small compared to what modern servers are able to sustain without
experiencing performance degradation, so much that caching may be a completely
unnecessary component.

Having that in mind, and in case a BFF approach is chosen to act as the only
backend for the early stage, a recommendation is to omit the formal caching
layer across the board, and selectively add caching to common data endpoints
which may turn out to be "hot". Once the application evolves towards building a
standalone API backend, caching should be an integral part of that architecture.

Should the choice be to build a standalone API from the start, having caching
as a part of the API architecture is a recommended approach.

TL;DR: As long as BFF can support the whole application, caching may be added
selectively to "hot" data endpoints only, if necessary. Once the standalone API
becomes a necessity, caching should be an integral part of that architecture.

----

## Data Ingestion Pipeline

When it comes to data ingestion, generally speaking, there are several possible
approaches ranging from lower level techical solutions to more advanced and
complex ones. We can start thinking from the cron-jobs orchestrated independent
scripts as the most basic way of accomplishing such a task; over a serverless
solution leveraging AWS Lambda and Step Functions, where observability is still
limited, but reliability is increased due to the resilience of the cloud; all
the way to workflow orchestration tools offering pipelines coordination with the
observability dashboard built-in.

### Cron Jobs

An example of the cron-job approach is simply a set of scripts, written in any
language that can be run through a Linux shell, and the cron-job utility for
orchestration. The downside is, as mentioned, extremely low observability,
unless an integration with some kind of an observability tool is built manually.

### AWS Step Functions & Serverless

The Serverless approach with AWS Step Functions and AWS Lambda Serverless
platform has potential benefits in lower overall compute cost if data ingestion
is happening sporadically, as compute time is paid only for the time actually
spent running. Additional benefit is zero infrastructure to maintain for those
ingestion pipelines.

A downside of this setup is development experience, as this approach is heavily
reliant on the cloud. There is also the vendor lock-in aspect which kicks in
when leveraging proprietary cloud technology.

### Data & Workflow Orchestration Tools

Regarding the third approach, data and workflow orchestration tools have
emerged in the last 10 years exactly for processing data type of tasks.
There are several established solutions, including but not limited to
Apache Airflow, Dagster, Prefect, Temporal, etc. Such tools get deployed in a
contanerized environment and provide an observability dashboard and coordinate
executing data ingestion tasks registered with the platform.

From the current perspective, all of the orchestrators are capable of fetching,
transforming, and ingesting the required data, so focus should be on the ease
of use in development environment, and the reasonable cost of the cloud-hosted
platform for running it in production hassle-free.

#### Apache Airflow

Probably the most well-known orchestration tool, emerged from AirBNB, today an
Apache project, mainly fueled by the company named Astronomer, who are offering
a cloud-hosted Airflow platform as the business model. With the recent release
of Airflow 3, it mostly, but not fully, caught up with the rest of the space it
was lagging behind. Orchestration logic is written natively in Python, and
having announced native support for Golang, JavaScript/TypeScript, and Java,
but no target release date was given. Airflow is best-suited for complex and
static workflows with complex dependencies and task relationships.

#### Dagster

[Dagster](https://dagster.io/) emerged as a tool addressing Airflow's
limitations, and gained significant traction in the space. It's supported
by [Dagster Labs](https://dagster.io/blog/introducing-dagster-labs) (formerly
Elementl), an organization developing the product and offering a hassle-free
cloud-hosted Dagster platform (similar to Astronomer above). Orchestration
logic is written natively in Python only. Dagster has a declarative nature,
without explicitly defining the execution steps, thus simplifying pipeline
creation by abstracting away implementation details and promoting a more
structured workflow design.

#### Prefect

[Prefect](https://www.prefect.io/) is another of the tools emerged to address
Airflow's limitations. It's Python-native, the same as the previous ones, and
"it distinguishes itself with its emphasis on simplicity and efficient
scheduling mechanisms, making it an ideal choice for rapidly evolving workflows
that demand agility". It has a more imperative model with full granular control
over task execution and dependencies, requiring each step of the workflow to be
defined explicitly. Prefect enables developers to fine-tune their workflows
based on specific requirements.

#### Temporal

[Temporal](https://temporal.io/) is designed for high-throughput, long-running
workflows. Temporal excels in handling complex business processes and workflows
that involve external events or human interaction. Due to its focus on complex
workflows and distributed systems, Temporal might have a steeper learning curve
for beginners. It's also the only tool that supports multiple languages,
currenly offering six SDKs for writing the workflows: Java, Go, TypeScript,
.NET, Python, and PHP.


### Summary / Conclusion

_PERSONAL TAKE: I've had experience of building and maintaining a technically
low level solution with cron-job orchestrated scripts (back when workflow
orchestration tools have not existed yet), but for it to work reliably, I kept
them under my full control at all times. On the other hand, orchestration tools
have evolved since to a degree where it makes sense to consider such a tool
which provides orchestration capability with observability dashboard built-in._

With the release of Airflow 3, Airflow has caught up with most, though not all,
of the functionality offered by Dagster and Prefect. That said, all three are
solid products that can effectively orchestrate data acquisition from various
sources, with the added benefit of built-in observability.

Airflow has been around the longest and boasts the largest developer community
among orchestration tools, making it probably the safest bet for finding
engineers already familiar with it. Dagster offers a slightly better developer
experience and enhanced observability across running workflows, earning praises
from users who have switched from Airflow. Based on its marketing materials,
Prefect appears to focus on highly detailed, fine-grained control, which may
not be necessary for this use case. Temporal, on the other hand, acknowledges a
steeper learning curve due to its emphasis on complex workflows and distributed
systems.

CONCLUSION: The aim is at simplicity of development environment, and a solid
cloud-hosted platform to avoid management overhead of running such a platform.
Based on the above, focus should primarily be on Airflow and Dagster. Both offer
Docker-based local development environments, and the selection comes down to
their cloud hosting options, specifically which one provides a more affordable
solution for production.


----

## Cloud Hosting Platform

When it comes to cloud hosting platforms, there are two major classes of such
platforms - Infrastructure as a Service (IaaS) and Platform as a Service (PaaS)
solutions. In a nutshell, IaaS provides access to compute, storage, and
networking resources as building blocks for building your own infrastructure;
while PaaS provides an application deployment platform and execution
environments as an integrated solution.

In case of IaaS, the user is responsible for the operating system and any data,
applications, middleware, and runtimes, while a provider gives access to and
management of the network, servers, virtualization, and storage needed. PaaS,
on the other hand, enables developing, running, and managing applications
without having to build and maintain the infrastructure or platform - the
environment to build and deploy is provided by the vendor.

The benefits of taking the IaaS route is full flexibility in organizing the
whole environment, starting from networking and security, to the application
compute and storage services, with the added cost of setting up and maintaining
that infrastructure, similar to operating your own data center, except for this
one being virtual and components available instantly on-demand. The drawbacks
are mainly the cost associated with running your own cloud infrastructure,
requiring qualified system/cloud engineer on-borad who will design and ensure
the platform is running, and, generally speaking, higher initial cost compared
to a PaaS at an early stage of the application life where there aren't many
requirements regarding security and access protocols, compliance, etc.

The benefits of taking the PaaS route is a deployment-ready platform where the
vendor takes care of providing the compute, storage, and services in the form
of pre-fabricated blocks of common sizes, while making sure the whole platform
is operational without any involvement of the end-customer. Depending on the
provider, different levels of isolation from other tenants are possible, and
usually come with a price, but still don't require a system/cloud engineer on
board, as those platforms are being structured to be developer-friendly, so
even a slight increase in the platform cost is offset by not needing another
engineer on board. The drawbacks of PaaS platforms is less flexibility compared
to running your own infrastructure, and at some level the limits are hit when
it comes to isolation, security, and compliance, even though the most advanced
platforms have built their solutions to the level where they can offer very
high levels of isolation and even satisfy compliance reuqirements. That last
part comes with a cost, where it's advisable to reassess the IaaS vs Paas
approach.

**IaaS PLATFORMS EXAMPLES:** AWS, Azure, Google Cloud Platform (GCP), Oracle
Cloud Infrastructure (OCI)

**PaaS PLATFORMS EXAMPLES:** [Heroku](https://www.heroku.com/),
[Fly.io](https://fly.io/), [Railway](https://railway.com/),
[Render](https://render.com/), [Netlify](https://www.netlify.com/),
[Digital Ocean Droplets](https://www.digitalocean.com/products/droplets),
Engine Yard, Vercel, Google App Engine, Cloudflare Pages + Workers, etc.

_On a side-note, even MongoDB Atlas and Supabase are dedicated database
solutions PaaS platforms, as they offer database as a service to the customer,
while the platform is managed by the vendor._

With PaaS platforms, application deployment boils down to preparing a Docker
container and handing it over to the platform to run, or as an alternative,
allowing the platform to connect to the github repository and making the build
and deployment by themselves. With either of those approaches, testing out the
platforms, and moving from one to another is not much of a pain. The only
detail to pay attention to is database migration, if choosing the PaaS provider
to be the database provider as well, with the change of the provider, the DB
needs to be moved as well.

That can be mitigated by selecting a separate database provier, like the Atlas
Cloud for MongoDB, or Supabase for Postgres, where the database remains
separated. The drawback of such an approach is that there will be somewhat
higher latency between the application and the database, and that the data
traffic, although encrypted, will be travelling via the public internet. There
could be that some kind of private connections exist in certain scenarios with
certain PaaS providers through partnerships, but that needs to be further
explored.

SUMMARY: PaaS is a recommended way for the initial stages of a consumer grade
digital product, if there aren't any regulatory compliance requirements, mainly
due to its simplicity and overall cost of ownership being less than building
own cloud infrastructure. That remains the case up until the business reaches a
stage where owning an infrastructure is justified whether by security,
compliance, or scaling requirements, and the the overall cost is justified from
the business perspective.
