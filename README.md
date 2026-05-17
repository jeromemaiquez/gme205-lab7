# Project Title
GmE 205 - Laboratory Exercise 7

# How to set up the virtual environment
1. Create a folder on your computer and open it in your IDE (e.g., VS Code)
2. Open the terminal then create the virtual environment by running the following:
    ```
    py -m venv .venv
    .\.venv\Scripts\activate
    ```
3. Press ```Ctrl + Shift + P``` in VS Code, search for *Python: Select Interpreter*, then choose the interpreter inside the ```.venv``` folder
4. Install the required packages by running the following in the terminal:
    ```
    python -m pip install --upgrade pip
    pip install pandas matplotlib
    ```
5. (Recommended) List the installed packages via:
    ```
    pip freeze > requirements.txt
    ```

# How to run Python scripts

In the terminal, ensuring that ```(.venv)``` is present in the prompt, run the following:
    ```
    python <folder/script_name.py>
    ```

# Reflections
1. In this architecture, PostGIS serves mainly as the place storing the parcel and road data. By connecting to the database and running queries, we are able to extract this data for the app.
2. Flask is the framework with which we made the web app that serves the parcel and road data to an external client. We use Flask to define routes and URLS, define API endpoints, and build necessary functionality such as connecting to databases, running the queries, and converting the results to standard GeoJSON format.
3. GeoJSON is useful for spatial web services because it has emerged as the standard format for exchanging spatial data. A major driver behind this is its readability by both humans and machines, making them very easy to parse.
4. The `ST_AsGeoJSON()` function in PostGIS converts the geometries into GeoJSON format, which is the standard format for spatial data exchange over a network. As such, this conversion step supports a distributed GIS framework, where separate but connected machines share data and functionalities to act as a greater whole.
5. Even with its capabilities to connect to web-based services, QGIS is still a locally-installed desktop GIS software at its core. Its installation involves a long list of sub-programs and plugins, and its use requires a large amount of processing and memory. This is in comparison to lightweight web-mapping APIs, such as Leaflet, Mapbox, or MapLibre.
6. Using a REST API eliminates the need for manual data copying and sharing of shapefiles or other spatial data file formats. This allows for automated or even real-time data sharing, and mitigates the risk of human errors.
7. This laboratory demonstrated the creation of geospatial functions (such as querying PostGIS tables) as API endpoints. This allows clients on other machines connected to the web to access these functions and the data they return. This is the essence of distributed geospatial computing: functions and data not limited to one machine, but shared across multiple connected machines.
8. A service-based GIS architecture "decouples" mapping components, processing functions, and data storage into modularized and independent services connected over a network. This enables smoother spatial data sharing, more easily scalable processing, and better integration with existing systems via loose coupling.
9. Since processing functions and mapping components are modularized and shared over a network (and thus are not limited to a single machine), they can be hosted on dedicated servers or even the cloud to serve multiple clients. More traffic in the form of web requests and data responses can occur simultaneously, since the functions run independently from each other.