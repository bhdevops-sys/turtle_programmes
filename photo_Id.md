### Sea Turtle Photo Identification Mobile App Documentation

#### Introduction

The Turtle Photo Identification Mobile App is designed to enable conservationists and researchers to log sea turtle details during underwater sightings using **AppSheet**
mobile app.
Data is stored in a **Microsoft SQL Azure** database, and visualized with **Power BI** to help establish effective conservation strategies.

---

#### Table of Contents

1. [Features](#features)
2. [Technology Stack](#technology-stack)
3. [Business Process](#business-process)
4. [User Guide](#user-guide)
5. [Data Structure](#data-structure)
6. [Reporting and Visualization](#reporting-and-visualization)
7. [Deployment](#deployment)

---

#### Features

- **Turtle Sightings Logging:** Capture details of turtle sightings, location, date, and species.
- **Photo Upload:** Easily upload and store images of individual turtles for identification.
- **Population Baseline Data:** Help establish a population baseline dataset for effective conservation actions.
- **Migration Tracking:** Facilitate the study of migration patterns and habitat use by sea turtles.
- **Data Analysis:** Access and analyze data regarding population structure and residency patterns.

---

#### Technology Stack

- **Frontend:** AppSheet
- **Backend:** Microsoft SQL Azure
- **Data Visualization:** Power BI

---

#### Business Process

The mobile app follows a structured business process to gather and analyze turtle population data effectively:

1. **User Login:** Users log into the AppSheet app to access the features and data entry forms.
  
2. **Data Entry:**
   - Users record details about turtle sightings, including:
     - Date and time of sighting
     - Location (GPS coordinates)
     - Species identification
     - Upload of identification photos

3. **Data Validation:** 
   - The app checks for mandatory fields and valid entries to ensure data integrity.
   - Incomplete or inaccurate entries are rectified by photo-id team.

4. **Data Storage:** 
   - Data securely stored in a **Microsoft SQL Azure** database, providing reliable access to records.

5. **Data Retrieval:** 
   - Users can access historical sighting data for reporting and research.

6. **Data Analysis:**
   - Integrated with **Power BI**, the app visualizes turtle population data and sighting frequency.
   - Provides insights for statistical modeling of protected area populations and inter-nesting periods.

---

#### User Guide

1. **Creating an Account:**
   - Download the app from your device's app store;Google play, App store.
   - Create an account using your email and set a password (link to app will be shared to this account by app creator).

2. **Navigating the Interface:**
   - Home Screen: Displays options for data entry, reports, and settings.
   - Data Entry: Select the type of observation you wish to log.

3. **Logging Data:**
   - Fill out the required fields and hit the 'Submit' button to save the information.

4. **Viewing Reports:**
   - Navigate to the reports section to visual analysis provided by Power BI.

---

#### Data Structure

##### Database Tables

| Table Name          | Description                                                |
|---------------------|------------------------------------------------------------|
| TurtleSighting     | Records details of turtle sightings including location, date, and species. |
| TurtlePhotos        | Stores uploaded images for identification purposes.       |
| Individual   | Contains data on different species of sea turtles,name and unique identifiers.       |

##### Entity-Relationship Diagram (ERD)

For a visual representation of the database structure, refer to the [Entity-Relationship Diagram (ERD)](https://github.com/bhdevops-sys/turtle_programmes/blob/main/ERD/photo_id.md).

---

#### Reporting and Visualization

Integration of the app with **Power BI** provides powerful visualization tools, allowing users to:

- Analyze turtle population trends over time.
- Visualize migration patterns on maps.
- Generate reports on the abundance and structure of local turtle populations.

---

#### Deployment

To deploy the app, follow these steps:

1. Configure your Microsoft SQL Azure database to accept connections.
2. Set up the AppSheet application, linking it to the database.
3. Test the application thoroughly to ensure all features function correctly.
4. Deploy the app for user access.


---

