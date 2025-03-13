# Transportation & Logistics Tracking

## 1. Introduction
In today's fast-paced supply chain industry, optimizing shipment efficiency, reducing delivery times, and enhancing operational visibility are critical for success. This project analyzes real-world transportation and logistics data to derive actionable insights that improve shipment operations and reduce delays.

## 2. Problem Statement
The logistics industry faces challenges such as shipment delays, inefficient routing, and supplier performance inconsistencies. This project aims to answer key business questions, including:
- What are the most common shipment routes and their average distances?
- Which routes experience the longest delivery times?
- When are peak booking and delivery times?
- What factors contribute to shipment delays?
- Which customers receive the most shipments, and do they experience delays?
- Which suppliers have the highest delays?
- What are the most frequently shipped materials, and do certain materials have longer delivery times?
- How can we optimize routes for better efficiency?

## 3. Skills Demonstrated
- **Data Analysis & Visualization**: Power BI for interactive dashboards.
- **DAX (Data Analysis Expressions)**: Advanced calculations for KPIs and Visualizations.
- **Data Transformation**: Cleaning and structuring raw data.
- **UI/UX** : 
- **Statistical Analysis**: Understanding delay patterns and trends.
- **Business Intelligence**: Translating data into actionable insights.

## 4. Data Sourcing
The dataset used in this project consists of shipment records, GPS tracking data, vehicle information, and transportation distances. It includes key fields such as:

- Booking Date
- Trip Start Date
- Planned ETA vs. Actual ETA
- Delay Status (On Time, Delayed, Early)
- Supplier & Customer Information
- Shipment Material Type

## 5. Data Transformation
Data preprocessing involved:
- Handling NULL and Inconsistent values in key columns (e.g., `Vehicle Type`, `Driver Mobile No, and More.`).

  - Example of handling a Null Value using `Replace Value`.

    ![Data Transform](data_transformation/replace_value.png)

  - Final Data Transformation using Power Query

    ![Data Transform](data_transformation/data_transform.png)

- Creating a `Delay Category`, `Delay Days`,and `Travel Category` Column to deepen the analysis."

  - Delay Category Column

    | DAX | Result |
    |----------|----------|
    | ![](data_transformation/delay_category_dax.svg) | ![](data_transformation/delay_categoory_column.png) |

  - Delay Days Column

    | DAX | Result |
    |----------|----------|
    | ![](data_transformation/delay_dax.svg) | ![](data_transformation/delay_column.png) |

  - Travel Category Column

    | DAX | Result |
    |----------|----------|
    | ![](data_transformation/travel_dax.svg) | ![](data_transformation/travel_column.png) |
    
- Calculating additional metrics like `Total Shipment Delayed`, `Avg Delay Days`, `Top GPS Providers with Delay`, `and More`.

    ![Data Transform](dax_measure/kpi_dax.svg)

## 6. Modeling
The data structure consists of **Primary Data** as the main fact table that records all shipment transactions.  


- In addition, **Order Shipment Table** is used as the basis for building the `CONCEPT` of **Shipment Tracking**, which enables in-depth analysis of the status of shipment journeys without any direct relationship between tables.

  - Create `Shipment Status` Column on a Fact Table `Primary Data`.

  
  | DAX | Result |
  |----------|----------|
  | ![](shipment_tracking_concept/concept_column.svg) | ![](shipment_tracking_concept/shipment_status_column.png) |

  - The `Order Shipment Table` value is taken from the Fact Table `Primary Data` by taking a unique value, then adding a new column with a value that is used to sort the process in shipment   tracking.

  ![](shipment_tracking_concept/shipment_table.png)

  - Dax used in visualization to Create Base Line using `Line Chart` Visualization.


  | DAX | Result |
  |----------|----------|
  | ![](shipment_tracking_concept/dax_Viz.svg) | ![](shipment_tracking_concept/viz_result.png) |

- For dynamic analysis, **TopN Par** is used, a parameter table that allows users to select the highest number of Total Shipments in the shipment analysis. These parameters help filter the data according to the user's needs.

  - Example of application for visualization of Material Shipment and Supplier Name

  | DAX | Result |
  |----------|----------|
  | ![](parameter/parameter_dax.svg) | ![](parameter/parameter_result.png) |

  -  Final Result

  ![](shipment_tracking_concept/result_shipment_tracking.png)

- The **no direct relationship between tables** approach utilizes **DAX Measures** for key metric calculation and dynamic filter creation to ensure accurate and flexible analysis.

![](data_modeling.png)

## 7. Analysis & Visualization
The dashboard consists of **three pages**, each focusing on different insights:

1. **Performance Overview**
   - Shipment trends by month.
   - KPI metrics: Total Shipments, Delay Percentage, and Punctuality Rate.
   - Supplier performance comparison.

2. **Shipment Delays Analysis**
   - Delay trends over time.
   - Distribution of delay days.
   - Delay breakdown by shipment category and supplier.

3. **Route & GPS Analysis**
   - Top delayed routes and average distance.
   - Shipment distribution map.
   - Impact of GPS providers on shipment delays.

## 8. Conclusion
- **Peak Shipment Delays**: Delays are highest for Far Distance and Short Distance categories.
- **Supplier Performance**: Certain suppliers like `Ekta Transport Company` and `Trans Cargo India` have significantly higher delays.
- **Material Delay Trends**: `Yoke & Pole Assy` has the longest average delay of 30 days.
- **Operational Inefficiencies**: GPS Consent Track accounts for 73.4% of delayed shipments.
- **Punctuality Challenges**: The overall punctuality rate is **only 41%**, indicating significant room for improvement.

## Actionable Recommendations
✅ **Improve Supplier Accountability**: Set stricter SLAs for suppliers with repeated delays.
✅ **Optimize High-Delay Routes**: Identify bottlenecks and improve route planning.
✅ **Enhance GPS Tracking**: Reduce dependency on GPS Consent Track.
✅ **Refine Booking & Dispatching Processes**: Reduce the gap between booking and trip start times.
✅ **Enhance Real-Time Monitoring**: Implement alerts for high-risk shipments.

This analysis provides valuable insights into shipment performance, supplier trends, and delay factors, enabling stakeholders to make data-driven decisions to improve logistics operations.

---

📌 **Author:** [Your Name]  
📆 **Date:** March 2025
