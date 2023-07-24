# PLP-Power-Hacks

# Ojan-Energy
## Introduction
In this project, we are developing an energy management system that will enable real-time monitoring of energy consumption within industrial facilities. It can further be scaled to commercial and residential facilities. This will provide business owners, building owners and facility managers with a centralized visibility into the energy consumption patterns which can be analysed to increase efficiency and cut down their energy costs by 10-20%. It will also provide asset health data that will enable predictive maintenance through automated alerts to avoid future equipment breakdown and sudden power cuts again saving them on costs. Overall this will improve the facilities’ electrical health and safety.

## Approach
Using the data collected from the sensors, we made predictions for the next possible failure date using the LSTM Model. This was compared with the actual failure date.

This notebook contains the predictive part of the project for an industry use case. A further visual of the final system after deployment can be seen in the [figma prototype](https://www.figma.com/proto/QpJJ4OQr0ApL1ooixlugsR/Ojan-Energy?type=design&node-id=158-7&t=et6yNNh4ssNhZtWE-1&scaling=min-zoom&page-id=0%3A1&starting-point-node-id=158%3A7&mode=design).

The figma also shows an idea of how the system will work to provide centralized visibility and allow remote monitoring despite different locations.
    
As you hover through the figma prototype you will find the sign-up and login pages
* Home tab- A summary of what the company does and tabs to navigate to specific areas in the system
* Projects- A client industry with different locations and the overall performance and asset health in their specific locations
* Analytics- A visual of the electricity consumption breakdown through charts and graphs
* Dashboard- A dashboard with more detail on the analysis and asset health

## Background: problem description and approach
### Problem

High energy consumption within facilities resulting in high operations costs.
Lack of visibility in asset health leads to unpredicted equipment breakdown.
Electrical damages or cut-offs caused by low power factors or current imbalances.
### Solution

Cost Reduction- A centralized energy management system that provides visibility into the facilities' energy consumption patterns.
Predictive Maintenance- A real-time monitoring system that provides visibility into the asset health.
Improved Electrical Health and Safety- Automated alerts in cases of low power factors or current imbalances
The solution can be scaled to residential and commercial facilities. In addition, it can further be developed and integrated into existing grids such that the problem of current imbalances can be addressed from the grid. This will help curb the problem of sudden power cuts as they will be predicted and handled before happening.

## Data Understanding
For this project, we will make use of the Microsoft Azure DataSet that can be used for predictive maintenance. The data consists of:

Machine conditions and usage: The operating conditions of a machine e.g. data collected from sensors.
Failure history: The failure history of a machine or component within the machine.
Maintenance history: The repair history of a machine, e.g. error codes, previous maintenance activities or component replacements.
Machine features: The features of a machine, e.g. engine size, make and model, location.
Details

### The dataset consists of 5 CSV files:

Telemetry Time Series Data (PdM_telemetry.csv): It consists of an hourly average of voltage, rotation, pressure, and vibration collected from 100 machines for the year 2015.

Error (PdM_errors.csv): These are errors encountered by the machines while in operating condition. Since these errors don't shut down the machines, these are not considered failures. The error date and times are rounded to the closest hour since the telemetry data is collected at an hourly rate.

Maintenance (PdM_maint.csv): If a component of a machine is replaced, that is captured as a record in this table. Components are replaced under two situations: 1. During the regularly scheduled visit, the technician replaced it (Proactive Maintenance) 2. A component breaks down and then the technician does an unscheduled maintenance to replace the component (Reactive Maintenance). This is considered as a failure and corresponding data is captured under Failures. Maintenance data has both 2014 and 2015 records. This data is rounded to the closest hour since the telemetry data is collected at an hourly rate.

Failures (PdM_failures.csv): Each record represents replacement of a component due to failure. This data is a subset of Maintenance data. This data is rounded to the closest hour since the telemetry data is collected at an hourly rate.

Metadata of Machines (PdM_Machines.csv): Model type & age of the Machines.

## Exploratory Data Analysis and Data Preparation
Further analysis was done on the datasets and a summary was given for each. The data was prepared for modeling by one-hot encoding and normalizing select features.

## Modeling and Evaluation
We made use of the Long Short-Term Memory (LSTM) Model. LSTM provides multivariate time series forecasting to predict the future machine breakdown which could be used to improve efficiency and increase the remaining useful life (RUL) of the machines.
The model can predict the sensor reading in case of a machine failure. The difference between the predicted date of failure and the actual failure date is a testing error of 0.03 which can further be improved by hyper tuning our model. In our case, we have used static data and we have made the predictions for one machine.

## Conclusion
From the model above we can conclude that it is possible to predict a machine failure before actual breakdown. By using IoT, the sensor data can be collected in real-time and we can make real-time predictions for many machines instead of one machine.

This will enable facility managers, electrical engineers, and technicians to look into breakdowns before they occur hence saving them on down-time costs. The project is a work in progress that we intend to work on up to deployment. The solution can be scaled to commercial and industrial facilities.



