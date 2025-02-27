# Hiring Portal Backend

## Overview
The Hiring Portal Backend is a Spring Boot application that provides a REST API for managing job postings. It allows users to create job posts, search for jobs based on text queries, and retrieve all job listings. The application uses MongoDB as the database and integrates Swagger for API documentation.

## Features
- **Create Job Posts**: Add new job postings with relevant details like profile, description, experience required, and technologies.
- **Retrieve All Job Posts**: Fetch all available job listings.
- **Search Job Posts**: Search for job listings using a text query that matches profile names, descriptions, or technologies.
- **Swagger API Documentation**: Provides an interactive API documentation interface.

## Technologies Used
- **Java 17+**
- **Spring Boot 2.x**
- **Spring Data MongoDB**
- **MongoDB**
- **Swagger 2**
- **Spring Web**
- **Spring Boot Testing**

## Project Structure
```
com.telusko.joblisting
│── controller
│   ├── PostController.java
│── model
│   ├── Post.java
│── repository
│   ├── PostRepository.java
│   ├── SearchRepository.java
│   ├── SearchRepositoryImpl.java
│── JoblistingApplication.java
│── JoblistingApplicationTests.java
```

## API Endpoints
### Redirect to Swagger UI
```http
GET /
```
- Redirects to the Swagger UI page.

### Get All Job Posts
```http
GET /allPosts
```
- Returns a list of all job posts stored in the database.

### Search Job Posts
```http
GET /posts/{text}
```
- Searches job posts using the given text query.
- Searches through the `profile`, `desc`, and `techs` fields.
- Results are sorted by experience and limited to 5 records.

### Add a Job Post
```http
POST /post
Content-Type: application/json
```
#### Request Body
```json
{
  "profile": "Software Engineer",
  "desc": "Looking for a Java Developer",
  "exp": 3,
  "techs": ["Java", "Spring Boot", "MongoDB"]
}
```
#### Response
```json
{
  "profile": "Software Engineer",
  "desc": "Looking for a Java Developer",
  "exp": 3,
  "techs": ["Java", "Spring Boot", "MongoDB"]
}
```

## Setup & Installation
### Prerequisites
- **Java 17+**
- **Maven**
- **MongoDB (running on default port 27017)**

### Steps to Run
1. Clone the repository:
   ```sh
   git clone https://github.com/your-repo/hiring-portal.git
   cd hiring-portal
   ```
2. Start MongoDB (if not already running):
   ```sh
   mongod
   ```
3. Build and run the project:
   ```sh
   mvn spring-boot:run
   ```
4. The application will start at `http://localhost:8080`.
5. Access Swagger UI for API documentation at:
   ```sh
   http://localhost:8080/swagger-ui.html
   ```

## Testing
Run the tests using:
```sh
mvn test
```

## Future Enhancements
- Implement authentication and authorization using JWT.
- Add pagination for job listings.
- Improve search functionality using advanced filtering.

## License
This project is open-source and available under the MIT License.
