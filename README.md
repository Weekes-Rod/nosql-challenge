# Exploring Food Establishment Data with NoSQL Analysis

## Introduction
The UK Food Standards Agency evaluates food establishments across the United Kingdom, assigning hygiene ratings to ensure food safety. In collaboration with Eat Safe, Love magazine, we aim to analyze a subset of this data to assist journalists and food critics in prioritizing article topics.

## Database and Jupyter Notebook Setup
### A) Importing Dataset:
1. Import the dataset using the command: `mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json`.
2. Import necessary dependencies (PyMongo and Prettyprint).
3. Create an instance of MongoClient.
4. Confirm the creation of the new database.
5. Assign the database to a variable name.
6. Review the collections within the new database.
7. Assign the collection of interest, 'establishments', to a variable for further use.
8. Review a document within the 'establishments' collection.

## Updating the Database
### A) Addition of a New Restaurant:
1. Create a dictionary containing data for the new restaurant.
2. Insert the new restaurant into the collection.
3. Verify that the new restaurant was successfully added.
4. Find the BusinessTypeID for "Restaurant/Cafe/Canteen" and retrieve only the BusinessTypeID and BusinessType fields.
5. Update the new restaurant with the correct BusinessTypeID.
6. Confirm that the new restaurant was updated.

### B) Removal of Establishments in Dover:
1. Identify the number of documents with 'LocalAuthorityName' as "Dover".
2. Delete all documents where 'LocalAuthorityName' is "Dover".
3. Check if any documents related to Dover remain.
4. Confirm that other documents still exist using 'find_one'.

### C) Data Type Modification and Cleanup:
1. Convert longitude and latitude data from string to decimal.
2. Set non 1-5 rating values to null.
3. Convert the data type of 'RatingValue' from string to integer.
4. Update all documents in the collection.
5. Check that coordinates and rating values are now in numeric format.

## Exploratory Analysis
### A) Identifying Establishments with Hygiene Score of 20:
1. Find establishments with a hygiene score of 20.
2. Display the number of documents found.
3. Present the details of the first document.
4. Convert the result to a Pandas DataFrame.
5. Display the number of rows and the first 10 rows of the DataFrame.

### B) Locating High-Rated Establishments in London:
1. Identify establishments in London with a rating value greater than or equal to 4.
2. Display the number of relevant documents.
3. Present details of the first document.
4. Convert the result to a Pandas DataFrame.
5. Display the number of rows and the first 10 rows of the DataFrame.

### C) Finding Top-Rated Establishments near "Penang Flavours":
1. Set the latitude and longitude for "Penang Flavours".
2. Define the search range based on geographical coordinates.
3. Construct a query to find establishments with the highest rating value.
4. Limit the results to the top 5 establishments with the lowest hygiene score.
5. Display the results.
6. Convert the result to a Pandas DataFrame.

### D) Identifying Establishments with Zero Hygiene Scores by Local Authority:
1. Create a pipeline to match establishments with a hygiene score of 0.
2. Group the matches by Local Authority.
3. Sort the matches in descending order.
4. Execute the pipeline and print the first 10 results.
5. Convert the result to a Pandas DataFrame.
6. Display the number of rows and the first 10 rows of the DataFrame.

#References

UK Food Standards AgencyLinks to an external site. (2022). UK food hygiene rating data API. https://ratings.food.gov.uk/open-data/en-GBLinks to an external site.. Contains public sector information licensed under the Open Government Licence v3.0Links to an external site.
Accessed Sept 9, 2022 and Sept 12, 2022 with the establishment settings as follows: longitude=51.5072, latitude=-0.1276, maxdistancelimit=4567, pagesize=10000, sortoptionkey=distance, pagenumber=(1,2,3,4,5,6,7,8).
