# System design case studies

How I design systems: case studies from my internships and projects.

I'm Montassar Tantouch, a final-year software engineering student (TEK-UP University, Tunis, graduating June 2027), looking for a 6-month internship starting January 2027. Each case study below takes a few minutes to read. They all follow the same outline:

1. Context and problem
2. Constraints
3. Architecture (with a diagram)
4. Key design decisions and trade-offs: what I chose, what I rejected, and what it cost
5. What I'd improve next
6. Stack

If you only have two minutes, read the "Key design decisions" sections. They show how I think better than the diagrams do.

The first three case studies come from my internship at Socomec Group (IT department, summer 2026). I wrote them from memory. They contain no proprietary code, configuration or data, and I describe internal systems generically. The last two are my own projects, and their source code is public.

## Index

| Case study | Problem | Key patterns | Stack |
|---|---|---|---|
| [Industrial IoT: edge-to-IT pipeline](industrial-iot-edge-to-it/) | Get traceability data from production-line PLCs into IT systems without losing records during network outages | Edge brokers with MQTT bridging, store-and-forward, QoS 1 with idempotent writes, Strategy-pattern message routing, per-line topic ACLs | MQTT (Mosquitto), Node-RED, C# .NET 8 Worker Service, EF Core, SQL Server, TLS, Grafana |
| [PickPrint: CQRS back office](cqrs-shop-floor-app/) | Manage product configuration for several factories whose databases have different schemas, with a full audit trail | CQRS with MediatR, database-per-tenant resolved at request time, polymorphic JSON contracts, audit history with JSON diffs and change reasons, validated batch imports | ASP.NET Core 8, Blazor, MediatR, AutoMapper, EF Core, ClosedXML, Active Directory |
| [Gestion Formation: monolith to N-tier](monolith-to-n-tier/) | Split a training-management web app into layers and keep employee data in sync with HR and ERP systems | Layered projects with their own DI modules, read-only integration contexts, a background sync worker, AD authentication with app-side authorization | .NET 8 MVC, EF Core, SQL Server, IHostedService, Bodet HR, Sage ERP, Active Directory |
| [Calleem: voice AI SaaS](calleem-voice-ai-saas/) | Give every small business its own AI phone receptionist that can really book appointments | Managed voice loop with tool calls into my backend, tenant resolution for webhooks, webhook auth and de-duplication, encrypted per-tenant secrets, per-tenant event channels | FastAPI, MongoDB, Vapi, Twilio, Next.js 16, WebSockets, Docker |
| [Treservi: booking PWA](treservi-booking-pwa/) | Let salon customers book on their own and alert staff instantly, even when the app is closed | Shared-database multi-tenancy, QR self-booking with abuse controls, moving from WebSockets to Web Push, Service Worker caching strategies | React 19 PWA, Node.js, Express, MongoDB Atlas, Web Push, Docker |

## Links

- GitHub: https://github.com/montaassarr
- Portfolio: https://montassartantouch.me
- CV: https://montassartantouch.me/Montassar_Tantouch_CV.pdf
