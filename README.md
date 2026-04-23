# Collectra

A full-stack collection and inventory management platform where users can catalog, track, and share any type of collection — from watches and coins to trading cards and vinyl records.

**Live:** [collectra.site](https://collectra.site)

> Source code is private. This repo serves as a public project showcase.

![Collectra Dashboard](static/images/collectra-home-page.png)

## What It Does

Collectra lets users create collections with fully customizable fields per category, upload photos, track maintenance schedules, and share collections via public snapshot links. It's designed as a general-purpose tool — the same platform handles a watch collection with brand/movement/water-resistance fields and a playing card collection with edition/condition/rarity fields.

## Key Features

- **Dynamic custom fields** — An Entity-Attribute-Value (EAV) system lets each category define its own schema. Users add fields like "Movement Type" or "Edition" without any code changes or migrations.
- **Photo management** — Upload multiple photos per item with automatic thumbnail generation. Stored on AWS S3 with signed URLs.
- **Collection sharing** — Generate public snapshot links to share a collection with anyone, no account required.
- **Dashboard & analytics** — Overview of recent items, collection value tracking (cost vs current value), items by category breakdown, and maintenance due dates.
- **Full-text search** — Global search across all collections, items, and custom field values.
- **Authentication** — JWT with token rotation, Google Sign-In integration, and email/password registration.
- **GDPR compliance** — Full data export and complete account deletion including S3 cleanup.

## Tech Stack

| Layer | Technologies |
|-------|-------------|
| **Backend** | Java, Spring Boot, Spring Data JPA, Hibernate, REST API |
| **Frontend** | Angular, TypeScript, RxJS, Angular Material |
| **Database** | PostgreSQL, Flyway Migrations |
| **Storage** | AWS S3 (photos & thumbnails) |
| **Auth** | JWT with rotation, Google OAuth 2.0 |
| **Infrastructure** | Docker Compose, Nginx, Hetzner VPS, Cloudflare CDN/WAF |
| **Security** | Rate limiting (Bucket4j), Cloudflare WAF rules, HTTPS |
| **Testing** | JUnit, Mockito |

## Architecture

```
Client (Angular SPA)
  │
  ├── Cloudflare CDN / WAF
  │
  └── Nginx (reverse proxy)
        │
        └── Spring Boot API (Docker)
              ├── PostgreSQL (Docker)
              ├── AWS S3 (photo storage)
              └── Flyway (schema migrations)
```

The application runs on a Hetzner VPS with Docker Compose orchestrating the API server, PostgreSQL database, and Nginx reverse proxy. Cloudflare sits in front for CDN caching, DDoS protection, and WAF rules. Automated backups cover both the database and S3 assets.

## Contact

- **Email:** nikolay.va.georgiev@gmail.com
- **LinkedIn:** [linkedin.com/in/nikolai-georgiev](https://www.linkedin.com/in/nikolai-georgiev-55b48a1a9)
- **GitHub:** [github.com/NikolayGeorgievv](https://github.com/NikolayGeorgievv)
