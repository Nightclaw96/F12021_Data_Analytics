# F12021_Data_Analytics
An end to end solution to extract, manage, analyze and visualize publicly available data about the 2021 Formula 1 season

Final Data Visualization available here (https://public.tableau.com/views/2021Dashboard_16587232200670/2021Dashboard?:language=en-US&:display_count=n&:origin=viz_share_link)

Introduction:
This project is built by Vishal Kamalakannan from the University of Michigan Industrial and Operations Engineering program.
The primary goal of this project is to display the impact of strategic decisions made by the F1 teams during each race in the 2021 season.
The velocity of each car depends on the age of it's tyres. The older the tyre gets, the more worn out it becomes leading
to a loss in traction which reflects in the race pace.
To get the full picture of a race, one needs to understand the time taken by each driver to complete each lap.
Additionally, one also needs to understand which tyre was used and for how long by each driver to understand the impact of pitstops during the race.

Data Collection:
The first step of this project is to collect the data required.
The data about individual laptimes are taken from the Ergast database (http://ergast.com/mrd/)
The data about the participating drivers, teams and their nationalities were taken from Wikipedia (https://en.wikipedia.org/wiki/2021_Formula_One_World_Championship)
The data about the layout of each circuit is taken from the F1 website (https://www.formula1.com/en/racing/2021.html)
The data about the tyre strategies used by each driver is taken from the (https://www.racefans.net/2021-f1-season/2021-f1-statistics/)

Data ETL (Extract/ Transform/ Load):
Jupyter notebooks have been used to run python scripts to convert each dataset into an appropriately transformed csv file ready for import.
Data Management:
To manage the volume and dimensions of the data a normalised SQL server has been designed to store the data.
This also allows the data to be scaled up with statistics from other years should the need arise in the future.
The MySQL server used for this project is in the AWS environment.

Data Analytics (Track position per lap):
The track position at the end of each lap for each driver is estimated as a T-statistic based on the time taken by each driver to complete every lap.
For eg., in race 3 for lap 40, the time taken by each driver to finish that lap is calculated by adding up the laptimes of each driver upto lap 40.
Based on the time taken by all 20 drivers, a Student's T statistic is evaluated for each driver and that is considered to be a proxy for the track position at lap 40.
The above step is repeated for each lap of every race.
This measure gives a uniform way to visualize the track position of each driver at the end of each lap of every race.
The analytics is done using Jupyter Notebooks in python

Data Analytics (Average Race Pace):
The pitstop time for each driver during the lap(s) when he pitted is subtracted from his corresponding laptime.
The race pace is calculated based on this measure of time and the average is calculated for each driver throughout the race.
The average race pace is plotted along with the number of pitstops in the same graph as the total number of points secured
to give a picture of the performance of the driver v/s the final result.
The analytics is done using Jupyter Notebooks in python

Data Visualization:
The race selection is presented through a global map.
The race highlights is presented as a plot of the T-statistic for each lap in a moving line graph
The average race pace and the points secured are presented as two separate bar graphs for each driver.
The data visualization is available here (https://public.tableau.com/views/2021Dashboard_16587232200670/2021Dashboard?:language=en-US&:display_count=n&:origin=viz_share_link)
