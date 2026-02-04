### Turtle Programmes
Beyond helping with maintenance, updates, and troubleshooting in future, this documentation is a roadmap to help users understand the turtle program products, their purpose, and how they interactact with other components. 2 products are covered here:
 - **Nest monitoring mobile app**-photo_id_md
 - **Photo_ID mobile app**- turtle_nest_id
 - 
### Nest Mobile App

#### Introduction

Nesting Mobile App is designed to support nest patrol teams and researchers in monitoring and protecting sea turtle nests. This application captures various data points; turtle nest location, turtle interaction, nest relocation, false crawl, hatching, and excavation. Built on **AppSheet**, the app utilizes **Microsoft SQL Azure** for data storage and **Power BI** for data visualization.

---

#### Table of Contents

1. [Features](#features)
2. [Technology Stack](#technology-stack)
3. [Business Processes](#business-processes)
   - [Turtle Nest Information Process](#turtle-nest-information-process)
4. [User Guide](#user-guide)
5. [Data Structure](#data-structure)
6. [Reporting and Visualization](#reporting-and-visualization)
7. [Deployment](#deployment)

---

#### Features

- **Nest Capture:** Log the geographical coordinates of turtle nests.
- **Turtle Interaction:** Record data on turtle encounters during nesting.
- **Nest Relocation:** Manage and document the process of relocating nests for safety.
- **False Crawl Tracking:** Identify and record instances where turtles return to the sea without nesting.
- **Hatching and Excavation Data:** Monitor hatchlings, and document excavation of nests post-hatching.

---

#### Technology Stack

- **Frontend:** AppSheet
- **Backend:** Microsoft SQL Azure
- **Data Visualization:** Power BI

---

#### Business Processes

##### Turtle Nest Information Process

This process outlines how data is captured, stored, and utilized within the mobile app:

1. **Data Entry:** Users log into the AppSheet app to input data related to new nests, interactions, relocations, false crawls, hatching, and excavating.
  
2. **Data Validation:** The app employs validation rules to ensure input data is accurate and complete. Required fields include:
   - Nest location (Latitude, Longitude)
   - Date of observation
   - Type of observation (Nest, Interaction, Relocation, False Crawl, Hatching, Excavation)

3. **Data Storage:** Validated data is stored in a **Microsoft SQL Azure** database, enabling secure and reliable data management. 

4. **Data Retrieval:** Users can retrieve historical data through the app for reporting or further analysis.

5. **Data Analysis:** Power BI integrates with the SQL Azure database to visualize the data, providing insights into turtle behaviors, nesting success rates, and the effectiveness of conservation efforts.

---

#### User Guide

1. **Creating an Account:**
   - Download the app from your device's app store.
   - Create an account using your email and set a password.

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

| Table Name        | Description                                               |
|-------------------|-----------------------------------------------------------|
| TurtleNests       | Stores details of turtle nests including location and date. |
| TurtleInteractions | Records interactions with turtles during nesting activities. |
| NestRelocations    | Maintains information on nests that have been relocated.  |
| FalseCrawls       | Captures instances when turtles return without nesting.     |
| Hatching          | Logs data related to the hatching of turtle eggs.         |
| Excavations       | Documents the excavation process post-hatching.             |

---

#### Reporting and Visualization

The app's integration with **Power BI** allows users to visualize data through:

- Interactive dashboards displaying nest success rates.
- Charts illustrating turtle nesting timelines.
- Maps showing nest locations and false crawl paths.

---

#### Deployment

To deploy the app, follow these steps:

1. Configure your Microsoft SQL Azure database to accept connections.
2. Set up the AppSheet application, linking it to the database.
3. Test the application thoroughly to ensure all features function correctly.
4. Publish the app for user access.

---

