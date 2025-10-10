# Airport Simulation Distribution

This repository contains the necessary files to deploy and run the Airport Simulation application using Docker. This setup includes the user interface, the simulation server, and an RStudio environment for data analysis.

---

## TQ03000934 Project Distribution

This application was developed as part of the student project [**Research on factors affecting airport traffic performance based on developed predictive model**](https://starfos.tacr.cz/en/projekty/TQ03000934?query=6qsaaac7ljwq). The aim of the project is to develop a predictive model that will increase the predictability of aircraft movements in the tactical phase of operations based on the traffic situation and the throughput of the airport movement area as well as the accuracy of aircraft departure time estimation. To achieve the maximum level of correspondence with the real system, the model will incorporate the essential decision processes affecting taxiing and aircraft handling (including air traffic control and aircraft crew decision making). By linking experts from the university and industry, with experience in airport operations, programming, and simulation analysis, and using real data, a prototype tool applicable to real airport operations will be developed.

### Services

This distribution includes the following services, orchestrated by Docker Compose:

* [**airport-sim-ui**](https://github.com/LaChope/airport-sim-ui): The web-based user interface for the simulation.
* [**airport-sim-server**](https://github.com/LaChope/airport-sim-server/): The backend server that provides the simulation data.
* [**rstudio**](https://posit.co/products/open-source/rstudio/?sid=1): An RStudio environment for data analysis tasks.

---

## Getting Started

To get the application up and running, follow these simple steps.

### Prerequisites

* [Docker](https://www.docker.com/get-started)
* [Docker Compose](https://docs.docker.com/compose/install/)

### Installation and Configuration

1.  **Clone the repository:**
    ```sh
    git clone <your-new-repo-url>
    cd airport-sim-distribution
    ```
2.  **Configure the environment:**
    This repository includes template environment files. You will need to rename and customize them for your setup.
    * Rename `env.production.template` to `.env.production`
    * Rename `env.rstudio.template` to `.env.rstudio`

    Open each of these new `.env` files and fill in the required values. **Important:** In your `.env.production` file, you should set `VITE_AUTH_ENABLED` to `false` since authentication has been removed.

    *Example `.env.production`*:
    ```
    VITE_DATA_SOURCE=remote
    VITE_AUTH_ENABLED=false # Authentication is disabled
    VITE_API_URL=http://localhost:8000/generate-logs
    # ... other variables can be removed if they are auth-related
    ```
    *Example `.env.rstudio`*:
    ```
    PASSWORD=your_strong_password
    TZ=Europe/Prague
    ```

3.  **Run the application:**
    Use Docker Compose to start all the services in the background:
    ```sh
    docker-compose up -d
    ```

    The application will now be available at `http://localhost:8088` (or your configured port).