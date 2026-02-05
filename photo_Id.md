### Turtle Photo Identification Mobile App Documentation

#### Introduction

The Turtle Photo Identification Mobile App is designed to enable conservationists and researchers to identify sea turtles during underwater sightings.
Using **AppSheet**, this app captures critical data related to underwater turtle sightings, contributing to the study and conservation of various sea turtle species.
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

- **Turtle Sightings Logging:** Capture details of turtle sightings, including location, date, and species.
- **Photo Upload:** Easily upload and store images of individual turtles for identification.
- **Population Baseline Data:** Help establish a population baseline dataset for effective conservation actions.
- **Migration Tracking:** Facilitate the study of migration patterns and habitat use of sea turtles.
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
   - The app checks for required fields and valid entries to ensure data integrity.
   - Users receive feedback on incomplete or inaccurate entries.

4. **Data Storage:** 
   - Validated data is securely stored in a **Microsoft SQL Azure** database, providing reliable access to records.

5. **Data Retrieval:** 
   - Users can access historical sighting data for reporting and further research.

6. **Data Analysis:**
   - Integrated with **Power BI**, the app visualizes turtle population data, migration patterns, and sighting frequency.
   - Provides insights for statistical modeling of reef populations and inter-nesting periods.

---

#### User Guide

1. **Creating an Account:**
   - Download the app from your device’s app store.
   - Sign up using your email and create a password.

2. **Navigating the Interface:**
   - **Home Screen:** Provides options for data entry, visual reports, and user settings.
   - **Data Entry:** Select the “Log Sighting” option to input turtle data.

3. **Logging Data:**
   - Fill in required fields: Date, Location, Species, and upload the photo.
   - Submit the form to save your entry.

4. **Viewing Reports:**
   - Access the reports section for visual analytics created by Power BI.

---

#### Data Structure

##### Database Tables

| Table Name          | Description                                                |
|---------------------|------------------------------------------------------------|
| TurtleSightings     | Records details of turtle sightings including location, date, and species. |
| TurtlePhotos        | Stores uploaded images for identification purposes.       |
| SpeciesInformation   | Contains data on different species of sea turtles.       |
| MigrationPatterns    | Maintains records on turtle migration and habitat use.   |

##### Entity-Relationship Diagram (ERD)

For a visual representation of the database structure, refer to the [Entity-Relationship Diagram (ERD)](https://github.com/bhdevops-sys/turtle_programmes/blob/main/ERD/photo_id.md).

---

#### Reporting and Visualization

The app’s integration with **Power BI** provides powerful visualization tools, allowing users to:

- Analyze turtle population trends over time.
- Visualize migration routes and patterns on maps.
- Generate reports on the stability and structure of local turtle populations.

---

#### Deployment

To deploy the Turtle Photo Identification Mobile App, follow these steps:

1. Configure your SQL Azure database to accept incoming data.
2. Set up the AppSheet application, linking it to the database securely.
3. Conduct thorough testing to ensure all functionalities are operating as intended.
4. Publish the app for user access.

---

