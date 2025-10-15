<p>
    <img src="https://cdn.muni.cz/media/3232863/logo-tacr-starfos.png?mode=boxpad&center=0.5,0.5&rnd=132363578900000000&heightratio=0.5&width=270"/>
</p>

## TQ03000934 Project Distribution

This application was developed as part of the project [**Research on factors affecting airport traffic performance based on developed predictive model**](https://starfos.tacr.cz/en/projekty/TQ03000934?query=6qsaaac7ljwq). The aim of the project is to develop a predictive model that will increase the predictability of aircraft movements in the tactical phase of operations based on the traffic situation and the throughput of the airport movement area as well as the accuracy of aircraft departure time estimation. To achieve the maximum level of correspondence with the real system, the model will incorporate the essential decision processes affecting taxiing and aircraft handling (including air traffic control and aircraft crew decision making). By linking experts from the university and industry, with experience in airport operations, programming, and simulation analysis, and using real data, a prototype tool applicable to real airport operations will be developed.

### Services

This distribution includes the following services, orchestrated by [Docker Compose](https://docs.docker.com/compose/):

* [**airport-sim-ui**](https://github.com/LaChope/airport-sim-ui): The web-based user interface for the simulation.
* [**airport-sim-server**](https://github.com/LaChope/airport-sim-server/): The backend server that provides the simulation data.
* [**auth-server**](https://www.keycloak.org/): A Keycloak instance for user authentication and authorization.

<p align="center">
    <img src="https://raw.githubusercontent.com/LaChope/airport-sim-distribution/refs/heads/main/architecture.png"/>
</p>

---

## Getting Started

To get the application up and running, follow these simple steps.

### Prerequisites

* [Docker](https://www.docker.com/get-started)
* [Docker Compose](https://docs.docker.com/compose/install/)

### Installation and Deployment
1.  **Clone the repository:**
    ```sh
    git clone https://github.com/LaChope/airport-sim-distribution.git
    cd airport-sim-distribution
    ```
2.  **Choose your setup and run the application:**

    You can run the application with or without authentication.

    #### Option 1: Run with Authentication (Default)
    This setup requires a `.env` file to enable and configure authentication.

    1. Create a file named `.env` in the root directory.
    2. Add the following variables to the `.env` file. Replace the placeholder values with your actual domain information.

        ```env
        # Set to true to enable authentication
        VITE_AUTH_ENABLED=true

        # Set your public-facing domain name for Keycloak
        KC_HOSTNAME=your-domain.com

        # Set the full URL to your Keycloak service
        KC_HOSTNAME_URL=[https://your-domain.com/services/auth](https://your-domain.com/services/auth)
        ``
    3. Run the following command to start all services:
        ```sh
        docker-compose up -d

    #### Option 2: Run without Keycloak Authentication

    This command starts the UI and the server, with authentication disabled.
    ```sh
    docker-compose up -d airport-sim-ui airport-sim-server
    ```


3.  **Access the Application**

    The application will be available at `http://localhost:8088`

