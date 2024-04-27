# Home_Sales

## Analysis process included in Home Sales jupyter notebook: 

* Import of necessary dependencies
* Read the AWS S3 bucket into a DataFrame
* Created a temporary view of the DataFrame, home_sales
* Used Spark SQL to query the temporary view and answer the following questions:
    * What is the average price for a four bedroom house sold per year?
    * What is the average price of a home for each year the home was built, that has three bedrooms and three bathrooms?
    * What is the average price of a home for each year the home was built, that has three bedrooms, three bathrooms, two floors, and is greater than or equal to 2,000 square feet?
    * What is the average price of a home per "view" rating having an average home price greater than or equal to $350,000?
        * I also determined the run time for this last query 
* I cached the temporary table home_sales and then used the cached data to run the fourth query again to see if the run time would improve. The original query took 0.28 seconds and the query using the cached data took 0.16 seconds. 
* I then wrote a parquet, partitioning by the 'date_built' field. 
* After verifying the parquet was created successfully (please see the 'date_built' folder in the repo), I read the parquet data and created a separate temporary view for the parquet data, 'parq_home_sales'
* I used the parquet data to run the fourth query again to see if the run time would improve even more - it took 0.19 seconds to process. 
* I then uncached the home_sales temporary table to save memory space. 


## Conclusion: 

Caching and partitioning are methods to optimize data storage and improve Spark performance, especially when working with large datasets. This assignment displays how caching and partitioning data can improve the run times of queries. Both methods yielded faster run times than the original query (0.28 seconds). Caching the data yielded a faster run time than partitioning - 0.16 seconds compared to 0.19 seconds. 
