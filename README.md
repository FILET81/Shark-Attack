# Sharks-Attack

Import of several libraries:
    import numpy as np
    import pandas as pd

    import seaborn as sns
    import matplotlib.pyplot as plt

    import warnings
    warnings.filterwarnings("ignore")

Look for a list of countries by continent - Done

Import of original DataFrame:
    Look for Encoding of .csv file - Done

DataFrame checking, cleaning and standardization:
   .Check columns info: All dtypes ="object" but Year (="float64")
   .Create a copy of the original DataFrame to work with; and keep the original (just in case)
   .Remove Columns "Unnamed: 22" and "Unnamed: 23" since not significant data
   .Check for missing data in the whole DataFrame
   .Remove columns with high % of missing values and not significant data for the analysis:
        "Case Number"
        "Name"
        "Investigator or Source"
        "pdf"
        "href formula"
        "href"
        "Case Number.1"
        "Case Number.2"
        "original order"
   .Check column names data:
   .Convert column names to lowercase and remove blank spaces
   .Remove all rows where all their values are NaNs
   .No need to reset the index since rows were all the last ones
   .Final DataFrame size to start working on = (6252 x 13)

   .Data cleaning of column "country":
        Apply .title() for a future merge with a new column ("continent")
        Rename country names with lower cases/counts to "Other"
        Remove NaN values (why I didn't renamed to "Other" too?)
        Replace names of both "Usa" and "England" according to the list of countries by continent
        Rename names of "Atlantic Ocean", "South Atlantic Ocean" and "Pacific Ocean" to "Other"
        Upload file with list of countries by continent (.xslx format -pip install openpyxl-) and create a second DataFrame
        Apply same structure as the first DataFrame (column names in lowercase, etc)
        Merge both DataFrames in order to have a new column called "continent"

   .Data cleaning of column "type":
        Check values and counts to analyse their significance compared to the whole DataFrame
        Rename weird values like "Boatomg", "Questionable" or NaNs to "Invalid" in order to have a standardized structure  
  
    .Data cleaning of column "year":
        Check values and counts to analyse their significance compared to the whole DataFrame:
            Check NaN values (just 2 found) and see if they can be replaced for the right year, appearing in other columns
            Replace values having years "500", "5" and "0", for the .mean() of all other years
            Replace dtype to "int64"

    .Data cleaning of column "sex":
        Following same rationale as above, check values and counts of this Series in order to have a standardized structure
        For the assignment of NaN values to either "M" or "F", the approach followed is "proportionality"
        Consideration to convert final values (just "M" and "F") to dtype "bool"; finally dircarded

    .Data cleaning of column "fatal_(y/n)":
        Same rationale as column "sex"
        In this case, conversion to dtype "bool" is applied

    .Data cleaning of column "age":
        Similar approach to column "year"; especially, related to replacement of NaN values for the .mean() of all other ages
        Consideration of using .median() instead of .mean(), but finally discarded since insignificance of output difference
        Replace dtype to "int64" too

    .Missing columns to be cleaned:
        "activity"
        "species"
        In both cases, large amount of values to be cleaned; and difficult to follow a pattern for a good standardization
        Lack of time for the project's delivery too
        Cleaning finally discarded since columns shouldn't be used in Visualizations.


Visualizations:
    .Show shark attacks by "continent" (countplot) - Done
    .Show shark attacks by "continent" and "type" (countplot) - Done
    .Show shark attacks by "continent" and "sex" (countplot) - Done
    .Show age distribution of people attacked (histplot) - Done

    .Show trend over "years", and split by "sex" (lineplot) - Facing issues on the final trends output (further actions needed for the right final output -for instance, group by decades)

    .Try to use a scatterplot with "year" and "age" for pure practice; not fully convinced with the final output
