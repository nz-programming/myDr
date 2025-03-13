# myDr

Your partner in preventing disease by tracking and analyzing your life log.

## What is it?

myDr logs and analyzes your life, unveiling insights about your lifestyle. The main function is to reason through your life log.

## Main Features

- Analyze your life log from your life log tracker (currently, only Fitbit is supported).

## Requirements

- Fitbit life log tracking device
- Fitbit account

## How it Works

- **Data Retrieval**: Use the Fitbit API to obtain your life log data.
- **Analysis**: Utilize Gemini to analyze and reason through the obtained life log data.

## How to Use

1. Use your Fitbit device to record your daily activities.
2. Open the myDr app and log in with your Fitbit account.
3. The app will automatically retrieve data through the Fitbit API and start the analysis.
4. Review the analysis results to gain insights and tips for lifestyle improvements.

## System Architecture

```mermaid
graph TD
    subgraph "Frontend"
    A[User Interface<br>TypeScript + React]
    end
    
    subgraph "Backend"
    B[API Gateway<br>TypeScript + Express.js]
    C[Data Processing Module]
    D[(Database<br>GCP Firestore/Cloud SQL)]
    end
    
    subgraph "External Services"
    E[Fitbit API]
    F[Gemini AI]
    end
    
    A <--> B
    B --> C
    C --> D
    C <--> E
    C <--> F
    D <--> F
    
    style A fill:#d4f1f9,stroke:#333,stroke-width:1px
    style B fill:#dff9d4,stroke:#333,stroke-width:1px
    style C fill:#dff9d4,stroke:#333,stroke-width:1px
    style D fill:#dff9d4,stroke:#333,stroke-width:1px
    style E fill:#f9ecd4,stroke:#333,stroke-width:1px
    style F fill:#f9ecd4,stroke:#333,stroke-width:1px
```

### Data Flow

1. Users access the application through the frontend interface
2. The backend API gateway processes requests
3. The data processing module retrieves users' life logs from the Fitbit API
4. Collected data is stored in the database
5. Gemini AI analyzes the data and generates insights
6. Analysis results are stored in the database and displayed on the frontend

### Deployment Architecture on GCP

```mermaid
graph TD
    A[Cloud Run<br>Frontend] --> B[Cloud Run<br>Backend API]
    B --> C[(Cloud Firestore)]
    B --> D[Cloud Functions<br>Data Processing]
    D <--> E[Fitbit API]
    D <--> F[Vertex AI<br>Gemini]
    
    style A fill:#d4f1f9,stroke:#333,stroke-width:1px
    style B fill:#dff9d4,stroke:#333,stroke-width:1px
    style C fill:#d4d4f9,stroke:#333,stroke-width:1px
    style D fill:#dff9d4,stroke:#333,stroke-width:1px
    style E fill:#f9ecd4,stroke:#333,stroke-width:1px
    style F fill:#f9d4d4,stroke:#333,stroke-width:1px
```
