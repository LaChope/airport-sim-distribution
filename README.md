<p align="center">
    <img src="https://cdn.muni.cz/media/3232863/logo-tacr-starfos.png?mode=boxpad&center=0.5,0.5&rnd=132363578900000000&heightratio=0.5&width=270"/>
</p>

## TQ03000934 Project Distribution

This application was developed as part of the student project [**Research on factors affecting airport traffic performance based on developed predictive model**](https://starfos.tacr.cz/en/projekty/TQ03000934?query=6qsaaac7ljwq). The aim of the project is to develop a predictive model that will increase the predictability of aircraft movements in the tactical phase of operations based on the traffic situation and the throughput of the airport movement area as well as the accuracy of aircraft departure time estimation. To achieve the maximum level of correspondence with the real system, the model will incorporate the essential decision processes affecting taxiing and aircraft handling (including air traffic control and aircraft crew decision making). By linking experts from the university and industry, with experience in airport operations, programming, and simulation analysis, and using real data, a prototype tool applicable to real airport operations will be developed.

### Services

This distribution includes the following services, orchestrated by Docker Compose:

* [**airport-sim-ui**](https://github.com/LaChope/airport-sim-ui): The web-based user interface for the simulation.
* [**airport-sim-server**](https://github.com/LaChope/airport-sim-server/): The backend server that provides the simulation data.
* [**rstudio**](https://posit.co/products/open-source/rstudio/?sid=1): An RStudio environment for data analysis tasks.
* [**auth-server**](https://www.keycloak.org/): A Keycloak instance for user authentication and authorization.
---

## Getting Started

To get the application up and running, follow these simple steps.

### Prerequisites

* [Docker](https://www.docker.com/get-started)
* [Docker Compose](https://docs.docker.com/compose/install/)

### Installation and Configuration

Follow the instructions for the setup you wish to run.

---

### Option 1: Running with Keycloak Authentication

This setup enables user authentication through Keycloak.

1.  **Clone the repository:**
    ```sh
    git clone https://github.com/LaChope/airport-sim-distribution.git
    cd airport-sim-distribution
    ```
2.  **Configure the environment:**
    Rename and customize all three template files:
    * Rename `env.production.template` to `.env.production`
    * Rename `env.rstudio.template` to `.env.rstudio`
    * Rename `env.auth.production.template` to `.env.auth.production`

    In your new `.env.production` file, ensure **`VITE_AUTH_ENABLED` is set to `true`** and that the Keycloak variables point to your authentication server.

    *Example `.env.production`*:
    ```
    VITE_DATA_SOURCE=remote
    VITE_AUTH_ENABLED=true # Important: Set to true
    VITE_API_URL=http://localhost:8000/generate-logs
    VITE_KEYCLOAK_URL=http://localhost:9090/
    VITE_KEYCLOAK_REALM=airport-sim-realm
    VITE_KEYCLOAK_CLIENT_ID=airport-sim-ui-client
    ```
    In your `.env.auth.production`, set a strong password for the Keycloak admin.

3. **Set-up the keycloak client:** Follow the [Server Administration Guide](https://www.keycloak.org/docs/latest/server_admin/index.html) to set-up your keycloak instance.

3.  **Run the application:**
    Use Docker Compose to start all services.
    ```sh
    docker-compose up -d
    ```
    The application will be available at `http://localhost:8088`, and you will be prompted to log in.

---

### Option 2: Running without Authentication

This is the simplest setup and does not require Keycloak.

1.  **Clone the repository:**
    ```sh
    git clone <your-new-repo-url>
    cd airport-sim-distribution
    ```
2.  **Configure the environment:**
    Rename and customize the following template files:
    * Rename `env.production.template` to `.env.production`
    * Rename `env.rstudio.template` to `.env.rstudio`

    In your new `.env.production` file, **you must set `VITE_AUTH_ENABLED` to `false`**.

    *Example `.env.production`*:
    ```
    VITE_DATA_SOURCE=remote
    VITE_AUTH_ENABLED=false # Important: Set to false
    VITE_API_URL=http://localhost:8000/generate-logs
    ```

3.  **Run the application:**
    Use Docker Compose to start the required services.
    ```sh
    docker-compose up -d airport-sim-ui airport-sim-server rstudio
    ```
    The application will be available at `http://localhost:8088`.

