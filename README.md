# Gentrification Data Set — 01/2018 to 12/2023

This repository contains data, analytic code, and findings that were collected by [The New York City Consumer and Worker Protection](https://data.cityofnewyork.us/Business/Legally-Operating-Businesses/w7w3-xahh) and is available via Open Data which is updated every day. Please filter this dataset using the methodology below, which contains important context and details, before proceeding.

TKTKTK –– About Foreclosure Data

## Data

This [`raw data`](output/tktktk.csv) for this analysis uses active and inactive licensing data, as well as pre-foreclosure and foreclosure records, from 2018 to 2021.

The spreadsheets come from the following sources:

- The New York City Consumer and Worker Protection:
  - `DCA_Legally_Operating_Businesses_08092021.xlsx`: Raw data of active and inactive licenses

The raw data contains, among others, the following columns relevant to the analysis:

- `Expiration Year` — This provides the year in which the license was declared active or inactive.
- `License Status` — This lets viewers know if the license status is inactive or active.
- `Business Name` — This field includes the business names.
- `Business Address` — This column lists the businesses' addresses.
- `Longitude` — This field has the longitude of each business's address.
- `Latitude` — This lists the latitude of each business's address.

TKTKTK –– About Foreclosure Data

- Property Shark:
  - `Raw_Property Shark - Pre-Foreclosure STORES.xlsx` and `Raw_Property Shark - Foreclosure STORES.xlsx`: Raw data of Pre-Foreclosures and Foreclosures

This [`raw data`](https://github.com/reneeonque/gentrification-data/tree/main/data) for this analysis contains, among others, the following columns relevant to the analysis:

- `tktktk` — TK description
- `tktktk` — TK description

## Methodology

#### Licensing Data

##### Part 1: Cleaning Data

- We cloned original document holding all businesses that had "Deli" or "Bodega" in their name. We then split License Expiration Data into month/date/year columns. We also split License Creation Date into month/date/year columns. 
- Once it was filtered, we copied the data to a new spreadsheet and sorted it by expiration year, in reverse chronological order. Then, we deduped by business name to keep the latest instance, which should settle the question of whether something is still open or not. 
- After that, we hid "License Type" because they are all "Business", "Address State" which are all "NY", Borough Code, and Detail. 


##### Part 2: Filtering Data

- In our Pivot Table, we filtered columns by zip code, rows by expiration year and separated the license status by active or inactive. Values are counts of each instance of inactive or active status. We wanted to see which zip codes had more than a 50% increase in inactive licenses during the pandemic. This was done with a percent change formula between 2018-2019 and 2020-2021. An IF statement told us which zip code fit the criteria with the label of “1”.


#### Pre-Foreclosures and Foreclosures Data

##### Part 1: Cleaning Data

- 

##### Part 2: Filtering Data

-

## Findings

#### Licensing Data

The output of the filtered spreadsheet which contains an analyzed tab, a deduped tab, a tab that filters the license expirations by year, the pivot table mentioned in the methodology, a filter that lists addresses that appeared multiple times in the data with a new owner, a tab that lists the addresses with the most ownership changes: [`Filtered_DCA_Legally_Operating_Businesses_08092021.xlsx`](output/tktktk.csv).

- The highest counts of inactive delis and bodegas are 10452 (30), 11216 (30), 11221 (30), 11226 (31), 11208 (32), 11212 (32), 10458 (33), 11233 (33), 11385 (37), 10456 (38), and 11207 (55). These equate to Highbridge, Bedford-Stuyvesant, Bushwick, Flatbush, East New York, Brownsville, Belmont, Ocean Hill, Ridgewood, and Melrose.
- These are the neighborhoods that have experienced more inactivity during the pandemic (2020-2021 to date): 10033, 10453, 10469, 11214, 11219, 11220, 11235, 11374 (all inactive licenses happened during the pandemic), 11417, 11422, and 11423
  - None of the zip codes listed above overlap with zip codes that have the most inactive licenses in general, and many range from just 5-10 inactive licenses, which some of the top zip codes experience every year. 
- Neighborhoods that have experienced more than a 50% increase in inactive licenses during the pandemic are 10021, 11102, 11214, 11219, 11234, 11355, 11358, 11364, 11374, 11417, 11422, 11423, 11693, and 11694.
- We recommend using neighborhoods with more than 5 closures during the pandemic, which focuses on zip codes 11214, 11219, and 11234. These are the neighborhoods of Bath Beach and Bensonhurst, Borough Park, and the area of Marine Park, Flatlands, Georgetown, and Bergen Beach. 
- There are five addresses that became inactive under one name and active under another name. This happened four times for these addresses: 10453, 11214, 11216, 10010, and 10040 which are the neighborhoods of Morris Heights, Bath Beach and Bensonhurst, Bed-Stuy and Crown Heights, Flatiron, and Fort George.
- The address in Bath Beach and Bensonhurst correlates with the 50% increase in inactive licenses during the pandemic. The address is 1919 CROPSEY AVE, Brooklyn, NY 11214.
- The Bed-Stuy and Crown Heights address correlates with the zip codes that have the highest count of inactive licenses over the past four years. This address is 496 NOSTRAND AVE Brooklyn, NY 11216.
- We plan to focus on one of these communities.

#### Foreclosure Data

The [`output data`](output/tktktk.csv) of the filtered spreadsheet which contains TKTKTKTKTK: `Property Shark - Pre-Foreclosure STORES.xlsx` and `Property Shark - Foreclosure STORES.xlsx`.

## Licensing

All code in this repository is available under the [MIT License](https://opensource.org/licenses/MIT). The data file in the output/ directory is available under the [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/) (CC BY 4.0) license. All files in the data/ directory are released into the public domain.

## Feedback / Questions?

Contact Zachary Smith at zachary.smith90@journalism.cuny.edu, Juliet Jeske at juliet.jeske050@journalism.cuny.edu, Renée Onque at renee.onque91@journalism.cuny.edu, or Gabriel Poblete at gabriel.polete35@journalism.cuny.edu.
