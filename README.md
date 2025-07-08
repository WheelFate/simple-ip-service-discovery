# Simple IP-Based Service Discovery (Static Simulation)

## Project Overview

This project demonstrates the fundamental concepts of **Service Discovery** using entirely static files hosted on GitHub Pages. It simulates a basic service registry where "services" (simple HTML pages) register their information (like IP, port, description, and status) in a central JSON file. A "client" application (the main `index.html` page) then queries this registry to "discover" and display available services.

This project requires **no installations** and is **completely free** to host and run.

## Features

* **Static Service Registry (`registry.json`):** A central JSON file acts as the database for all registered services.
* **Individual Service Pages (`service_a.html`, `service_b.html`, `service_c.html`):** Each page represents a distinct "service" and displays its registered information, including its simulated status.
* **Client-Side Service Discovery (`index.html`):** The main application page fetches data from `registry.json` and dynamically renders the discovered services.
* **Search/Filter Functionality:** Users can search for services by name or description directly from the client page.
* **Simulated Service Health Status:** Services have a `status` field (`"up"` or `"down"`) in the registry, and the client page visually reflects this status.
* **Easy Navigation:** Links from the client page to individual service pages, and a "Back to Client" link on service pages.

## How to Use/View

Simply open the project's GitHub Pages URL in your web browser:
[https://wheelfate.github.io/simple-ip-service-discovery/](https://wheelfate.github.io/simple-ip-service-discovery/)

You can also navigate directly to individual service pages:
* [ServiceA Page](https://wheelfate.github.io/simple-ip-service-discovery/service_a.html)
* [ServiceB Page](https://wheelfate.github.io/simple-ip-service-discovery/service_b.html)
* [ServiceC Page](https://wheelfate.github.io/simple-ip-service-discovery/service_c.html)

## How It Works

1.  **`registry.json`:** This file holds an array of JSON objects, each representing a "service" with properties like `name`, `ip_address`, `port`, `description`, and `status`.
2.  **`index.html` (The Client):**
    * Uses JavaScript's `fetch` API to retrieve `registry.json`.
    * Parses the JSON data.
    * Dynamically creates HTML elements (`div` cards) for each service.
    * Displays the service details, including a color-coded status.
    * Includes a search bar and buttons to filter services by name/description or reset the filter.
    * Each service name is a hyperlink to its dedicated service page.
3.  **`service_a.html`, `service_b.html`, `service_c.html` (The Services):**
    * Each page specifically queries `registry.json` to find its own corresponding entry based on its `serviceName`.
    * It then displays its own registered details and status.
    * Includes a link back to the main client page.

## Simulating Changes & Health Checks

To simulate a service update or a service going "down":

1.  **Edit `registry.json`** directly on GitHub.
2.  Change a service's `ip_address`, `port`, `description`, or critically, its `status` (e.g., from `"up"` to `"down"`).
3.  Commit your changes.
4.  After GitHub Pages deploys (usually 1-2 minutes), refresh your main client page (`index.html`). You will see the updated information reflected instantly.

## Limitations & Real-World Service Discovery

This project is a simplified simulation. In real-world distributed systems, service discovery is much more complex and dynamic. This static approach has several limitations:

* **Manual Updates:** The `registry.json` must be manually updated when services change or come online/offline.
* **No Dynamic Registration:** Services cannot automatically register or deregister themselves.
* **No Real Health Checks:** The `status` field is manually updated. Real systems have automated health checks (e.g., pings, heartbeats) to determine if a service is truly alive.
* **Single Point of Failure:** If `registry.json` becomes inaccessible, service discovery fails.
* **Scalability:** Not suitable for large numbers of frequently changing services.

Real-world service discovery solutions like **Consul**, **Eureka**, **etcd**, and **Kubernetes' built-in service discovery** address these limitations by providing:
* Dynamic service registration and deregistration APIs.
* Automated health checking mechanisms.
* Highly available and distributed registries.
* Integration with load balancing and routing.

This project serves as an excellent foundation to understand the core problem that these powerful tools solve.
