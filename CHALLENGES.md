# Challenges

Below are a series of challenges for the Hack. This assumes that you are 

## Challenge 0

Verify that you have all the pre-requisites installed and setup in your local machine:
- Azure CLI 2.0.64 or later
- Python 3.6.8 (or a later version in the 3.6.x series)
- Node.js 10.15.3 or later
- .NET CORE SDK 2.2
- Visual Studio Code 1.35.0 or later (our prefered IDE for the Hack)
- Git

Once you have these tools installed, clone the repository for the data generator code. This contains C# code implemented in .NET Core 2.2 that will generate the data streams necessary for our simulation of large data streams arriving at EventHubs and Blob Storage. It will also generate the reference data that will be stored in SQL database and blob storage.

## Challenge 1

- Create an SQL Database Instance that will be used to store the reference data as well as the final output data.
- Run the DDL and DML statements to create the tables and load the reference data into the SQL tables.
- Create a Cosmos DB database and collection that will be used to store the final output.
- Create a Storage Account that will be used to store reference data
- Create the Event Hub name space that will be used for the incoming data stream
- Create 3 input EventHubs called California, Florida and Washington.
- Create 4 output EventHubs called Texas, Alabama, Kansas and Virginia
- For each of the EventHubs, create a consumer group called stranalysis01

Verify that the resources have been created successfully

## Challenge 2

- Create a Stream Analytics Job that uses the Tumbling window to fetch how many unique patients we have every 15 seconds from the California Event Hub. Write the output to the Texas Event Hub. Include events that arrive at the beginning of the interval and exclude those that arrive at the end of each interval. Each output event should include the mailing address and number of beds in the hospital.
- Create a Stream Analytics Job that uses the Hopping window to fetch how many unique patients we have every 15 seconds with a hopping size of 5 minutes from the Washington Event Hub. Write the output to the Alabama Event Hub. Exclude events that arrive at the beginning of the interval and include those that arrive at the end of each interval. Each output event should include the mailing address and number of beds in the hospital.
- Create a Stream Analytics Job that uses the Sliding window to retreive the number of patients from the California Event Hub in the out-patient-unit grouped by gender for a 15 seconds window and update the view each time a patient enters or exits the window. Write the output to the Kansas Event Hub. Each output event should include the mailing address and number of beds in the hospital.
- Create a Stream Analytics Job that uses the Session Window function to retrieve the vitals of each patient from the Florida Event Hub given a 10 second timeout with a maximum duration of 15 seconds. Write the output to the Virgina Event Hub. Each output event should include the mailing address, date of birth, primary care doctor and emergency contact for each patient.
- Start all 4 stream analytics jobs.
- Run the data generator code to generate events for 100 rounds. You can define this in the Program.cs C# script.

## Challenge 3
- Create an entry point Azure function that gets triggered when events arrive at Texas Event Hub. 
- Create an entry point Azure function that gets triggered when events arrive at Alabama Event Hub. 
- Create an entry point Azure function that gets triggered when events arrive at Kansas Event Hub. 
- Create an entry point Azure function that gets triggered when events arrive at Virginia Event Hub. 
- Create an orchestrator function that will be called by the entry point functions
- Create activity functions that will enrich the patient or hospital metadata leveraging Azure Cognitive services (vision, text analysis). This function will extract metadata from images in the record and also analyze feedback as positive or negative using sentiment analysis.
- Create an activity function that will collect the final metadata and write it out to datastore (Cosmos DB or SQL Server). Data from each of the 4 output event hubs will go to a seperate SQL table or Cosmos DB collection.
- Run the data generator code to generate events for 100 rounds. You can define this in the Program.cs C# script.

## Challenge 4
- Deploy a Power BI instance
- Visualize the output streams coming out of the corresponding tables/collections for the 4 event hubs.
- Run the data generator code to generate events for 100 rounds. You can define this in the Program.cs C# script.

