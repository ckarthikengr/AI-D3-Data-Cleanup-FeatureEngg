# AI-D3-Data-Cleanup-FeatureEngg
Customer Segmentation - Data Cleanup and Feature Engineering experiment

1) Description of the dataset (e.g., what it contains, its features, and the problem it addresses).
    The data set contains customer and their purchase information of a shopping portal. It has features like Customer Age, Marital status , Products, Education, Income and Date of becoming the customer etc. 
    We can perform customer segmentation based on the features.
2) Steps taken for cleaning the dataset
   1) Removed empty income rows
   2) Derived No of days the customer started to shop
   3) Extracted Till date - Age from Year of Birth
   4) Calculated Total spent from various items
   5) Simplified the Marital status
   6) Calculated Family size and parental status
   7) Renamed the column for better understanding
   8) After clean up removed the redundant features
   9) Identified out-liner by plot the dataset
   10) Removed the out-liner
3) Challenges faced during the process and how you resolved them
   1) When calculating total family members i had to suppress the warning as given below
        #Feature - Total members 
            pd.set_option('future.no_silent_downcasting', True)
            data["Family_Size"] = data["Living_With"].replace({"Alone": 1, "Partner": 2}).astype(int) + data["Children"]
   2) I had to use below option to plot correlation matrix. It seems correlation matrix requires only numeric values. I need to further research on the same 
        corrmat= data.select_dtypes(include=['number']).corr()
