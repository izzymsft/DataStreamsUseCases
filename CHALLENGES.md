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

- Create an SQL Database Instance that will be used to store the reference data
- Create a Storage Account that will be used to store reference data
- Create a Storage Account that will be used to store the incoming data stream
- Create the Event Hub name space that will be used for the incoming data stream
- Create 3 input EventHubs called California, Florida and Washington.
- Create 4 output EventHubs called Texas, Alabama, Kansas and Virginia
- For each of the EventHubs, create a consumer group called stranalysis01

Verify that the resources have been created successfully

## Challenge 2

- Create a Stream Analytics Job that uses the Tumbling window to fetch how many unique patients we have every 15 minutes from the California Event Hub. Write the output to the Texas Event Hub. Include events that arrive at the beginning of the interval and exclude those that arrive at the end of each interval.
- Create a Stream Analytics Job that uses the Hopping window to fetch how many unique patients we have every 15 minutes with a hopping size of 5 minutes from the Washington Event Hub. Write the output to the Alabama Event Hub. Exclude events that arrive at the beginning of the interval and include those that arrive at the end of each interval.
- Create a Stream Analytics Job that uses the Sliding window to retreive the number of patients from the California Event Hub in the out-patient-unit grouped by gender for a 15 minute window and update the view each time a patient enters or exits the window. Write the output to the Kansas Event Hub
- Create a Stream Analytics Job that uses the Session Window function to retrieve the vitals of each patient from the Florida Event Hub given a 10 minute timeout with a maximum duration of 15 minutes. Write the output to the Virgina Event Hub.
- Start all 4 stream analytics jobs.

