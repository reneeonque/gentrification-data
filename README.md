# Gentrification Data Set — 01/2018 to 12/2023

This repository contains data, analytic code, and findings that were collected by [The New York City Consumer and Worker Protection](https://data.cityofnewyork.us/Business/Legally-Operating-Businesses/w7w3-xahh) and is available via Open Data which is updated every day. Please filter this dataset using the methodology below, which contains important context and details, before proceeding.

TKTKTK –– About Foreclosure Data

## Data

This analysis uses active and inactive licensing data.

The spreadsheets come from the following sources:

- The New York City Consumer and Worker Protection:
  - `DCA_Legally_Operating_Businesses_08092021.xlsx`: Raw data of active and inactive licenses

Each of the spreadsheets contain, among others, the following columns relevant to the analysis:

- `Expiration Year` — TK description
- `License Status` — TK description
- `Business Name` — TK description
- `Business Address` — TK description
- `Longitude` — TK description
- `Latitude` — TK description

TKTKTK –– About Foreclosure Data

## Methodology

##### Part 1: Cleaning Data

- We cloned original document holding all businesses that had "Deli" or "Bodega" in their name. We then split License Expiration Data into month/date/year columns. We also split License Creation Date into month/date/year columns. Once it was filtered, we copied the data to a new spreadsheet and sorted it by expiration year, in reverse chronological order. Then, we deduped by business name to keep the latest instance, which should settle the question of whether something is still open or not. After that, we hid "License Type" because they are all "Business", "Address State" which are all "NY", Borough Code, and Detail. 


##### Part 2: Filtering Data

- In our Pivot Table, we filtered columns by zip code, rows by expiration year and separated the license status by active or inactive. Values are counts of each instance of inactive or active status. We wanted to see which zip codes had more than a 50% increase in inactive licenses during the pandemic. This was done with a percent change formula between 2018-2019 and 2020-2021. An IF statement told us which zip code fit the criteria with the label of “1”.


### TKTK About Foreclosure Data

##### Part 1: TKTK

##### Part 2: TKTK


## Outputs

The notebooks output this spreadsheet which contains TKTK: [`output/tktktk.csv`](output/tktktk.csv).

## Licensing

All code in this repository is available under the [MIT License](https://opensource.org/licenses/MIT). The data file in the output/ directory is available under the [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/) (CC BY 4.0) license. All files in the data/ directory are released into the public domain.

## Feedback / Questions?

Contact YOUR NAME HERE at your.name@email.com.
