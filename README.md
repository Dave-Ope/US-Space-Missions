# US-Space-Missions

## Problem Statement

This dashboard is a report of the descriptive analysis done for the US space mission. It would help NASA to identify the areas of strength and weakness in details concerning all the outer space missions from 1957 to August 2022.

The datasets includes details on the location, date, and result of the launch, the company responsible, and the name, price, and status of the rocket used for the mission.

We want to find out the following:

- How have rocket launches trended across time? Has mission success rate increased?

- Which countries have had the most successful space missions? Has it always been that way?

- Which rocket has been used for the most space missions? Is it still active?

- Are there any patterns you can notice with the launch locations?

                                                                                                                                                        
### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset is a csv file.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 4 : It was observed that all columns have correct data types, except for columns "Price" which has a data type of text.
- Step 5 : The dropdown icon on column "Price" was first used to filter out the blank cells then converted to Integers. Further to that we multiplied the each cell in the column by a million as dataset brief states that prices were in millions dollars.
- Step 6 : Data is then loaded from power query. In the report view, under the view tab, theme was selected.
- Step 7 : Since the data contains dates, a data table was created for proper date reference and accurate data modelling. Sorting was done by month number. 

   ![Image 1](https://github.com/Dave-Ope/US-Space-Missions/assets/144362123/4c128440-4126-4921-8f15-71236f70223b)

  
  - Step 8 : For accuracy and efficiency, all measures to be used will be stored in a table
    
  - Step 9 : Line chart was added to determine the trends, on the x-axis 'years' from the Date table was used and on the y-axis 'Total Missions' was used, 'Total Missions' is a measure as created as below, then Mission status was used as the Legend colour demarkers
  
  ![Image 2](https://github.com/Dave-Ope/US-Space-Missions/assets/144362123/263a7a4d-251e-47b9-85e3-b47ef7ec406d)

- Step 10 : Three card visuals were added to the canvas, one representing Total missions, Successful Missions and Total cost of the missions taken.
      Using visual level filter from the filters pane, basic filtering was used & null values were unselected for consideration into average calculation.
      Although, by default, while calculating average, blank values are ignored.
  
  ![Image 3](https://github.com/Dave-Ope/US-Space-Missions/assets/144362123/1d977782-7edd-4a65-b4fd-31a0f9302dae)

- Step 11 : New measure was created to find total failed missions.

Following DAX expression was written for the same,
     
      Failed Missions = 
      
      CALCULATE(
          COUNT('US Space Missions'[Mission]), 'US Space Missions'[MissionStatus] = "Failure"
      )

- Step 12 : New measure was created to find total missions that failed partially.

Following DAX expression was written for the same
        
        Partial Failure Missions = 
        
        CALCULATE(
            COUNT('US Space Missions'[Mission]), 'US Space Missions'[MissionStatus] = "Partial Failure"
        )
        
- Step 13 : New measure was created to find total missions that failed pre launched.

Following DAX expression was written for the same
   
    Pre Launched failure Missions = 
    
    CALCULATE(
        COUNT('US Space Missions'[Mission]), 'US Space Missions'[MissionStatus] = "Prelauch Failure"
    )




- Step 14 : A bar chart was also added to the report design area representing each company and their successful missions. While creating this visual, new measure was created "Successful missions" using the following DAX measure

  Success Rate = DIVIDE( [Successful Missions], [Total Missions])

Snapshot of the generated visual below:


![Image 4](https://github.com/Dave-Ope/US-Space-Missions/assets/144362123/f7799e26-3180-4928-b9bd-1fc09682bdc5)

  
 - Step 15 : The report was then designed and formatted as below.
 
 
 # Report Snapshot (Power BI DESKTOP)
 
![Snapshot Dashboard)](https://github.com/Dave-Ope/US-Space-Missions/assets/144362123/3efd4aab-2b83-464d-a749-6a6fae141a55)

# Insights

A single page report was created on Power BI Desktop.

Following inferences can be drawn from the dashboard;

### [1] Total Number of Missions = 1,265 Missions

### [2] Total Number of Successful Missions = 1,197 Missions

### [3] Total Price of Missions = £162,304,450,000.00

### [4] Succesful Missions by companies

  Number of successful missions with CASC = 233

  Number of successful missions with SpaceX = 170

  Number of successful missions with NASA = 146

  Number of successful missions with Astra = 2

  Number of successful missions with CASIC = 1

  Number of successful missions with Khrunichev = 1

  Number of successful missions with ESA = 1

  Number of successful missions with GK LS = 1


           thus, the company with the highest succesful missions is CASC


Other insights can be seen in the dashboard.
