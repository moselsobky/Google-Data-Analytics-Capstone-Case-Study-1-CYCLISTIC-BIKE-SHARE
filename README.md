# Google-Data-Analytics-Capstone-Case-Study-1-CYCLISTIC-BIKE-SHARE
The business task you mentioned aims to investigate the differences between how casual and member riders use Cyclistic, with the goal of using this data to create a new marketing campaign to convert casual riders into annual members. 

For my first project, I used the R programming language to conduct my analysis.

---
  title: "Cycalitics_trips_2022"
author: "Mostafa_Elsobky"
date: "2023-07-20"
output:
  html_document: default
pdf_document: default
---


## R Markdown
I am using this R Markdown document to showcase my skills in analyzing, cleaning, and visualizing a data set containing 12 files, each representing a month of the year 2022 for the Cycalitics trip data. With the help of R packages such as dplyr and ggplot2, I will process the data and present the results in visually appealing plots and tables. My goal is to gain insights into the patterns and trends of the Cycalitics trip data for the year 2022.

When you click the **Knit** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. 

# # # # # # # # # # # # # # # # # # # # # # # 
# Install required packages
# tidyverse for data import and wrangling
# lubridate for date functions
# ggplot for visualization
# # # # # # # # # # # # # # # # # # # # # # # 

```{r installpackages}
install.packages("tidyverse")          #for data import and wrangling
install.packages("lubridate")          #for date functions
install.packages("ggplot2")             #for visualization

library(tidyverse)                     #helps wrangle data
library(lubridate)                     #helps wrangle date attributes
library(ggplot2)                       #helps visualize data
library(dplyr)                        #for data manipulation
getwd()                                #displays your working directory
setwd("C:/Users/Moselsobky/Documents/Cycalitic-Trips_2022.CSV") #sets your working (use your own username and your folder path ) directory to simplify calls to data
```

#=====================
# STEP 1: COLLECT DATA
#=====================
# Upload Divvy datasets (csv files) here
```{r upload datasets}
January_2022 <- read_csv("1.January_2022.csv")
February_2022 <- read_csv("2.February_2022.csv")
March_2022 <- read_csv("3.March_2022.csv")
April_2022 <- read_csv("4.April_2022.csv")
May_2022 <- read_csv("5.May_2022.csv")
June_2022 <- read_csv("6.June_2022.csv")
July_2022 <- read_csv("7.July_2022.csv")
August_2022 <- read_csv("8.August_2022.csv")
September_2022 <- read_csv("9.September_2022.csv")
October_2022 <- read_csv("10.October_2022.csv")
November_2022 <- read_csv("11.November_2022.csv")
December_2022 <- read_csv("12.December_2022.csv")
```
#====================================================
# STEP 2: WRANGLE DATA AND COMBINE INTO A SINGLE FILE
#====================================================
# Compare column names each of the files
# While the names don't have to be in the same order, they DO need to match perfectly before we can use a command to join them into one file
# Rename columns  to make them consistent

```{r combine data into a single file }
January_2022 <- rename(January_2022
                       ,trip_id = ride_id
                       ,bike_type = rideable_type 
                       ,start_time = started_at  
                       ,end_time = ended_at  
                       ,from_station_name = start_station_name 
                       ,from_station_id = start_station_id 
                       ,to_station_name = end_station_name 
                       ,to_station_id = end_station_id 
                       ,user_type = member_casual
                       ,start_lat = start_lat
                       ,start_lng = start_lng)

February_2022 <- rename(February_2022
                       ,trip_id = ride_id
                       ,bike_type = rideable_type 
                       ,start_time = started_at  
                       ,end_time = ended_at  
                       ,from_station_name = start_station_name 
                       ,from_station_id = start_station_id 
                       ,to_station_name = end_station_name 
                       ,to_station_id = end_station_id 
                       ,user_type = member_casual
                       ,start_lat = start_lat
                       ,start_lng = start_lng)


March_2022 <- rename(March_2022
                        ,trip_id = ride_id
                        ,bike_type = rideable_type 
                        ,start_time = started_at  
                        ,end_time = ended_at  
                        ,from_station_name = start_station_name 
                        ,from_station_id = start_station_id 
                        ,to_station_name = end_station_name 
                        ,to_station_id = end_station_id 
                        ,user_type = member_casual
                        ,start_lat = start_lat
                        ,start_lng = start_lng)

April_2022 <- rename(April_2022
                     ,trip_id = ride_id
                     ,bike_type = rideable_type 
                     ,start_time = started_at  
                     ,end_time = ended_at  
                     ,from_station_name = start_station_name 
                     ,from_station_id = start_station_id 
                     ,to_station_name = end_station_name 
                     ,to_station_id = end_station_id 
                     ,user_type = member_casual
                     ,start_lat = start_lat
                     ,start_lng = start_lng)

May_2022 <- rename(May_2022
                     ,trip_id = ride_id
                     ,bike_type = rideable_type 
                     ,start_time = started_at  
                     ,end_time = ended_at  
                     ,from_station_name = start_station_name 
                     ,from_station_id = start_station_id 
                     ,to_station_name = end_station_name 
                     ,to_station_id = end_station_id 
                     ,user_type = member_casual
                     ,start_lat = start_lat
                     ,start_lng = start_lng)
  

June_2022 <- rename(June_2022
                   ,trip_id = ride_id
                   ,bike_type = rideable_type 
                   ,start_time = started_at  
                   ,end_time = ended_at  
                   ,from_station_name = start_station_name 
                   ,from_station_id = start_station_id 
                   ,to_station_name = end_station_name 
                   ,to_station_id = end_station_id 
                   ,user_type = member_casual
                   ,start_lat = start_lat
                   ,start_lng = start_lng)

July_2022 <- rename(July_2022
                    ,trip_id = ride_id
                    ,bike_type = rideable_type 
                    ,start_time = started_at  
                    ,end_time = ended_at  
                    ,from_station_name = start_station_name 
                    ,from_station_id = start_station_id 
                    ,to_station_name = end_station_name 
                    ,to_station_id = end_station_id 
                    ,user_type = member_casual
                    ,start_lat = start_lat
                    ,start_lng = start_lng)

August_2022 <- rename(August_2022
                    ,trip_id = ride_id
                    ,bike_type = rideable_type 
                    ,start_time = started_at  
                    ,end_time = ended_at  
                    ,from_station_name = start_station_name 
                    ,from_station_id = start_station_id 
                    ,to_station_name = end_station_name 
                    ,to_station_id = end_station_id 
                    ,user_type = member_casual
                    ,start_lat = start_lat
                    ,start_lng = start_lng)

September_2022 <- rename(September_2022
                      ,trip_id = ride_id
                      ,bike_type = rideable_type 
                      ,start_time = started_at  
                      ,end_time = ended_at  
                      ,from_station_name = start_station_name 
                      ,from_station_id = start_station_id 
                      ,to_station_name = end_station_name 
                      ,to_station_id = end_station_id 
                      ,user_type = member_casual
                      ,start_lat = start_lat
                      ,start_lng = start_lng)

October_2022 <- rename(October_2022
                         ,trip_id = ride_id
                         ,bike_type = rideable_type 
                         ,start_time = started_at  
                         ,end_time = ended_at  
                         ,from_station_name = start_station_name 
                         ,from_station_id = start_station_id 
                         ,to_station_name = end_station_name 
                         ,to_station_id = end_station_id 
                         ,user_type = member_casual
                         ,start_lat = start_lat
                         ,start_lng = start_lng)

November_2022 <- rename(November_2022
                       ,trip_id = ride_id
                       ,bike_type = rideable_type 
                       ,start_time = started_at  
                       ,end_time = ended_at  
                       ,from_station_name = start_station_name 
                       ,from_station_id = start_station_id 
                       ,to_station_name = end_station_name 
                       ,to_station_id = end_station_id 
                       ,user_type = member_casual
                       ,start_lat = start_lat
                       ,start_lng = start_lng)

December_2022 <- rename(December_2022
                        ,trip_id = ride_id
                        ,bike_type = rideable_type 
                        ,start_time = started_at  
                        ,end_time = ended_at  
                        ,from_station_name = start_station_name 
                        ,from_station_id = start_station_id 
                        ,to_station_name = end_station_name 
                        ,to_station_id = end_station_id 
                        ,user_type = member_casual
                        ,start_lat = start_lat
                        ,start_lng = start_lng)


```

# Inspect the dataframes and look for incongruencies

```{r check data frame}
str(January_2022)
str(February_2022)
str(March_2022)
str(April_2022)
str(May_2022)
str(June_2022)
str(July_2022)
str(August_2022)
str(September_2022)
str(October_2022)
str(November_2022)
str(December_2022)
```
# Convert ride_id and rideable_type to character so that they can stack correctly

```{r conver some columns to character}
January_2022 <-  mutate(January_2022, trip_id = as.character(trip_id)
                        ,bike_type = as.character(bike_type)) 
February_2022 <-  mutate(February_2022, trip_id = as.character(trip_id)
                         ,bike_type = as.character(bike_type)) 
March_2022 <-  mutate(March_2022, trip_id = as.character(trip_id)
                      ,bike_type = as.character(bike_type)) 
April_2022 <-  mutate(April_2022, trip_id = as.character(trip_id)
                      ,bike_type = as.character(bike_type)) 
May_2022 <-  mutate(May_2022, trip_id = as.character(trip_id)
                    ,bike_type = as.character(bike_type)) 
June_2022 <-  mutate(June_2022, trip_id = as.character(trip_id)
                     ,bike_type = as.character(bike_type)) 
July_2022 <-  mutate(July_2022, trip_id = as.character(trip_id)
                     ,bike_type = as.character(bike_type)) 
August_2022 <-  mutate(August_2022, trip_id = as.character(trip_id)
                       ,bike_type = as.character(bike_type)) 
September_2022 <-  mutate(September_2022, trip_id = as.character(trip_id)
                          ,bike_type = as.character(bike_type)) 
October_2022 <-  mutate(October_2022, trip_id = as.character(trip_id)
                        ,bike_type = as.character(bike_type)) 
November_2022 <-  mutate(November_2022, trip_id = as.character(trip_id)
                         ,bike_type = as.character(bike_type)) 
December_2022 <-  mutate(December_2022, trip_id = as.character(trip_id)
                         ,bike_type = as.character(bike_type)) 
```

# Stack individual quarter's data frames into one big data frame

```{r combine all data frames in one big data frame}
all_trips <- bind_rows(January_2022, February_2022, March_2022,   April_2022,May_2022,June_2022,July_2022,August_2022,September_2022,October_2022,November_2022,December_2022)
```

#======================================================
# STEP 3: CLEAN UP AND ADD DATA TO PREPARE FOR ANALYSIS
#======================================================

# Inspect the new table that has been created
```{r inspect the new table}
colnames(all_trips)  #List of column names
nrow(all_trips)  #How many rows are in data frame?  
dim(all_trips)  #Dimensions of the data frame?      
head(all_trips)  #See the first 6 rows of data frame.  Also tail(all_trips)
str(all_trips)  #See list of columns and data types (numeric, character, etc)
summary(all_trips)  #Statistical summary of data. Mainly for numeric
```
# There are a few problems we will need to fix:

# (1) The data can only be aggregated at the ride-level, which is too granular. We will want to add some additional columns of data -- such as day, month -- that provide additional opportunities to aggregate the data.

# (2) We will want to add a calculated field for length of ride  to the entire dataframe for consistency.

# (3) There are some rides where tripduration shows up as negative, including several hundred rides where Divvy took bikes out of circulation for Quality Control reasons. We will want to delete these rides.

# Check to make sure the proper number of observations were reassigned
```{r check the number of observation in column member_casual}
table(all_trips$user_type)
```

# Add columns that list the date, month and day, of each ride.
# This will allow us to aggregate ride data for each month or day ... before completing these operations we could only aggregate at the ride level
```{r adding new columns to represent the day, day_of_week and month}
all_trips$date <- as.Date(all_trips$start_time) #The default format is yyyy-mm-dd
all_trips$month <- format(as.Date(all_trips$date), "%B")
all_trips$day <- format(as.Date(all_trips$date), "%d")
all_trips$year <- format(as.Date(all_trips$date), "%Y")
all_trips$day_of_week <- format(as.Date(all_trips$date), "%A")
```
# Calculate ride length in minutes

```{r calcualte ride_length_in_minutes}
all_trips$ride_length <- difftime(all_trips$end_time, all_trips$start_time, units = "mins")
```
# Inspect the structure of the columns
```{r chech the new columns structure}
str(all_trips)
```
# Convert "ride_length" from Factor to numeric so we can run calculations on the data
```{r convert from factor to numeric}
is.factor(all_trips$ride_length)
all_trips$ride_length <- as.numeric(as.character(all_trips$ride_length))
is.numeric(all_trips$ride_length)
```
```

#=====================================
# STEP 4: CONDUCT DESCRIPTIVE ANALYSIS
#=====================================

# Descriptive analysis on ride_length (all figures in minutes)


```{r statistical calculations}
library(dplyr)

all_trips_v2 <- all_trips %>%
  mutate(
    mean_ride_length = mean(ride_length), #straight average (total ride length / rides)
    median_ride_length = median(ride_length),#midpoint number in the ascending array of ride lengths
    max_ride_length = max(ride_length),#longest ride
    min_ride_length = min(ride_length) #shortest ride
  )
summary(all_trips_v2$ride_length)

```



# You can condense the four lines above to one line using summary() on the specific attribute

```{r check the summary of the new dataset}
summary(all_trips_v2$ride_length)
```
# Compare members and casual users

```{r compare members and casula users}
aggregate(all_trips_v2$ride_length ~ all_trips_v2$user_type, FUN = mean)
aggregate(all_trips_v2$ride_length ~ all_trips_v2$user_type, FUN = median)
aggregate(all_trips_v2$ride_length ~ all_trips_v2$user_type, FUN = max)
aggregate(all_trips_v2$ride_length ~ all_trips_v2$user_type, FUN = min)
```
# See the average ride time by each day for members vs casual users
```{r average ride length by member and casual users Vs day}
aggregate(all_trips_v2$ride_length ~ all_trips_v2$user_type + all_trips_v2$day_of_week, FUN = mean)
```
# Notice that the days of the week are out of order. Let's fix that.

```{r order by day of week}
all_trips_v2$day_of_week <- ordered(all_trips_v2$day_of_week, levels=c("Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"))
```
# Now, let's run the average ride time by each day for members vs casual users

```{r average ride length by member and casual users Vs day order by day of week}
aggregate(all_trips_v2$ride_length ~ all_trips_v2$user_type + all_trips_v2$day_of_week, FUN = mean)

```
# analyze ridership data by type and weekday

```{r analyzing ridership}
all_trips_v2 %>% 
  mutate(weekday = wday(start_time, label = TRUE)) %>%  #creates weekday field using wday()
  group_by(user_type, weekday) %>%  #groups by user type and weekday
  summarise(number_of_rides = n()							#calculates the number of rides and average duration 
            ,average_duration = mean(ride_length)) %>% 		# calculates the average duration
  arrange(user_type, weekday)								# sorts
```
# Let's visualize the number of rides by rider type
```{r viz number of rides by rider type}
all_trips_v2 %>% 
  mutate(weekday = wday(start_time, label = TRUE)) %>% 
  group_by(user_type, weekday) %>% 
  summarise(number_of_rides = n()
            ,average_duration = mean(ride_length)) %>% 
  arrange(user_type, weekday)  %>% 
  ggplot(aes(x = weekday, y = number_of_rides, fill = user_type)) +
  geom_col(position = "dodge")
```


# Let's create a visualization for average duration
```{r viz for average duration}
all_trips_v2 %>% 
  mutate(weekday = wday(start_time, label = TRUE)) %>% 
  group_by(user_type, weekday) %>% 
  summarise(number_of_rides = n()
            ,average_duration = mean(ride_length)) %>% 
  arrange(user_type, weekday)  %>% 
  ggplot(aes(x = weekday, y = average_duration, fill = user_type)) +
  geom_col(position = "dodge")
```


#viz month and casual&member riders according to average ride length and number of rides 
all_trips_v2 %>%
  mutate(month = month(start_time, label = TRUE)) %>%
  group_by(user_type, month) %>%
  summarise(number_of_rides = n(),
            average_duration = mean(ride_length)) %>%
  ggplot(aes(x = month, y = number_of_rides, fill = user_type)) +
  geom_col(position = "dodge") +
  scale_y_continuous(sec.axis = sec_axis(~ . / max(all_trips_v2$ride_length) * max(all_trips_v2$number_of_rides), name = "Average Duration")) +
  geom_line(aes(y = average_duration / max(all_trips_v2$ride_length) * max(all_trips_v2$number_of_rides), group = user_type), size = 1, color = "black") +
  geom_point(aes(y = average_duration / max(all_trips_v2$ride_length) * max(all_trips_v2$number_of_rides)), size = 3, color = "black")




#=================================================
# STEP 5: EXPORT SUMMARY FILE FOR FURTHER ANALYSIS
#=================================================

# Create a csv file that we will visualize in Excel, Tableau, or presentation software

```{r exportinga csv file for future use}
counts <- aggregate(all_trips_v2$ride_length ~ all_trips_v2$user_type + all_trips_v2$day_of_week + all_trips_v2$start_lat + all_trips_v2$start_lng , FUN = mean)
write.csv(counts, file = "C:/Users/Moselsobky/Desktop/alltrips_v2_2022.csv")
```
# Congratulations!

```


