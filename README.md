# PHP · OOP · Design Patterns
## A Checklist Roadmap

---

## Stage 1 — PHP Fundamentals

> PHP runs on the server, outputs to the browser, and has 30 years of legacy baked into it. Learn what the language actually is before worrying about what it should be.

### Environment & Tooling

- [ ] Install PHP locally (8.2+ — don't start on anything older)
- [ ] Understand the request/response cycle — what PHP does per request
- [ ] Run PHP from the CLI (`php file.php`, `php -S localhost:8000`)
- [ ] Install Composer — PHP's dependency manager
- [ ] Understand `composer.json`, `composer.lock`, and `vendor/`
- [ ] Configure a basic `php.ini` — error reporting, display errors, timezone

### Core Syntax

- [ ] Variables and type juggling — PHP's loose typing and why it bites people
- [ ] Data types — int, float, string, bool, null, array, object
- [ ] String syntax — single quotes vs. double quotes (the difference matters)
- [ ] Heredoc and nowdoc
- [ ] Type declarations — `declare(strict_types=1)` and why to always use it
- [ ] Casting — `(int)`, `(string)`, `(bool)`, `(array)`
- [ ] Null coalescing — `??` and `??=`
- [ ] Spaceship operator `<=>`
- [ ] Arithmetic, comparison, and logical operators
- [ ] `===` vs `==` — understand this deeply before moving on

### Control Flow

- [ ] `if`, `elseif`, `else`
- [ ] `switch` and `match` — and why `match` is almost always better
- [ ] `while`, `do...while`, `for`, `foreach`
- [ ] `break`, `continue`
- [ ] Alternative syntax for control structures (used in templates)

### Functions

- [ ] Defining and calling functions
- [ ] Type declarations on parameters and return types
- [ ] Default parameter values
- [ ] Variadic functions — `...$args`
- [ ] Named arguments (PHP 8.0+)
- [ ] Return type `void`, `never`, union types (`int|string`), nullable (`?string`)
- [ ] First-class callables (`strlen(...)`)
- [ ] Anonymous functions (closures) and `use` — how variable capture works
- [ ] Arrow functions — `fn($x) => $x * 2`
- [ ] Scope — no block scope; `global` keyword; why global state is dangerous

### Arrays

- [ ] Indexed arrays, associative arrays, multidimensional arrays
- [ ] Array functions — `array_map`, `array_filter`, `array_reduce`, `array_merge`, `array_keys`, `array_values`, `in_array`, `array_search`
- [ ] Sorting — `sort`, `usort`, `ksort`, `uasort`
- [ ] Spread operator in arrays — `[...$a, ...$b]`
- [ ] Destructuring — `[$a, $b] = [1, 2]`

### Strings

- [ ] Core string functions — `strlen`, `str_contains`, `str_starts_with`, `str_ends_with`, `substr`, `strpos`, `str_replace`, `trim`, `explode`, `implode`, `sprintf`
- [ ] Regular expressions — `preg_match`, `preg_replace`, `preg_split`
- [ ] String interpolation in double-quoted strings

### Error Handling

- [ ] Error levels — `E_ERROR`, `E_WARNING`, `E_NOTICE`, `E_ALL`
- [ ] `try`, `catch`, `finally`
- [ ] `throw` as an expression (PHP 8.0+)
- [ ] Exception hierarchy — `Exception`, `Error`, `Throwable`
- [ ] Creating custom exception classes
- [ ] `set_exception_handler` and `set_error_handler`

### Working with Files & I/O

- [ ] `file_get_contents`, `file_put_contents`
- [ ] `fopen`, `fread`, `fwrite`, `fclose`
- [ ] Reading directories — `scandir`, `glob`, `DirectoryIterator`
- [ ] JSON — `json_encode`, `json_decode`, handling errors
- [ ] CSV — `fgetcsv`, `fputcsv`
- [ ] File existence and metadata — `file_exists`, `is_file`, `is_dir`, `pathinfo`

### PHP & the Web

- [ ] Superglobals — `$_GET`, `$_POST`, `$_SERVER`, `$_SESSION`, `$_COOKIE`, `$_ENV`
- [ ] Form handling and input validation — never trust user input
- [ ] `htmlspecialchars` — why every output must be escaped
- [ ] Sessions — `session_start()`, storing and reading session data
- [ ] Headers — `header()`, redirects, content types
- [ ] HTTP methods — GET vs POST and when to use each

### Databases

- [ ] PDO — the right way to talk to a database in PHP
- [ ] Prepared statements — parameterized queries, never string-concatenated SQL
- [ ] Fetching rows — `fetch`, `fetchAll`, `fetchColumn`
- [ ] Transactions — `beginTransaction`, `commit`, `rollBack`
- [ ] Understanding SQL injection and why prepared statements prevent it

### Checkpoint ✓
> Build a data-driven web page: a form that takes user input, validates it, stores it in a database using PDO and prepared statements, and displays the results — with proper escaping on output. No framework. No classes yet. Just clean procedural PHP.

---

## Stage 2 — Object-Oriented PHP

> PHP's OOP model is close to Java's in syntax but has PHP-specific quirks. Learn them explicitly — don't assume it works like another language.

### Classes & Objects

- [ ] Defining a class, instantiating with `new`
- [ ] Properties — typed properties (PHP 7.4+), nullable types
- [ ] Constructor — `__construct`, constructor promotion (PHP 8.0+)
- [ ] Access modifiers — `public`, `protected`, `private`
- [ ] `$this` — what it refers to and when it's not available
- [ ] Object cloning — `clone` and `__clone`
- [ ] Object comparison — `==` vs `===` for objects

### Constructor Promotion

```php
// Instead of this:
class User {
    public function __construct(
        private string $name,
        private string $email,
    ) {}
}
```

- [ ] Understand the shorthand and when it improves readability

### Static Members

- [ ] `static` properties and methods
- [ ] `self::` vs `static::` — late static binding
- [ ] When static is appropriate (rarely) vs. when it's a hidden global

### Magic Methods

- [ ] `__construct`, `__destruct`
- [ ] `__toString`
- [ ] `__get`, `__set`, `__isset`, `__unset`
- [ ] `__call`, `__callStatic`
- [ ] `__invoke`
- [ ] `__clone`
- [ ] `__debugInfo`
- [ ] Serialization — `__serialize`, `__unserialize`

### The Four Pillars — in PHP

- [ ] **Encapsulation** — access modifiers, typed properties, no public property mutation without intent
- [ ] **Abstraction** — abstract classes, interfaces, hiding implementation
- [ ] **Inheritance** — `extends`, `parent::`, method overriding
- [ ] **Polymorphism** — same method, different behavior; type-hinting against interfaces

### Inheritance in Depth

- [ ] `extends` — single inheritance only in PHP
- [ ] `parent::` — calling parent constructor and methods
- [ ] `final` classes and methods — preventing extension
- [ ] Abstract classes — `abstract class`, `abstract` methods
- [ ] When to use abstract class vs. interface

### Interfaces

- [ ] Defining and implementing interfaces with `implements`
- [ ] A class can implement multiple interfaces
- [ ] Interface constants
- [ ] Interface type hinting — why you should type-hint against interfaces, not classes
- [ ] Extending interfaces

### Traits

- [ ] Defining and using traits with `use`
- [ ] Trait conflict resolution — `insteadof`, `as`
- [ ] Abstract methods in traits
- [ ] Properties in traits
- [ ] When traits solve a real problem vs. when they obscure design problems

### Enums (PHP 8.1+)

- [ ] Pure enums vs. backed enums (string/int)
- [ ] Enum methods and interfaces
- [ ] `cases()`, `from()`, `tryFrom()`
- [ ] Using enums instead of class constants

### Readonly Properties & Classes

- [ ] `readonly` properties (PHP 8.1+)
- [ ] Readonly classes (PHP 8.2+)
- [ ] When immutability is the right default

### Namespaces & Autoloading

- [ ] Declaring namespaces
- [ ] `use` statements — importing classes, aliasing
- [ ] PSR-4 autoloading standard
- [ ] Configuring autoloading in `composer.json`
- [ ] How Composer's autoloader works

### Type System

- [ ] Union types — `int|string`
- [ ] Intersection types — `Countable&Iterator`
- [ ] `mixed`, `never`, `void`
- [ ] Nullables — `?string`
- [ ] Return type covariance and parameter type contravariance
- [ ] `declare(strict_types=1)` — always, everywhere

### Fibers (PHP 8.1+)

- [ ] What a Fiber is — cooperative concurrency
- [ ] `Fiber::suspend()`, `Fiber::resume()`
- [ ] Where Fibers are used (async frameworks, event loops)

### Checkpoint ✓
> Rebuild your Stage 1 project using classes. Model the domain — User, Post, Database, whatever fits. Use an interface for the data access layer. Use constructor promotion and typed properties throughout. Then add one feature you didn't plan for, and observe where the design resists you.

---

## Stage 3 — Design Patterns Prerequisites

> The thinking that makes patterns make sense. Skip this and you'll memorize shapes without understanding why they exist.

### SOLID Principles in PHP

- [ ] **S** — Single Responsibility: one class, one reason to change
- [ ] **O** — Open/Closed: extend behavior without modifying existing code
- [ ] **L** — Liskov Substitution: subtypes must be substitutable for their base type
- [ ] **I** — Interface Segregation: small, focused interfaces over fat ones
- [ ] **D** — Dependency Inversion: depend on abstractions; inject concrete implementations

For each: find a violation in your own code, explain exactly why it's a violation, then fix it.

### Core Design Concepts

- [ ] Coupling — tight vs. loose; why tightly coupled code resists change
- [ ] Cohesion — a class that does one thing is easier to test, change, and understand
- [ ] Separation of concerns — logic, data access, and presentation in separate layers
- [ ] DRY — and when enforcing it creates wrong abstractions
- [ ] YAGNI — premature abstraction is technical debt with better PR

### PHP-Specific Tools Patterns Use

- [ ] Closures passed as callbacks — how patterns use them in PHP
- [ ] Anonymous classes — `new class implements SomeInterface { ... }`
- [ ] Attributes (PHP 8.0+) — `#[Attribute]` and how frameworks use them
- [ ] `clone` — used in Prototype pattern
- [ ] Late static binding — used in Singleton and factories
- [ ] SPL data structures — `SplStack`, `SplQueue`, `SplDoublyLinkedList`
- [ ] SPL interfaces — `Iterator`, `Countable`, `ArrayAccess`, `Serializable`

### PSR Standards (Read These)

- [ ] PSR-1 — Basic coding standard
- [ ] PSR-12 — Extended coding style
- [ ] PSR-4 — Autoloading
- [ ] PSR-7 — HTTP message interfaces
- [ ] PSR-11 — Container interface (used by DI containers)
- [ ] PSR-14 — Event dispatcher interface (Observer pattern standardized)
- [ ] PSR-15 — HTTP handlers and middleware

### Reading Real Code

- [ ] Read the source of one package you use (Carbon, Symfony Console, Guzzle)
- [ ] Find where classes are composed vs. extended — and why
- [ ] Find one place that's over-engineered and explain what you'd simplify

### Checkpoint ✓
> Audit your Stage 2 project against SOLID. Write down every violation. Fix the worst one. You're ready for Stage 4 when you can explain the *why* of each violation, not just which principle it breaks.

---

## Stage 4 — Design Patterns

> Learn each one in code that has the problem. Not in isolated examples. In something you built.

### Creational Patterns

- [ ] **Singleton** — one instance, globally accessible; learn it, then learn why it's overused
  - PHP-specific: thread safety is mostly irrelevant here; focus on testability problems
- [ ] **Factory Method** — delegate object creation to subclasses; eliminates `instanceof` chains
- [ ] **Abstract Factory** — create families of related objects without specifying concrete classes
- [ ] **Builder** — construct complex objects step by step; fluent interface variant common in PHP
- [ ] **Prototype** — clone existing objects; understand PHP's `clone` and `__clone`

### Structural Patterns

- [ ] **Adapter** — wrap an incompatible interface; common when integrating third-party packages
- [ ] **Decorator** — add behavior by wrapping, not by extending; middleware is this pattern
- [ ] **Facade** — simplified interface over a complex subsystem; service classes often are facades
- [ ] **Proxy** — control access to another object; lazy loading, logging, caching proxies
- [ ] **Composite** — treat individual objects and trees uniformly; menu systems, DOM-like structures
- [ ] **Bridge** — decouple abstraction from implementation so both can vary independently
- [ ] **Flyweight** — share state across many similar objects; useful with large collections

### Behavioral Patterns

- [ ] **Observer** — notify subscribers when state changes; PSR-14 EventDispatcher is this pattern
- [ ] **Strategy** — swap algorithms at runtime; replaces if/elseif chains with pluggable objects
- [ ] **Command** — encapsulate a request as an object; enables undo, queuing, logging
- [ ] **Template Method** — skeleton in the parent, steps filled in by subclasses
- [ ] **Iterator** — traverse collections without exposing internals; implement SPL `Iterator`
- [ ] **State** — object changes behavior when its internal state changes
- [ ] **Chain of Responsibility** — pass a request along a chain; PSR-15 middleware is this
- [ ] **Mediator** — centralize complex communication between objects
- [ ] **Memento** — capture and restore object state; undo functionality
- [ ] **Visitor** — add operations to object structures without modifying them
- [ ] **Interpreter** — define a grammar and interpret expressions; query builders, rule engines

### PHP-Specific Pattern Applications

- [ ] Middleware pipeline — Decorator + Chain of Responsibility together (PSR-15)
- [ ] Repository pattern — abstraction over data access; type-hint against an interface
- [ ] Service Container / DI Container — autowiring, binding interfaces to implementations
- [ ] Active Record vs. Data Mapper — understand the tradeoff before reaching for an ORM

### For Each Pattern, Do All Three

- [ ] Read the definition and draw the class diagram by hand
- [ ] Find it in a real PHP library or framework (Laravel, Symfony, Slim)
- [ ] Implement it in your own code where the problem actually exists

### Checkpoint ✓
> You can identify a missing pattern in a codebase and explain what it would fix. You've argued against applying a pattern in at least one real situation and been right. You've refactored something messy into something clean using at least three patterns.

---

## Stage 5 — Putting It Together

> Individual patterns are micro-decisions. This stage connects them into systems.

### Architectural Patterns

- [ ] MVC — where GoF patterns live inside it; how Laravel and Symfony implement it
- [ ] Layered architecture — presentation, application, domain, infrastructure
- [ ] Hexagonal architecture (Ports & Adapters) — domain has no framework dependencies
- [ ] CQRS — separate read and write models; when it's worth the complexity
- [ ] Event-driven architecture — events, listeners, event sourcing at a conceptual level
- [ ] Repository + Unit of Work — the data access layer done properly

### Dependency Injection

- [ ] Manual DI — passing dependencies through constructors
- [ ] DI containers — PSR-11, how autowiring works
- [ ] Service providers — registering bindings in Laravel or Symfony
- [ ] Why DI is not the same thing as a service locator

### Testing

- [ ] Unit testing with PHPUnit
- [ ] Test doubles — mocks, stubs, spies, fakes
- [ ] Mocking interfaces with Mockery or PHPUnit mocks
- [ ] Why DI makes code testable and global state doesn't
- [ ] Test-driven development — at minimum, try it for two weeks

### Code Quality

- [ ] Static analysis — PHPStan or Psalm; run at max level
- [ ] Code style — PHP-CS-Fixer or PHP_CodeSniffer
- [ ] Code review — giving and receiving feedback on design decisions
- [ ] Reading *Refactoring* by Fowler alongside patterns — they pair directly

### Ongoing

- [ ] Read the source of Laravel or Symfony — find every GoF pattern in it
- [ ] Contribute to an open-source PHP package
- [ ] Re-read the Gang of Four after 6 months of real production code — it reads differently

---

## Reference: Books in Order

| When | Book |
|------|------|
| Stage 1–2 | *PHP 8 Objects, Patterns and Practice* — Matt Zandstra |
| Stage 2 | *Modern PHP* — Josh Lockhart |
| Stage 3 | *Clean Code* — Robert C. Martin |
| Stage 4 | *Head First Design Patterns* — Freeman & Robson |
| Stage 4 | *Design Patterns* (GoF) — read after Head First, not before |
| Stage 5 | *Refactoring* — Martin Fowler |
| Stage 5 | *Clean Architecture* — Robert C. Martin |
| Stage 5 | *Domain-Driven Design* — Eric Evans (dense; worth it) |

---

## Reference: PHP Pattern Landmarks in the Wild

| Pattern | Where to Find It |
|---------|-----------------|
| Singleton | `DB::connection()` in early Laravel (now replaced by DI) |
| Factory | `DB::table()`, `Cache::driver()` in Laravel |
| Builder | Query builder in Laravel/Doctrine; `MailMessage` builder |
| Facade | Laravel's Facade system (static proxies over DI container) |
| Observer | Laravel model events; Symfony EventDispatcher (PSR-14) |
| Decorator | Guzzle middleware stack; PSR-15 middleware pipelines |
| Strategy | Laravel's cache drivers, mail drivers, queue drivers |
| Command | Laravel's Artisan commands; `illuminate/bus` |
| Iterator | `Collection` in Laravel; SPL iterators |
| Chain of Responsibility | PSR-15 middleware; Laravel's pipeline |
| Template Method | Laravel's base Controller, Model, Command classes |
| Composite | Symfony Form types; tree-structured menu builders |

---

*A checked box means you've done it, not read about it. The difference is everything.*
