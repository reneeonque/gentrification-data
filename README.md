# Licensing and property shark data analysis — 01/2018 to 12/2023

This repository contains data, analytic code, and findings for a story about gentrification. Please read the story before proceeding to the analyses because it contains important contextualizing information.


## Data

This analysis uses data of active and inactive licensing data, as well as pre-foreclosure and foreclosure records, from 2018 to 2021.

The spreadsheets come from the following sources:

#### The New York City Consumer and Worker Protection data
`data/DCA_Legally_Operating_Businesses_08092021.xlsx`: Data of active and inactive business licenses. The data can be found on the website of [the New York City Consumer and Worker Protection](https://data.cityofnewyork.us/Business/Legally-Operating-Businesses/w7w3-xahh).

The data contains, among others, the following columns relevant to the analysis:

- `Expiration Year` — This provides the year in which the license was declared active or inactive.
- `License Status` — This lets viewers know if the license status is inactive or active.
- `Business Name` — This field includes the business names.
- `Business Address` — This column lists the businesses' addresses.
- `Longitude` — This field has the longitude of each business's address.
- `Latitude` — This lists the latitude of each business's address.

#### Property Shark data

`data/Property Shark - Pre-Foreclosure STORES.xlsx` and `data/Property Shark - Foreclosure STORES.xlsx`: This is raw data of Pre-Foreclosures and Foreclosures of stores in New York City. [Property Shark](https://www.propertyshark.com/mason/), which requires membership in order to utilize. The data consists of foreclosure and pre-foreclosure data stretching back to October 2018. Compiling the data took several steps which you can see read about in the methodology further down.

This dataset contains, among others, the following columns relevant to the analysis:

- `Address` — This column lists the businesses' addresses.
- `Zip code` — This is a listing of the zip codes.
- `Creditor` — This lists the creditor of each business.
- `Neighborhood` — This column includes the neighborhood in the city in which the business is located.
- `Effective date` — This lists the date of foreclosure or pre-foreclosure.

## Methodology

#### Licensing Data

The licensing data analysis can be found in the  Excel spreadsheet `output/Filtered_DCA_Legally_Operating_Businesses_08092021.xlsx.`

##### Part 1: Cleaning data to remove duplicate entries of the same business

- We first imported the licensing data, which contains all businesses that had "Deli" or "Bodega" in their name, into a sheet called `Raw.` We then duplicated the original data into a sheet called `Split Date Column` in which we split `License Expiration Date` column into month/date/year columns. We also split `License Creation Date` into month/date/year columns. This allows us to look into license expirations and license creations by year later on.
- We then copied the modified data to a new sheet called `Deduped` and sorted it by expiration year, in reverse chronological order. The data contains multiple entries if the same business has renewed its license multiple times. We then erased entries that contained the same business name except for the latest instance, leaving us with just the latest license registered by a business. These entries also help determine whether an older business with multiple licenses over time, is still open or not.


##### Part 2: Filtering Data
- We wanted to see which zip codes had more than a 50% increase in inactive licenses during the pandemic. To achieve this goal we summarized the data using a pivot table by zip code with subcategories that included the expiration year and whether the license status was active or inactive. This was done with a percent change formula between 2018-2019 and 2020-2021. Using an `IF` statement we labeled any zip code that fit the criteria with a `1`.


#### Pre-Foreclosures and Foreclosures Data

##### Part 1: Downloading the data

Downloading and compiling the data from [Property Shark](https://www.propertyshark.com/) takes several steps. The site has four categories in a pull-down menu for foreclosures. Those categories are:
  - New York City Foreclosures
  - New York City Pre-Foreclosures
  - New York City Auction Results
  - New York City Bank Owned (REO)

Property Shark also includes a number of different types of buildings. For this project, we searched for the category of `Store Buildings` limiting the search first to `New York City Foreclosures` and then to `New York City Pre-Foreclosures` during a second search.

There is a limit of 100 items per Excel spreadsheet downloads on Property Shark and each month had to be downloaded separately. Spreadsheets that contain 100 items or more are sent to a user's email address.

We copied the information from each small sheet and pasted it along with the other months on one single spreadsheet. When we were finished, we had two sets of raw data. (Note: From May of 2020 to September 2021 there are no foreclosures due to the COVID-19 crisis and only two foreclosures for November 2021, October 2021 and from April 2020 through October 2018.)


##### Part 2: Cleaning Data
The lists from Property Shark are labeled with multiple columns that might be useful for a deeper analysis, but for the purposes of counting how many foreclosures occurred from year to year, the columns weren’t needed.  

After making copies of both spreadsheets the only information that was saved was, which allows us to combine the pre-foreclosure with the foreclosure buildings data:
  - Address
  - Zip Code
  - Year
  - Neighborhood


##### Part 3: Filtering Data

Using pivot tables, the datasets were split into zip codes and then broken up by year, with counts of zip codes per year. We were looking for any increase of more than 50% in the amount of foreclosures per zip code between 2018-2019 then 2019-2020 and 2020-2021.  

The pivot table was then copied into separate sheets. The first one was 2018-2019.  The amount of foreclosures for 2019 was sorted highest to lowest.  Then, when compared against the number of foreclosures for 2018, it was easy to see when there was a 50% or more increase.  For instance, for zip code 11233 from 2018, there were 2 buildings and in 2019 there were 10. Any zip code that met the criteria of an increase of more than 50% was given a checkmark in a third column. After the entire list was compared and marked this way, the list was sorted for the column with X and the results were copied and pasted to a new clean spreadsheet that is much easier to read than one buried in a pile of pivot tables.

This was repeated again for 2019-2020 and again 2020-2021. The results of this search are in the spreadsheet labeled Property Shark 50% change - Pre-foreclosure and Foreclosure combined.

The spreadsheet that shows all of the pivot tables and work involved is labeled Working copy for analysis - Pre-foreclosure/Foreclosure

This data set serves as secondary and contextualizing information for this project. Since the foreclosure data was limited for 2020 and 2021 due to COVID-19 it was difficult to determine what was happening in any given neighborhoods, though we could contextualize trends leading up to the pandemic.


## Findings

#### Licensing Data

The output of the analysis is within several tabs of the Excel Spreadsheet named `Filtered_DCA_Legally_Operating_Businesses_08092021.xlsx` and includes a tab without duplicates, a tab that filters the license expirations by year, the pivot table mentioned in the methodology, a filter that lists addresses that appeared multiple times in the data with a new owner, a tab that lists the addresses with the most ownership changes.

- The highest counts of inactive deli and bodega licenses are in the following zip codes: 10452 (30), 11216 (30), 11221 (30), 11226 (31), 11208 (32), 11212 (32), 10458 (33), 11233 (33), 11385 (37), 10456 (38), and 11207 (55). These equate to Highbridge, Bedford-Stuyvesant, Bushwick, Flatbush, East New York, Brownsville, Belmont, Ocean Hill, Ridgewood, and Melrose.
- These are the neighborhoods that have experienced more inactivity during the pandemic (2020-2021 to date): 10033, 10453, 10469, 11214, 11219, 11220, 11235, 11374 (all inactive licenses happened during the pandemic), 11417, 11422, and 11423
- None of the zip codes listed above overlap with zip codes that have the most inactive licenses in general, and many range from just 5-10 inactive licenses, which some of the top zip codes experience every year.
- Neighborhoods that have experienced more than a 50% increase in inactive licenses during the pandemic are 10021, 11102, 11214, 11219, 11234, 11355, 11358, 11364, 11374, 11417, 11422, 11423, 11693, and 11694.
- We recommend using neighborhoods with more than 5 closures during the pandemic, which focuses on zip codes 11214, 11219, and 11234. These are the neighborhoods of Bath Beach and Bensonhurst, Borough Park, and the area of Marine Park, Flatlands, Georgetown, and Bergen Beach.
- There are five addresses that became inactive under one name and active under another name. This happened four times for these addresses: 10453, 11214, 11216, 10010, and 10040 which are the neighborhoods of Morris Heights, Bath Beach and Bensonhurst, Bed-Stuy and Crown Heights, Flatiron, and Fort George.
- The address in Bath Beach and Bensonhurst correlates with the 50% increase in inactive licenses during the pandemic. The address is 1919 CROPSEY AVE, Brooklyn, NY 11214.
- The Bed-Stuy and Crown Heights address correlates with the zip codes that have the highest count of inactive licenses over the past four years. This address is 496 NOSTRAND AVE Brooklyn, NY 11216.
- We plan to focus on one of these communities.

#### Foreclosure Data

The output folder contains two spreadsheets — `output/Property Shark - Pre-Foreclosure STORES.xlsx` and `output/Property Shark - Foreclosure STORES.xlsx` — that each contain several tabs with findings around zip codes with the highest amount of pre-foreclosures and foreclosures.

- `Zip Code by Number` in `output/Property Shark - Pre-Foreclosure STORES.xlsx`: The zip codes with the highest amount of pre-foreclosures are 11412, 11206, and 11432. These are the neighborhoods of St. Albans, Bushwick, and Jamaica.
- `Sorted by Year` in `output/Property Shark - Pre-Foreclosure STORES.xlsx`: St. Albans pops up in the top 5 for the years 2018, 2019, and 2020. Peak pre-foreclosures happened during the pandemic in 2020 and 2021. The neighborhood 11214 (Bensonhurst) appears in the 2020 data top 10.
- Top neighborhoods that experienced a 50% increase in pre-foreclosures for stores between 2019 and 2020 are 10012, 10314, 11214,and 11433. These are the neighborhoods of SOHO, Casteton Corners, Bensonhurst, and Jamaica.
- Top neighborhoods that experienced a 50% increase in pre-foreclosures for stores between 2020 and 2021 are 11412, 11434, 10075, and 11354. These are the neighborhoods of St. Albans, Jamaica, Yorkville, and Flushing.

## Licensing

All code in this repository is available under the [MIT License](https://opensource.org/licenses/MIT). The data file in the output/ directory is available under the [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/) (CC BY 4.0) license. All files in the data/ directory are released into the public domain.

## Feedback / Questions?

Contact Zachary Smith at zachary.smith90@journalism.cuny.edu, Juliet Jeske at juliet.jeske050@journalism.cuny.edu, Renée Onque at renee.onque91@journalism.cuny.edu, or Gabriel Poblete at gabriel.polete35@journalism.cuny.edu.
