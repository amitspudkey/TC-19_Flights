# TC-19_Flights
 Tableau Conference 19 - Adding AI to your BI, C I can do it too!

Data and instructions for the conference session is located at https://www.kaggle.com/neelybd/tc19-adding-ai-to-your-bi.


# Below is the original lab instructions from the session.

# Adding AI to your BI, C I Can Do it Too!
## Hands-on with Keyence’s KI AI


Welcome @lab.User.FirstName. I hope you have fun and learn something neat.

This session is designed for novice level users.

If you have any questions, raise your hand and someone walking around will help you out.

#### Note: For every step, there is a backup file. Feel free at anytime to use it if you get lost or off track.

===

# Outline
1.  Understanding the original data
2.  Preparing the data using Tableau Prep
3.  Importing cleaned data into Tableau
4.  Creating a map
5.  Using AFE to add in Weather data
6.  Use AI to figure out what is important
7.  Create a full dashboard
8.  Whats your delay?

===

# Procedure
## Initial Steps
1. Login to the computer by selecting the password box and either clicking in or entering +++@lab.VirtualMachine(TC2019-DesktopPrep-Ki-R2).Password+++

2. Get familar with the orignal data

  - [] Flight Data: knowledge[Bureau of Transportation Statistics](https://transtats.bts.gov/Tables.asp?DB_ID=120&    DB_Name=Airline%20On-Time%20Performance%20Data&DB_Short_Name=On-Time)

  - [] Weather Data: knowledge[Iowa State University](https://mesonet.agron.iastate.edu/request/download.phtml?network=IL_ASOS)
  
  - [] Precipitation Data: knowledge[NOAA](https://www.ncdc.noaa.gov/cdo-web/datasets)

3.  From the Desktop
  - Open [TC 2019 Lab Files]
  - Open [2 - Tableau Pre]
  - Launch Flight Work Flow.tflx

4.  Run flow. 

===

# First Dashboard
## Import Data
5.  Open Tableau
  1.  Select the start menu
  2.  Type Tableau
  3.  Select Tableau 2019.2

6.  In File Explorer
  - Go to +++Type C:\Users\Labuser\Desktop\TC 2019 Lab Files\3 - Tableau Prep Results+++

7.  Import Data into Tableau
  - Drag the {Prepared Flight Data.csv} into Tableau

8.  Pivot Origin and Destination Airports
  - []  Click [Update Now]
  - []  Scroll to the far right
  - []  Holding [CTRL], select [Origin] and [Dest]
  - []  Right click the data header, Select [Pivot]
  - []  Click [Update Now]
  - []  Scroll to the far left
  - []  Right Click [Pivot Field Names] and select [Rename]
  - []  Type [Location]
  - []  Right Click [Pivot Field Values] and select [Rename]
  - []  Type [Airport]

9. Select [Abc] above [Airport] and change to Geographic Role - Airport

## Map

10.  Right click [Sheet 1], Rename to [Map], and open

11. Drag:
  1.  [Latitude (generated)] and [Longitude (generated)] to Canvas
  2.  [Flight Path] to Detail
  3.  [Airport] to Detail
  4.  [ArrDelay] to Color

12. Change Default Aggragation [ArrDelay]
  - Right Click [ArrDelay]
  - Select [Default Properties - Aggregation - Average]

13. Change Mark Type [O Automatic] to Line

14. Left click on Color
  1.  Edit Colors...
  2.  Palette -> Orange-Blue Diverging
  3.  Check Reversed 
  4.  Click Enter

## Congratulations, You made a simple map...
#### Now what?

===

# What's important for causing delays?

Is it the destination Airport?

What about the Airline?

Was it where the plane came from?

Time of day?

????????

## Too many questions, not enough answers...

## Let's next use an AI to figure out what is important...
and to add in some weather data.

===

# Meet Ki
He might seem a little absent minded today, his brain is being virtualized in a virtual machine.

### Preparing for the Date
15. Go to Desktop and select Ki

16. Enter +++admin+++ as the password.

17. Click the [Datasets] at the right.
  You are currently in the Projects Screen

18. Select the three datasets and Create Project

19. Name the project whatever you like

20. The AFE setting will autopopulate, set the following relationships
  !IMAGE[Ki Relationships.PNG](Ki Relationships.PNG)

>[!hint] If you click into the text box, you can type the name of the variable in the select box and it will filter the list.

>[!hint] Pay careful attention to the Arrival vs Depature. A plane departing needs to be paired with the Origin.

21. Click [Next]

22. Select [Minimize]

23. Select [ArrDelay] for drop down menu

24. Click [Next]

25. <font color=red> Don't Click </font>[Execute AFE]
  - This is because it will take 20 minutes to run.

### Getting to Know Each Other

26. Left click the [KI DATA ANALYTICS PLATFORM] at the top left.

27. Select [Tableau - Airport]

28. Select [Arrival Delay] at the Project Bar.

29. Look at the generated insights.
  - The list is order by which factor is the most impactful.
  - Top Insight says that how long a flight is matter the most.
  - Second insight is more interesting, flights going to Frisco is the most likely to be be delayed.
  - Also the IATA airline is a very large factor determining delays.

30. Find the insight: [Origin.Wind Direction_2]
  - Left click the insight
  - It says that when the wind direction is between 60<sup>o</sup> and 169<sup>o</sup>, the delays will be much larger.
  - This is heavily cross winded to runway 1L and 1R

### Exporting Our Dashboard
31. Left click [Workflow] near the top left.

32. Left click the right most bubble [Ki - AFE Output].

33. Click [Download] on the right.

===
# Return to Tableau
## Replace old dataset

34. Open the downloaded zip file at the bottom and save the csv to the desktop

>[!alert] If there was a problem with the output, go to +++C:\Users\Labuser\Desktop\TC 2019 Lab Files\6 - Ki AFE Export\+++ and use [Ki - AFE Output - Backup.csv]

35. Reopen the Prior Tableau Dashboard

36. Open [Data Source]

37. Replace Data Source
  - []  Select [Data - New Data Source]
  - []  Click [Text File] 
  - []  Select [Ki - AFE Output] from +++C:\Users\Labuser\Desktop\TC 2019 Lab Files\6 - Ki AFE Export "Ki - AFE Output"+++ 
  - []  Click Open
  - []  Click [Update Now]
  - []  Scroll to the far right
  - []  Holding [CTRL], select [Origin] and [Dest]
  - []  Right click the data header, Select [Pivot]
  - []  Click [Update Now]
  - []  Right Click [Pivot Field Names] and select [Rename]
  - []  Type [Location]
  - []  Right Click [Pivot Field Values] and select [Rename]
  - []  Type [Airport]
  - []  Select [Abc] above [Airport] and change to Geographic Role - Airport
  - []  Click Map
  - []  Go to [Data - Replace Data Source]
  - []  Current: [Prepared Flight Data] - Replacement: [Ki - AFE Output]

38. Change Default Aggragation [ArrDelay]
  - Right Click [ArrDelay]
  - Select [Default Properties - Aggregation - Average]


===

## New Graphs

#### Airline
39. Create Airline Bar Graph
  - Click [New Worksheet]
  - Right Click, Rename [Sheet 2] to Airline.
  - Drag [IATA Code Reporting Airline] to [Columns]
  - Drag [ArrDelay] to [Rows]
  - Drag [ArrDelay] to [Color]
  - Left click on Color
    1.  Edit Colors...
    2.  Palette -> Orange-Blue Diverging
    3.  Check Reversed 
    4.  Click Enter

>[!hint] The [New Worksheet] button is just to the right of [Map] at the bottom of the screen

===

## New Graphs

#### Wind
39. Create Airline Bar Graph
  - Click [New Worksheet]
  - Right Click, Rename [Sheet 3] to Wind Direction.
  - Drag [Origin.Wind Direction 2] to [Dimensions]
  - Drag [Origin.Wind Direction 2] to [Columns]
  - Drag [ArrDelay] to [Rows]
  - Drag [ArrDelay] to [Color]
  - Left click on Color
    1.  Edit Colors...
    2.  Palette -> Orange-Blue Diverging
    3.  Check Reversed 
    4.  Click Enter

===

## New Graphs

#### Flight Path
39. Create Airline Bar Graph
  - Click [New Worksheet]
  - Right Click, Rename [Sheet 3] to Flight Path.
  - Drag [Flight Path] to [Dimensions]
  - Drag [Flight Path] to [Rows]
  - Drag [ArrDelay] to [Column]
  - Drag [ArrDelay] to [Color]
  - Left click on Color
    1.  Edit Colors...
    2.  Palette -> Orange-Blue Diverging
    3.  Check Reversed 
    4.  Click Enter

===

## Full Dashboard

40. Click [New Dashboard]

>[!hint] The [New Dashboard] button is just to the right of [Map] at the bottom of the screen

41. Drag [Map] to Canvas
42. Delete the Arrival Delay Color.
43. Drag [Airline] to bottom of the [Map]
44. Drag [Wind Direction] to the right side of [Airline]
45. Drag [Flight Path] to the right side of the Canvas
46. Delete [Arrival Delay] container

>[!hint] To delete a container, click the container then click the X at the top right

## Simulator

47. Reopen Ki
48. Go to [Tableau - Airport]
49. Open ArrDelay_
50. Click Features (On the right)
51. Select 
  1.  [Dest.1HR Precepitation]
  2.  [CRSElapsed Time]
  3.  [Dest]
	3.  [IATA_CODE Reporting Airline]
	4.  [Distance]

52. Click [Simulation]

53. Input your flight information

54. Go to [https://info-analytics.keyence.com/tc19-flights](URL https://info-analytics.keyence.com/tc19-flights) and put in your delay.

55. Hope your connection time is enough...
