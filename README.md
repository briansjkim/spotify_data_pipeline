# Spotify Data Pipeline
Spotify data pipeline uses the Spotify API to extract the top 50 global songs, transform it to be structured, and use the data to query desired results

# Technologies Used
Python (Pandas) + Jupyter Notebook\
Amazon CloudWatch\
AWS Lambda\
AWS S3\
AWS Glue Crawler + Data Catalog\
Amazon Athena

# Process
Using the Spotify API, the data extraction and transformation code was written in Jupyter notebook.\
The data extraction code was deployed onto AWS Lambda and CloudWatch trigger was added to run weekly. The extracted data is then stored onto a folder in an S3 bucket.\
The data transformation code was also deployed onto a separate Lambda function, and a S3 trigger was added so that whenever new data is stored in the S3 bucket, the transformation function
would run. The transformed data is then stored onto a separate folder in the same S3 bucket.\
When the transformed data arrives, the Glue Crawler will parse through the files and store them in the Glue Data Catalog. From there, I used Athena to query the results.
