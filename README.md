# 🏺 Pottery Application – C4 Modeling Brief

## Objective
You will create a **C4 model** for a new pottery marketplace application. The goal is to practice visualising software architecture at different levels of abstraction, from high-level system interactions to low-level code.

---

## 1. System Context Diagram
Define the **Pottery System** in its environment.

- **External systems** (not detailed by you):
  - **Payment System** → Handles financial transactions.
  - **Email System** → Sends confirmation and notification emails.

- **Primary users**:
  - **Potters** → Register, sign in, list pottery, manage studio information, view sales visualisations.
  - **Customers** → Register, sign in, browse pottery, make purchases.

👉 You only need to fully define the **Pottery System**. The Payment and Email systems remain external dependencies.

---

## 2. Container Diagram
Inside the Pottery System, there should be **three containers**:

1. **API Container**
   - Handles incoming HTTP requests (REST API).
   - Manages authentication (potter or customer).
   - Orchestrates business logic, interacts with the Database and the Pottery API.
   - Provides functionality specific to pottery (e.g. , pottery catalogue, sales analytics).

2. **Database Container**
   - Stores users, potters, pottery items, and orders.
   - Supplies data for visualisations consumed by potters.

3. **Pottery API Container**
   - Exposes endpoints for potters to view **data visualisations** (e.g. most sold pottery types: bowls, plates, mugs, jars).

👉 You must decide how these containers communicate (e.g. synchronous HTTP requests, asynchronous messaging, direct DB access).

---

## 3. Component Diagram (for the API Container)
Zoom into the **API Container** and identify **all the major components**:

- **Authentication Component**
  - Validates JWTs and ensures users are signed in as either a customer or a potter.
  - Provides role-based access control (e.g. potters can access analytics, customers cannot).

- **Controllers**
  - Entry points for handling requests (`/potters`, `/orders`, `/login`, `/analytics`).

- **Components**
  - Components which attatch onto external systems such as payments and the email system.

Show how these components interact within the Pottery API and externally with the Visualisation and Database Container.

---

## 4. Code (Level 4 – for Controllers)
Define code level diagrams for at least **two controllers** in your API.

Examples:
- **AuthenticationController**
  - Handles `signIn(username, password)` for both potters and customers.
  - Issues a JWT containing role information.
- **PotterController**
  - `cermaics.getAll()` → retrieves all cermaic items in the db.
  - `createCeramicPiece()` → creates a new cermaic item created by a potter to the db.

Your code should demonstrate:
- Receiving a request.
- Validating data.
- Passing work to a service.
- Returning a response.
- The protocols used to reach the API from a frontend
- The information expected to be received and returned from the request/response cycle

---

## Deliverables
1. **System Context Diagram** (Pottery System + external actors/systems).
2. **Container Diagram** (API, Database, Pottery API, with connections).
3. **Component Diagram for the API Container** (must include an Authentication Component).
4. **Sample Code** for at least two controllers in the API.
5. **Description of how authentication works** (e.g. JWTs, roles, middleware placement).

---

## Stretch Goal (Optional)
Consider:
- How the system might scale if potters want to upload images or more detailed pottery metadata.
- How analytics could evolve (e.g. visualisations of revenue per month).
