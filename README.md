# Employee Management Portal

A Spring Boot application for managing employee information with Docker support.

## Technologies Used

- Java 17
- Spring Boot 3.1.3
- PostgreSQL
- Docker
- Maven
- JPA/Hibernate
- RESTful API

## Prerequisites

- Docker and Docker Compose
- Java 17 (for local development)
- Maven (for local development)

## Project Structure

```
portal-jv/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/portal/
│   │   │       ├── controller/
│   │   │       ├── model/
│   │   │       ├── repository/
│   │   │       ├── service/
│   │   │       └── PortalApplication.java
│   │   └── resources/
│   │       └── application.properties
├── Dockerfile
├── docker-compose.yml
├── .dockerignore
├── pom.xml
└── README.md
```

## Features

- Employee CRUD operations
- Search functionality
- Soft delete support
- RESTful API endpoints
- Docker containerization
- Persistent database storage

## API Endpoints

- GET `/api/employees` - Get all employees
- GET `/api/employees?activeOnly=true` - Get active employees only
- GET `/api/employees/{id}` - Get employee by ID
- POST `/api/employees` - Create new employee
- PUT `/api/employees/{id}` - Update employee
- DELETE `/api/employees/{id}` - Soft delete employee
- GET `/api/employees/search?query={searchTerm}` - Search employees

## Running with Docker

1. Clone the repository:
   ```bash
   git clone https://github.com/jahangir842/portal-jv.git
   cd portal-jv
   ```

2. Build and start the containers:
   ```bash
   docker-compose up -d --build
   ```

3. The application will be available at:
   ```
   http://localhost:8080
   ```

4. Stop the containers:
   ```bash
   docker-compose down
   ```

## Local Development Setup

1. Install Java 17:
   ```bash
   sudo apt install -y wget apt-transport-https
   wget -O - https://packages.adoptium.net/artifactory/api/gpg/key/public | sudo tee /etc/apt/trusted.gpg.d/adoptium.asc
   echo "deb https://packages.adoptium.net/artifactory/deb $(awk -F= '/^VERSION_CODENAME/{print$2}' /etc/os-release) main" | sudo tee /etc/apt/sources.list.d/adoptium.list
   sudo apt update && sudo apt install -y temurin-17-jdk
   ```

2. Install PostgreSQL:
   ```bash
   sudo apt install postgresql postgresql-contrib
   ```

3. Create database:
   ```bash
   sudo -u postgres psql
   CREATE DATABASE employee_portal;
   \q
   ```

4. Build and run the application:
   ```bash
   mvn clean install
   java -jar target/portal-jv-1.0-SNAPSHOT.jar
   ```

## Environment Variables

The following environment variables can be configured:

- `SPRING_DATASOURCE_URL` - Database URL (default: jdbc:postgresql://localhost:5432/employee_portal)
- `SPRING_DATASOURCE_USERNAME` - Database username (default: postgres)
- `SPRING_DATASOURCE_PASSWORD` - Database password (default: postgres)
- `SPRING_JPA_HIBERNATE_DDL_AUTO` - Hibernate DDL mode (default: update)

## Docker Container Management

### View logs
```bash
# All containers
docker-compose logs -f

# Specific container
docker-compose logs -f app
docker-compose logs -f db
```

### Restart containers
```bash
docker-compose restart
```

### Stop and remove everything
```bash
docker-compose down -v
```

## Database Management

The PostgreSQL database is persisted using Docker volumes. Data will survive container restarts.

To reset the database:
1. Stop the containers: `docker-compose down`
2. Remove volumes: `docker-compose down -v`
3. Restart: `docker-compose up -d`

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## License

This project is licensed under the MIT License.
- Role-based access control
- Dashboard with employee statistics

## Tech Stack

- Java 17
- Spring Boot 3.x
- Spring Security
- Spring Data JPA
- PostgreSQL
- Maven
- Thymeleaf (for server-side rendering)
- Bootstrap 5 (for styling)

## Prerequisites

- JDK 17 or later
- Maven 3.8+
- PostgreSQL 14+

## Installing Maven

### For Linux:
```bash
# Update package index
sudo apt update

# Install Maven
sudo apt install maven

# Verify installation
mvn -version
```

### For macOS:
```bash
# Using Homebrew
brew install maven

# Verify installation
mvn -version
```

### For Windows:
1. Download Maven from the [official website](https://maven.apache.org/download.cgi)
2. Extract the downloaded archive to a directory (e.g., `C:\Program Files\Apache\maven`)
3. Add Maven to system environment variables:
   - Add `M2_HOME` variable pointing to Maven installation directory
   - Add `%M2_HOME%\bin` to the `Path` variable
4. Verify installation:
   ```cmd
   mvn -version
   ```

### Manual Installation (Any OS):
1. Download Maven binary from [Apache Maven website](https://maven.apache.org/download.cgi)
2. Extract the archive to your preferred location
3. Add the following to your environment variables:
   ```
   M2_HOME=/path/to/maven
   PATH=$PATH:$M2_HOME/bin
   ```
4. Verify installation:
   ```bash
   mvn -version
   ```

## Project Structure

```
portal-jv/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/portal/
│   │   │       ├── controller/    # REST controllers
│   │   │       ├── model/         # Entity classes
│   │   │       ├── repository/    # JPA repositories
│   │   │       └── service/       # Business logic
│   │   └── resources/
│   │       ├── static/           # CSS, JS, images
│   │       ├── templates/        # Thymeleaf templates
│   │       └── application.yml   # Application config
│   └── test/                    # Test classes
└── pom.xml                      # Maven configuration
```

## Getting Started

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/portal-jv.git
   cd portal-jv
   ```

2. Configure the database:
   - Create a PostgreSQL database named `employee_portal`
   - Update `src/main/resources/application.yml` with your database credentials

3. Build the project:
   ```bash
   mvn clean install
   ```

4. Run the application:
   ```bash
   mvn spring-boot:run
   ```

5. Access the application:
   Open your browser and navigate to `http://localhost:8080`

## Database Configuration

The application uses PostgreSQL. Update the following properties in `application.yml`:

```yaml
spring:
  datasource:
    url: jdbc:postgresql://localhost:5432/employee_portal
    username: your_username
    password: your_password
```

## Default Users

The system comes with two default users:

1. Admin:
   - Username: admin@portal.com
   - Password: admin123

2. Employee:
   - Username: user@portal.com
   - Password: user123

## Features in Detail

### Employee Management
- Add new employees
- Update employee information
- View employee details
- Delete employee records
- Search employees by various criteria

### Department Management
- Create and manage departments
- Assign employees to departments
- Transfer employees between departments
- Department-wise reporting

### Leave Management
- Apply for leave
- Approve/reject leave requests
- View leave history
- Leave balance tracking

### Role-based Access
- Admin role with full access
- Manager role with department-level access
- Employee role with personal access

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details
