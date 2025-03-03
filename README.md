# CS-340 Project Two: Grazioso Salvare Dashboard

### Project Overview

This project involves developing a MongoDB-powered dashboard for Grazioso Salvare, an organization that identifies and trains rescue dogs. The dashboard allows users to:

- View and filter shelter dog data based on specific rescue types.

- Interact with a data table displaying dynamically filtered results.

- Visualize breed distributions through a pie chart.

- Display geolocation data on an interactive map.

The project follows the Model-View-Controller (MVC) pattern, using MongoDB as the database (model), Dash components as the view, and Python CRUD operations as the controller.

### Functionality

1. Interactive Filtering Options

Users can filter the data by selecting a rescue type:

- Water Rescue

- Mountain or Wilderness Rescue

- Disaster or Individual Tracking

- Reset (to show all dogs)

2. Data Table

- Displays shelter dog records.

- Dynamically updates based on the selected filter.

- Allows row selection for mapping.

3. Pie Chart (Breed Distribution)

- Displays only breeds with at least 1% representation.

- Breeds below 1% are grouped into 'Other'.

- Updates dynamically based on the filtered dataset.

4. Interactive Map

- Updates when a row is selected from the data table.

- Displays dog locations using latitude and longitude.

- Shows a marker and tooltip with the dog’s name and location.

### Tools Used

1. Dash Framework (View & Controller)

- Used for building the interactive web application.

- Components: dash, dash_core_components, dash_html_components, dash_table, dash_leaflet.

2. MongoDB (Model & Data Storage)

- Stores shelter dog data.

- Enables CRUD operations via a Python module.

- Allows filtering and querying of specific dog breeds and rescue types.

3. Plotly (Charts & Graphs)

- Used to create the dynamic pie chart displaying breed distributions.

4. Pandas (Data Manipulation)

- Converts MongoDB query results into structured data tables.

5. Waitress (Deployment)

- Used to serve the application efficiently.

### Setup Instructions

1. Install Dependencies

Run the following command to install all required packages:

```
pip install dash jupyter-dash dash-leaflet pandas plotly pymongo waitress
```

2. Connect to MongoDB

Ensure MongoDB is running and update your CRUD module with the correct credentials:

```
username = "aacuser"
password = "securepassword"
uri = "mongodb+srv://aacuser:securepassword@your-cluster.mongodb.net/your-database"
db = CRUD(uri, "AAC")
db.set_collection("animals")
```

3. Run the Dashboard

Execute the following command to start the app:

```
python ProjectTwoDashboard.py
```

Or, if using Jupyter Notebook:

```
app.run_server(mode='inline', debug=True)
```

Challenges & Solutions

1. Row Selection Not Updating the Map

- Issue: Clicking a row did not update the map.

- Solution: Ensured row_selectable="single" was enabled and used derived_virtual_selected_rows correctly.

2. Breeds with <1% Representation Crowding the Pie Chart

- Issue: Too many breeds made the chart unreadable.

- Solution: Grouped all breeds with less than 1% into an "Other" category.

3. MongoDB Connection Issues

- Issue: The NoneType error occurred when calling find().

- Solution: Ensured set_collection() was called before read().

Screenshots & Demonstration

![Starting State](Snip1.png)

![Selections](Snip2-1.PNG)

Resources & References

Dash Documentation

MongoDB Python Driver

Plotly Graphing Library

Python Pandas