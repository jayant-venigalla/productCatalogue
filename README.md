# Extensible Product Catalog

## Objective

Develop a scalable and extensible solution to manage product information currently maintained on a wiki page. The new solution will centralize product data in a structured format, allowing easy management, retrieval, and updating via a web interface and a database backend. Additionally, explore the feasibility of integrating with ServiceNow for enhanced product management and version control.

## Functional Requirements

### Product Information Management

- **Add, Update, Delete, View Products**: Users should be able to manage product information through a user-friendly interface.
- **Product Attributes**:
  - Name
  - Description
  - Category
  - SKU
  - Supplier Information
  - Status (Active, Discontinued)
- **Extensibility**: System should allow the addition of new product attributes without significant redesign (e.g., customizable fields).

### Search and Filter Products

- Implement search functionality to locate products based on attributes such as name, category, SKU, and status.
- Provide filtering options by category, supplier, and status.

### Product Versioning (Optional)

- Track historical changes to product information to allow versioning and rollbacks if necessary.

### Integration with ServiceNow

- Explore integrating product catalog management with ServiceNow for improved workflow, such as tracking product lifecycle or changes through ServiceNow’s ITSM capabilities.

## Non-Functional Requirements

### Scalability

- The system should handle growth in product catalog size, supporting many products and frequent updates.

### Security

- Implement authentication and role-based access control (RBAC) to restrict access to the product management system.
- Protect sensitive data like supplier information and pricing.

### Performance

- Ensure fast retrieval and updates of product data, even with a large dataset.
- A page should load within 3 seconds for optimal user experience.

### Extensibility

- Support future expansion to include additional product attributes or integration with other systems without significant restructuring.

### Usability

- The UI should be intuitive and easy for non-technical users to interact with.
- Provide comprehensive error handling and user-friendly messages.

## System Architecture

### Frontend (Angular)

- Create a responsive web application for managing the product catalog.
- Use Angular components to handle forms, lists, search, and filtering.
- Implement validation and error handling for user inputs.

### Backend (Spring Boot)

- Develop RESTful APIs for managing product data.
- Implement services for CRUD operations (Create, Read, Update, Delete) on the product catalog.
- Handle business logic for versioning, product status, and integration with external systems like ServiceNow.

### Database (PostgreSQL)

- Design a normalized schema for storing product information.
- Ensure schema supports additional fields without major refactoring.
- Index key fields (e.g., product name, SKU) for efficient querying.
- Implement product versioning (optional).

## Database Schema (High-Level)

### Tables

- **Products**: `id`, `name`, `description`, `category`, `sku`, `status`, `created_at`, `updated_at`
- **Suppliers**: `id`, `name`, `contact_info`, `created_at`, `updated_at`
- **Product_Attributes**: `id`, `product_id`, `attribute_key`, `attribute_value`, `created_at`
- **Product_Versions (Optional)**: `id`, `product_id`, `version_number`, `change_description`, `created_at`

## API Endpoints (Sample)

- `GET /products`: Retrieve a list of products with optional filters for search.
- `POST /products`: Add a new product to the catalog.
- `PUT /products/{id}`: Update product details.
- `DELETE /products/{id}`: Remove a product from the catalog.
- `GET /products/{id}/history`: Retrieve version history (if versioning is implemented).

## Integration Points

### ServiceNow

- Investigate using ServiceNow APIs for syncing or storing product-related workflows (e.g., when a product is marked for review, updates are reflected in ServiceNow).
- Explore automated notifications for changes to product status (Active to Discontinued).

## User Stories

- As a user, I want to view all products in the catalog so that I can see what is available.
- As an admin, I want to add new products so that the catalog remains up to date.
- As an admin, I want to modify existing product details so that the product information is always accurate.
- As a user, I want to search for products by category or SKU to quickly find specific items.
- As a product manager, I want to track product history to revert changes if necessary.

## Milestones and Timeline

### Phase 1: Initial Setup

- Set up database, Spring Boot backend, and Angular frontend
- Basic CRUD operations on products

### Phase 2: Search, Filtering, and Extensibility

- Implement search and filtering functionality
- Support dynamic product attributes

### Phase 3: Integration with ServiceNow

- Investigate and implement integration with ServiceNow for product management workflows

### Phase 4: Testing and Deployment

- Comprehensive testing (unit, integration, performance)
- Deployment to production

## Dependencies

- PostgreSQL database setup
- ServiceNow API access
- Spring Boot, Angular development environment

## Risks and Mitigation

- **Risk**: Complexity in adding new attributes dynamically.
  - **Mitigation**: Design a flexible schema using key-value pairs for additional product attributes.
- **Risk**: ServiceNow integration may introduce unexpected delays.
  - **Mitigation**: Investigate and prototype ServiceNow API integration early in the project.

## Acceptance Criteria

- Users can add, update, delete, and search products.
- System supports dynamic addition of new product attributes.
- ServiceNow integration is tested and functional for managing product lifecycle workflows (if required).
