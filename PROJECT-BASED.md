# PHP · OOP · Patterns
## Project-Based Learning Path

Five projects. Each one bigger than the last. Each one introducing concepts only when a real problem demands them — not before.

| | |
|---|---|
| **Projects** | 5 |
| **Timeline** | ~24 weeks |
| **PHP Version** | 8.2+ |
| **Approach** | Build first, abstract later |

---

## Stage 1 · Weeks 1–3 · Pure PHP

---

### Project 01 — Personal Expense Tracker

`PHP`

A CLI tool that logs expenses to a CSV file, reads them back, filters by category or date, and prints a summary. No database. No classes. Just PHP doing real work.

#### PHP Fundamentals

- Variables, types, operators
- Arrays — indexed and associative
- Functions with type declarations
- `declare(strict_types=1)`
- File I/O — `fgetcsv`, `fputcsv`
- CLI args via `$argv`
- Error handling — try/catch
- `array_filter`, `array_map`, `usort`

#### What You'll Feel

- Functions getting too long
- Related data scattered across variables
- No clear place to add a new feature
- Duplication across filter functions

#### Features to Build

- Add expense: category, amount, date, note
- List all expenses
- Filter by category or month
- Monthly total summary
- Delete an expense by ID

> **Deliverable:** A working CLI app. Messy is fine — that's the point. When it's done, write a short note about what's painful about the code. That list is your OOP motivation.

**Stretch goals:** Export to JSON · Multi-currency support · Budget limits per category

---

## Stage 2 · Weeks 4–8 · OOP Introduction

---

### Project 02 — Blog Engine (No Framework)

`PHP` `OOP`

A web-based blog: posts, categories, comments. Built with raw PHP and MySQL via PDO. No framework. You write the routing, the templates, the data layer — all of it. Classes introduced because the procedural version becomes unmanageable.

#### PHP Concepts

- PDO + prepared statements
- Superglobals — `$_GET`, `$_POST`
- Sessions — login, auth state
- Input validation + `htmlspecialchars`
- Simple front controller routing
- PSR-4 autoloading via Composer
- Namespaces

#### OOP Introduced

- Classes, properties, methods
- Constructor promotion
- Typed properties
- `public` / `protected` / `private`
- `__toString`, `__get`
- Model classes — Post, Comment, User
- Separation of concerns — Model vs. View

#### Features to Build

- Post CRUD — create, read, update, delete
- Categories and tags
- Comment system
- Admin login with sessions
- Slug-based URLs
- Pagination
- Simple search

> **Deliverable:** A running blog you can deploy. The Database class will start growing into a god object. Your model classes will have too many responsibilities. Notice it. Don't fix it yet — that's Project 3's job.

**Stretch goals:** RSS feed · Markdown rendering · Image upload · Draft/published status

---

## Stage 3 · Weeks 9–13 · OOP in Depth + First Patterns

---

### Project 03 — Task Management API

`PHP` `OOP` `Patterns`

A JSON REST API for managing tasks, projects, and users. No UI. This project forces real architecture: clean separation of layers, interface-driven design, and the first design patterns applied where they actually solve problems.

#### PHP Concepts

- HTTP headers — `Content-Type`, status codes
- JSON encode/decode with error handling
- Environment variables — `$_ENV`, `.env`
- Enums — task status, priority levels
- Readonly classes for DTOs
- Named arguments
- Attributes for route metadata

#### OOP in Depth

- Interfaces — `RepositoryInterface`
- Abstract classes — base Controller
- Traits — `HasTimestamps`, `Validatable`
- Late static binding
- Dependency injection — manual
- SOLID — applied to each layer
- Value objects — `Email`, `TaskId`

#### Design Patterns

- **Repository** — data access behind an interface
- **Factory Method** — ResponseFactory, TaskFactory
- **Strategy** — sorting and filtering tasks
- **Decorator** — logging, caching wrappers
- **Facade** — TaskService over complex subsystem

> **Deliverable:** A working REST API testable with Postman or cURL. You'll wire up the Repository pattern first and feel exactly why it exists the moment you swap MySQL for an in-memory store for tests.

**Stretch goals:** JWT authentication · Rate limiting · API versioning · PHPUnit test suite

---

## Stage 4 · Weeks 14–18 · Advanced Patterns

---

### Project 04 — E-Commerce Order System

`PHP` `OOP` `Patterns`

A backend order processing system: products, carts, orders, payments, notifications. The domain complexity is high enough that patterns stop being optional. You'll feel each one's absence before you reach for it.

#### PHP Concepts

- Fibers — async payment processing
- Generators — batch order export
- SPL — `SplQueue` for order queue
- PDO transactions — atomicity
- PHPStan at max level
- Composer scripts
- PSR-7 HTTP messages

#### OOP in Depth

- Rich domain model — Order, Cart, Product
- Aggregate roots
- Domain events
- Invariant enforcement in constructors
- Immutable value objects
- Type-safe collections

#### Design Patterns

- **Observer** — order events → notifications
- **Strategy** — payment: Stripe, PayPal, COD
- **Command** — PlaceOrderCommand + undo
- **State** — order lifecycle (pending → shipped)
- **Chain of Responsibility** — order validation
- **Builder** — fluent OrderBuilder
- **Proxy** — lazy-loading product details
- **Composite** — discount rule trees

> **Deliverable:** A complete order processing backend. The Observer pattern will click the moment you need to send an email, update inventory, and log an audit trail when an order is placed — and you don't want those three things to know about each other.

**Stretch goals:** Inventory management · Coupon/discount engine · Order export to PDF · Webhook system · Full PHPUnit coverage

---

## Stage 5 · Weeks 19–24 · Architecture

---

### Project 05 — Mini PHP Framework

`PHP` `OOP` `Patterns`

Build the framework, not another app. A router, a DI container, a middleware pipeline, an ORM, a template engine, a CLI tool. Every component you've used blind until now — you'll understand it by building it. Then use your framework to rebuild Project 2.

#### PHP Concepts

- Reflection API — autowiring
- Anonymous classes
- `#[Attribute]` — route annotations
- Closures as route handlers
- PSR-11 Container interface
- PSR-14 Event dispatcher
- PSR-15 Middleware

#### OOP in Depth

- Fluent interfaces
- Recursive type structures
- SPL interfaces — `ArrayAccess`, `Iterator`
- Magic method `__invoke` for middleware
- Covariant return types
- Generic-style patterns with templates

#### Design Patterns

- **Singleton** — App container (then replace it)
- **Abstract Factory** — driver system
- **Decorator + Chain** — middleware pipeline
- **Template Method** — base Controller, Command
- **Iterator** — Collection class
- **Mediator** — Event dispatcher
- **Interpreter** — query builder DSL
- **Flyweight** — compiled template cache

> **Deliverable:** A working micro-framework — capable of routing requests, resolving dependencies, running middleware, and talking to a database. Then port your blog from Project 2 onto it. That port is the final exam.

**Stretch goals:** Console commands (like Artisan) · Template engine with inheritance · Simple ORM with relationships · Publish as open-source on GitHub

---

Every project builds on the last. The blog you wrote in week 6 runs on the framework you built in week 22. That continuity is the point — you'll see exactly what you didn't know when you wrote it.

**Stack:** PHP 8.2+ · MySQL · Composer · PHPUnit · PHPStan