
# Project 1: SQL

Disaster! There has been a data breach @ SAGOber, a new Mobility cum Travel network across the World. 

Someone from inside(an Employee) leaked the rider algorithm to the World (Probably Black Market). 

Now, SAGOber has called upon Sam, an in-house Data Analyst & SQL expert to handle the situation. He is handed some raw and crude information about the data breach. 

The information handed to him is as follows:

    1.It was done on date 2020-06-23
    2.It's was inside job

Company's CEO, Pam Butters is getting paranoid & wants to cover every possible avenue to figure out who did this.
Sam has full access to the Employees & All the rides related Database to catch the culprit. 

As SAGOber Employees can travel for free with their platform & also it's an insider job,  Pam Butters thinks that the culprit may have used the platform to get around.

With what we know now, we should be able to deduce some information from the database. After gathering some insights, we got the following information:

    1.Date of incident: 2020-06-23
    2.Keiko Corp Longitude: -74.997 to -74.9968
    3.Keiko Corp Latitude: 40.5 to 40.6

With this information we should be able to figure out which rides happened that day around the office premises.
Pam has asked to find the vehicle and owner info linked to those rides without any duplicates records! Let's check the tables we're going to deal with!

![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/SQL%20Project/ScreenShots/Capdture.PNG)

Let's Check the Vehicle Location Histories Table

![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/SQL%20Project/ScreenShots/Capture1.PNG)

## Query 1: Getting Rider_id

```
CREATE VIEW suspected_rides AS 
SELECT * FROM vehicle_location_histories AS vlh WHERE
            city = 'new york' AND long BETWEEN 40.5 AND 40.6 AND lat BETWEEN -74.997 AND -74.9968  AND 
            vlh.timestamp::date =  '2020-06-23'::date
ORDER BY long;

```

![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/SQL%20Project/ScreenShots/Capture2.PNG)


We got 428 records from the above query which is quite extensive.
Now that we know which vehicles were linked to those rides we use their current location to go and interrogate them for more information!

All the work and the interrogation of the drivers has come up flat as dealing with 428 riders is no joke.
We'll go ahead and filter out all of the unique riders(passengers) that were on those suspected rides on that horrible day of heist.
Let's Create a VIEW(Stored Procedure) for our above query

![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/SQL%20Project/ScreenShots/Capture3.PNG)

## Query 2: Multijoin for Specific Drivers

```
SELECT DISTINCT r.vehicle_id, u.name AS "Owner",u.address, v.status, v.current_location
FROM suspected_rides AS sr
INNER JOIN rides AS r ON r.id = sr.ride_id
INNER JOIN vehicles AS v ON v.id = r.vehicle_id
INNER JOIN users AS u ON u.id = v.owner_id;

```
![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/SQL%20Project/ScreenShots/Capture4.PNG)

We have done it! Well not quite there yet. We have narrowed done to just 89 records from potentially thousands of possible records.
But after interrogating all drivers, nothing significant was found. When all the hope of catching the culprit was lost, Sam realized that SAGOber has all the info regarding the passengers as well. 
Maybe we could link the riders and passengers(users) to get unique values.


## Query 3: Multijoin drivers & passengers

```
SELECT DISTINCT r.vehicle_id, u.name AS "Rider Name",u.address
FROM suspected_rides AS sr
INNER JOIN rides AS r ON r.id = sr.ride_id
INNER JOIN users AS u ON u.id = r.rider_id;

```

![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/SQL%20Project/ScreenShots/Capture5.PNG)


We now have 109 records, far more than 89 records above. But the good news is we have link to find those passengers(users) now.

Suddenly, there was a breakthrough. An anonymous call that somebody from inside(employees) helped someone from outside was revealed. That means, minimum 2 people were involved in this heist.
Now, we need to split the names in passengers(users) table to first_name and last_name so that we can link to employees database.
Let's Check Users Table to find Passengers Details

![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/SQL%20Project/ScreenShots/Capture6.PNG)

## Query 4: Splitting passengers(users) name 

```
CREATE VIEW suspect_riders_name AS 
SELECT DISTINCT
                split_part( u.name, ' ', 1 ) AS "first_name",
                split_part( u.name, ' ', 2 ) AS "last_name"
FROM suspected_rides AS sr
INNER JOIN rides AS r ON r.id = sr.ride_id
INNER JOIN users AS u ON u.id  = r.rider_id; 

```

We have 103 records now which tells us that someone from these 103 people have done the heist. 
Now, we need to link the 103 passengers(users) names to the employees database.

![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/SQL%20Project/ScreenShots/Capture7.PNG)

## Query 5: Linking passengers(users) to Employees database 

```
SELECT DISTINCT 
                concat(t1.first_name,' ', t1.last_name) AS "Employees",
                concat(u.first_name,' ', u.last_name) AS "Riders"

FROM dblink('host=localhost user=postgres password=postgres dbname=employees',
            'select first_name, last_name from employees;')
            
AS t1(first_name NAME, last_name NAME)
JOIN suspect_riders_name AS u ON t1.last_name = u.last_name
ORDER BY "Riders";

```
![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/SQL%20Project/ScreenShots/Capture.PNG)

Hurray! We did it. We narrowed it down to just 11 suspects from potential thousands of records.

An interesting pattern was seen. The Employee and the Passenger had same last name. So they can be family members who conducted this heist.
After interrogation, it was revealed that it was employee Gino Peck and rider Jeanne Peck who did this. 

Reason for the data breach was that Gino is working since 1995 very little promotion activity and less salary raises. Gino got access to database somehow and handed that data to a family member Jeanne.

We solved the mystery. We retrieve the data and no data breach has taken place. 

![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/SQL%20Project/ScreenShots/Capfture.PNG)

## Installation for databases mentioned the project

```
Step1: Install Postgres and Valentina Studio

Step2: Inside Valentina Studio, click on Create databases:
        and create two databases: Employees and Vehicle_Riders

Step3: Open Cmd, type cd " filepath to where databases are located in local machine" -->
        C:\Program Files\PostgreSQL\12\bin\psql.exe --> drag & drop the .exe file into Cmd.

Step4: C:\Program Files\PostgreSQL\12\bin\psql.exe  AND continue with the following code:
        -U postgres -d "database name in Valentina Studio" < .sqlname you want to load. 

Step5: Continue the same steps for remaining databases

Step6: Open Valentina Studio --> LocalHost-->Open SQL Editor-->Click on postgres localhost & load the database

Step7: Run the above mentioned queries


```
    
 ### Feedback & Queries

If you have any feedback or Queries, please reach out to me at sakshemgotekar@gmail.com
