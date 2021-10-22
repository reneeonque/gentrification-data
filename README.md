# Gentrification Data Set — 01/2018 to 12/2023

This repository contains data, analytic code, and findings that were collected by [The New York City Consumer and Worker Protection](https://www.google.com) and is available via Open Data published Month Date, Year. Please read that article, which contains important context and details, before proceeding.

## Data

This analysis uses TKTKTK spreadsheets.

The spreadsheets come from the following sources:

- Name of source:
  - `name_of_spreadsheet.xlsx`: Raw data of TKTKTK

Each of the spreadsheets contain, among others, the following columns relevant to the analysis:

- `tktktk` — TK description
- `tktktk` — TK description

## Methodology

The notebook [`tktktktk.ipynb`](notebooks/tktktktk.ipynb) performs the following analyses:

##### Part 1: TKTK

- We cloned original document holding all businesses that had "Deli" or "Bodega" in their name. We then split License Expiration Data into month/date/year columns. We also split License Creation Date into month/date/year columns.

Once it was filtered, we copied the data to a new spreadsheet and sorted it by expiration year, in reverse chronological order. Then, we deduped by business name to keep the latest instance, which should settle the question of whether something is still open or not.

After that, we hid License Type (They are all business), Address State (All NY), Borough Code, Detail

Pivot Table— Columns by Zip Code, Rows by Expiration Year, and Whether the License is Active or Inactive. Values are counts of each instance. 

We wanted to see which zip codes had more than a 50% increase in inactive licenses during the pandemic. This was done with a percent change formula between 2018-2019 and 2020-2021.

An IF statement told us which zip code fit the criteria with the label of “1”.



##### Part 2: TKTK

- Description of what you did with the data


## Outputs

The notebooks output this spreadsheet which contains TKTK: [`output/tktktk.csv`](output/tktktk.csv).

## Running the analysis yourself

You can run the analysis yourself. To do so, you'll need the following installed on your computer:

- Python 3
- The Python libraries specified in [`requirements.txt`](requirements.txt)

## Licensing

All code in this repository is available under the [MIT License](https://opensource.org/licenses/MIT). The data file in the output/ directory is available under the [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/) (CC BY 4.0) license. All files in the data/ directory are released into the public domain.

## Feedback / Questions?

Contact YOUR NAME HERE at your.name@email.com.
