# Nashville-Housing-Data
In this Project we are going to perform Data Cleaning on the dataset to make it more usable and comprehensible. The dataset I used contains housing details in Nashville and you can download it [here](https://github.com/AlexTheAnalyst/PortfolioProjects/blob/main/Nashville%20Housing%20Data%20for%20Data%20Cleaning.xlsx).

For a guided approach, follow the tutorial by Alex The Analyst, you canf find the video [here](https://www.youtube.com/watch?v=8rO7ztF4NtU&ab_channel=AlexTheAnalyst). You can find the SQL queries used in this video in this repository.

## Operations Performed

1. **Standardize the Sale Date column**:  In this given dataset, we have the time attached to the Date column which virtually is of no use, so we convert it to the standardized Date format and alter the table by adding a SaleDateConverted Column.


2. **Solving NULL Property Address** problem: In this dataset, we have a lot of NULL values under the column Property Address and it is ideal to remove NULL values in a dataset to make it more usable. If you scroll through the data, you'll find that the same ParcelIDs have missing Address Values, which essentially means we can have it filled by using the Address that already exists for that ParcelID. To do this, we perform a self join where the ParcelIDs are equal and UniqueIDs aren't, we can then update the missing values by using ISNULL() function and fill the values (as we have performed self-joined we have two "tables" to get values from). This solves the NULL value problems.


3. **Breaking out Address into Individual Columns**: In this dataset, the property and owner adresses have multiple values in them (address,city,state). To have a normalised relation we need to eliminate this and we do this by splitting the three values into separate columns for both Property Address and Owner Address.


4. **Change Y and N to Yes and No in "Sold as Vacant"**: In the Sold as Vacant field, we have four values that essentially indicate two outcomes i.e., Y and N essentially mean YES and NO resp. To remove the unneccessary Values and convert them to either YES or NO we use the CASE clause in SQL.


5. **Remove Duplicates**: We have a lot of repeated values in the dataset and it is ideal to not have those, so we remove them by using  a CTE. e essentially PARTITION the table in terms of a few columns and index these rows using ROW_NUMBER, we then fish out the rows that appear more than once and delete them.


6. **Deleting Useless Columns**:  We delete the columns that we have modified earlier in earlier steps and only keep the ones we've updated to optimize the dataset.

