# Mergetable

## Project Overview
Mergetable is a Spring Boot project that demonstrates entity merging using JPA event listeners. Instead of using database triggers, it listens for Hibernate insert events on the `User` and `Address` tables and updates a third table, `OneForAll`, which contains combined fields from both entities.

## Features
- **JPA Event Listeners**: Automatically updates `OneForAll` when `User` or `Address` is created.
- **No Database Triggers**: Ensures data consistency at the application level.
- **Simple API**: Supports only create operations for testing merging.

## Tech Stack
- **Backend**: Java (Spring Boot)
- **Database**: MySQL (or any relational database)
- **ORM**: Hibernate with JPA event listeners

## How It Works
1. **User Table** → Stores user-related data.
2. **Address Table** → Stores address-related data.
3. **OneForAll Table** → Stores combined fields from `User` and `Address`.
4. **JPA Event Listeners** detect insert operations in `User` and `Address` and automatically populate `OneForAll`.

## Installation & Setup
### Prerequisites
- Java 17+
- MySQL database
- Maven

### Steps
1. Clone the repository:
   ```sh
   git clone https://github.com/aditya9389/mergetable.git
   cd mergetable
   ```
2. Configure the database in `application.properties`:
   ```properties
   spring.datasource.url=jdbc:mysql://localhost:3306/mergetable
   spring.datasource.username=root
   spring.datasource.password=root
   spring.jpa.hibernate.ddl-auto=update
   ```
3. Run the application:
   ```sh
   mvn spring-boot:run
   ```

## API Endpoint
### Create User & Address (Triggers OneForAll Update)
- **Endpoint:** `POST /create`
- **Description:** Inserts a new user and address, triggering the `OneForAll` table update.
- **Request Body Example:**
   ```json
   {
     "user": {
       "name": "John Doe",
       "email": "john@example.com"
     },
     "address": {
       "street": "123 Main St",
       "city": "New York"
     }
   }
   ```

## Future Improvements
- Add update and delete event handling.
- Implement API for fetching merged data.
- Expand to support more entity relationships.

## Contact
For any questions, feel free to reach out via email or GitHub issues.

