# EnduranceResearch-Backend

Backend server for the Výzkum Odolnosti (Endurance Research) project. This application manages research participant data, questionnaire forms, and Garmin device integrations.

## Features

- REST API for research participant management
- Integration with Garmin Connect for sleep and activity data
- Questionnaire form submission and evaluation (PSQI, MEQ, MCTQ, PSS, Life Satisfaction, Demo)
- XLS export of collected data
- OAuth1 authentication for Garmin device registration
- Admin and reader roles for data access

## Project Structure

```
├── src/
│   ├── main/
│   │   ├── java/cz/cvut/fel/vyzkumodolnosti/
│   │   │   ├── controllers/
│   │   │   ├── model/
│   │   │   ├── repository/
│   │   │   ├── security/
│   │   │   ├── services/
│   │   │   └── utils/
│   │   └── resources/
│   │       └── public/
│   └── test/
├── lib/
├── gradle/
├── Dockerfile
├── docker-compose.yaml
├── build.gradle
├── .gitlab-ci.yml
├── README.md
└── ...
```

## Getting Started

### Prerequisites

- Java 11+
- Gradle
- PostgreSQL database

### Configuration

1. Copy and edit `application.properties` or create a `.env` file with the following parameters:

    ```
    DATASOURCE_URL=jdbc:postgresql://localhost:5432/yourdb
    DATASOURCE_USERNAME=youruser
    DATASOURCE_PASSWORD=yourpassword
    server.servlet.session.cookie.secure=true
    localdev=true
    fe_addr_one=localhost:8080
    vophp.api.accesstoken=yourtoken
    ```

2. Ensure your PostgreSQL server is running and accessible.

### Build and Run

To build and run the project locally:

```sh
./gradlew build
./gradlew bootRun
```

Or using Docker Compose:

```sh
docker-compose up --build
```

### Database

The application uses PostgreSQL. You can use the provided `postgres.yaml` for deployment or configure your own instance.

### API Documentation

- OpenAPI/Swagger: See [`swagger.yml`](swagger.yml)
- Example endpoints:
    - `/garmin/sleeps` - Sleep data endpoints
    - `/form-read` - Questionnaire data endpoints
    - `/garmin/oauthCallback` - Garmin OAuth callback

### XLS Export

Admin and reader roles can export data in XLS format via endpoints such as `/garmin/sleeps/export`.

## Development

- Java code is under `src/main/java/cz/cvut/fel/vyzkumodolnosti/`
- Static web resources are in `src/main/resources/public/`
- Unit tests are in `src/test/java/`

## License
MIT

---

For more information, see the code and comments in the repository.