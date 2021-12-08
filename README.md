# Gentrification Data Set — 01/2018 to 12/2023

This repository contains data, analytic code, and findings that were collected by [The New York City Consumer and Worker Protection](https://data.cityofnewyork.us/Business/Legally-Operating-Businesses/w7w3-xahh) and is available via Open Data which is updated every day. Please filter this dataset using the methodology below, which contains important context and details, before proceeding.

The second repository contains data obtained from [Property Shark](https://www.propertyshark.com/mason/), which requires membership in order to utilize. The data consists of foreclosure and pre-foreclosure data stretching back to October 2018.

## Analysis 1

## Data

This [`raw data`](https://github.com/reneeonque/gentrification-data/tree/main/data) for this analysis uses active and inactive licensing data, as well as pre-foreclosure and foreclosure records, from 2018 to 2021.

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

- Property Shark:
  - `Raw_Property Shark - Pre-Foreclosure STORES.xlsx` and `Raw_Property Shark - Foreclosure STORES.xlsx`: Raw data of Pre-Foreclosures and Foreclosures

This [`raw data`](https://github.com/reneeonque/gentrification-data/tree/main/data) for this analysis contains, among others, the following columns relevant to the analysis:

- `Address` — This column lists the businesses' addresses.
- `Zip code` — This is a listing of the zip codes.
- `Creditor` — This lists the creditor of each business.
- `Neighborhood` — This column includes the neighborhood in the city in which the business is located.
- `Effective date` — This lists the date of foreclosure or pre-foreclosure.

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

- Property Shark has four categories in a pull-down menu for foreclosures. Those categories are: 
  - New York City Foreclosures
  - New York City Pre-Foreclosures
  - New York City Auction Results
  - New York City Bank Owned (REO) 

- Property Shark also includes a number of different types of buildings.  For this project, we searched for the category of ‘Store Buildings’ which is at the bottom of a blue menu on the left-hand side of the screen.
- Then after searching for Store Buildings, we had to limit our search to one of the four foreclosure categories listed above. We started with ‘New York City Foreclosures’. For foreclosures, there is a gap in information because of Covid-19.  From May of 2020 to September 2021 there are no foreclosures due to the COVID-19 crisis. The error message read as “Due to the ongoing health emergency, foreclosure auctions have been temporarily suspended.”
- We were able to get two foreclosures for this month, October 2021 and from April 2020 bank through October 2018.  To find each month, there is a pull down menu at the top of the blue menu on the left hand side of the page. The months are listed under the topic - Show.  
- To get the data for each month, you have to select Export to Excel after selecting for the month, type of building and category.  Each month had only a handful of buildings, so we copied each small Excel spreadsheet for each month and compiled one large spreadsheet on google sheets of the entire data set.  
- We then repeated this process for the next category - New York City Pre-Foreclosures.  We selected for Store Building again.  There is a limit of 100 items per Excel spreadsheet downloads on Property Shark so since Juliet was using an account paid for by the Craig Newmark School of Journalism at CUNY, she had to download each month separately. Spreadsheets that contain 100 items or more are sent to a user’s email address.  In this case the email did not match her own, so she downloaded each month separately.  he repeated the same process. 
- We copied the information from each small sheet and pasted it along with the other months on one single Google Sheet. We were able to get pre-foreclosures from Sept. 2021 to Oct. 2018. We then repeated this exact process for the final two categories: New York City Auction Results and New York City Bank Owned (REO). Our search yielded no results. 
- When we were finished, we had two sets of raw data. The two lists were not formatted in the same way, so combining them would be difficult. All told these two spreadsheets were really made up of about 50 small Excel spreadsheets that were copied and pasted together by category.  

##### Part 2: Cleaning Data

- The lists from Property Shark are labeled with multiple columns that might be useful for a deeper analysis, but for the purposes of counting how many foreclosures occurred from year to year, the columns weren’t needed.  
- After making copies of both spreadsheets the only information that was saved was:
  - Address 
  - Zip Code 
  - Year 
  - Neighborhood 
- At this point, it was much easier to combine both the Pre-foreclosure and Foreclosure buildings. 

##### Part 3: Filtering Data

- Using pivot tables, the datasets were split into zip codes and then broken up by year, with the number of each time the zip codes appeared as a foreclosure per year.  We were looking for any increase of more than 50% in the amount of foreclosures per zip code between 2018-2019 then 2019-2020 and 2020-2021.  
- The pivot table was then copied into separate sheets.  The first one was 2018-2019.  The amount of foreclosures for 2019 was sorted highest to lowest.  Then, when compared against the number of foreclosures for 2018, it was easy to see when there was a 50% or more increase.  For instance, for zip code 11233 from 2018, there were 2 buildings and in 2019 there were 10. Any zip code that met the criteria of an increase of more than 50% was given a checkmark in a third column. After the entire list was compared and marked this way, the list was sorted for the column with X and the results were copied and pasted to a new clean spreadsheet that is much easier to read than one buried in a pile of pivot tables. 
- This was repeated again for 2019-2020 and again 2020-2021. The results of this search are in the spreadsheet labeled Property Shark 50% change - Pre-foreclosure and Foreclosure combined.
- The spreadsheet that shows all of the pivot tables and work involved is labeled Working copy for analysis - Pre-foreclosure/Foreclosure
- For now this data set is a secondary data set for this project. We agreed as a group that since so much foreclosure data was not available for 2020 and 2021 due to COVID-19 that we really couldn’t get the best idea of what was happening in those neighborhoods. It did give us an idea of what was happening from 2018-2019 and then again in 2019-2020. We did learn about some areas though that might be going through some changes due to what might be gentrification. 


## Findings

#### Licensing Data

The output of the filtered spreadsheet which contains an analyzed tab, a deduped tab, a tab that filters the license expirations by year, the pivot table mentioned in the methodology, a filter that lists addresses that appeared multiple times in the data with a new owner, a tab that lists the addresses with the most ownership changes: [`Filtered_DCA_Legally_Operating_Businesses_08092021.xlsx`](https://github.com/reneeonque/gentrification-data/tree/main/output).

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

The [`output data`](https://github.com/reneeonque/gentrification-data/tree/main/output) of the filtered spreadsheet: `Property Shark - Pre-Foreclosure STORES.xlsx` and `Property Shark - Foreclosure STORES.xlsx`.

- The zip codes with the highest amount of pre-foreclosures are 11412, 11206, and 11432. These are the neighborhoods of St. Albans, Bushwick, and Jamaica.
- St. Albans pops up in the top 5 for the years 2018, 2019, and 2020. Peak pre-foreclosures happened during the pandemic in 2020 and 2021. The neighborhood 11214 (Bensonhurst) appears in the 2020 data top 10.
- Top neighborhoods that experienced a 50% increase in pre-foreclosures for stores between 2019 and 2020 are 10012, 10314, 11214,and 11433. These are the neighborhoods of SOHO, Casteton Corners, Bensonhurst, and Jamaica.
- Top neighborhoods that experienced a 50% increase in pre-foreclosures for stores between 2020 and 2021 are 11412, 11434, 10075, and 11354. These are the neighborhoods of St. Albans, Jamaica, Yorkville, and Flushing.


## Analysis 2 (Referred to in the article)

Once we decided as a group that we wanted to focus on zip code, 11216 which is Bedford-Stuyvesant in Brooklyn, NY, we filtered the data to look at the inactive businesses within the zip code and the top four landlords with the most properties in the neighborhood.

## Data

We used both the DCA and the PropertyShark data for this section in CSV format:

The [`raw and filtered data`](https://github.com/reneeonque/gentrification-data/tree/main/data) for this analysis uses active and inactive licensing data, as well as pre-foreclosure and foreclosure records, from 2018 to 2021.

- The New York City Consumer and Worker Protection:
  - `DCA_Legally_Operating_Businesses_08092021.csv`: Raw data of active and inactive licenses

- Property Shark –– The PropertyShark data in this section is a condensed version of the initial dataset from Analysis 1. Each CSV includes the properties that a specific landlord owns in New York City.
  - `Shulem Herman - Sheet1.csv`: Filtered data of all NYC properties owned by Shulem Herman
  - `Larry Hirschfield - Sheet1.csv`: Filtered data of all NYC properties owned by Larry Hirschfield
  - `Richard Christopher Bramwell Jr. - Sheet1.csv`: Filtered data of all NYC properties owned by Richard Christopher Bramwell Jr.
  - `Yehuda Cohen - Sheet1.csv`: Filtered data of all NYC properties owned by Yehuda Cohen

## Methodology

All of the filtering can be found within this [`jupyter notebook`](https://github.com/reneeonque/gentrification-data/tree/main/notebooks).

#### Filtering DCA data to focus on inactive licenses in 11216

##### Importing Data

- We first imported the CSV.

##### Filtering Data

- We then changed the license expiration dates from objects to dates using the datetime function.
- After making this change, we sorted the dataset by expiration date in ascending order.
- We made the date time change permanent so that it would reflect in the dataset moving forward.
- We then dropped duplicate business names in order to make sure businesses were only being counted once. This way, active businesses would only be counted as active once, and inactive businesses would only be counted as inactive once.
- In order to compare this data to the foreclosure data, we dropped all dates from before 2018.
- We went on to search for the highest counts of inactive licenses by zip code by filtering.
- To determine turnover, we found addresses with unique business owners based on "Address Building," "Address Street Name" and "Address ZIP."
- After this, we were able to determine that zip code 11216 has both one of the highest counts of inactive licenses in our date range, but also an address with four different business owners in the past four years.
- Once this was clear, we filtered the data to just 11216.

##### Exporting Data

- Finally, we exported the data as a CSV.

#### Filtering PropertyShark data to focus on inactive licenses for each of the top four landlords with the most properties in 11216

## Licensing

All code in this repository is available under the [MIT License](https://opensource.org/licenses/MIT). The data file in the output/ directory is available under the [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/) (CC BY 4.0) license. All files in the data/ directory are released into the public domain.

## Feedback / Questions?

Contact Zachary Smith at zachary.smith90@journalism.cuny.edu, Juliet Jeske at juliet.jeske050@journalism.cuny.edu, Renée Onque at renee.onque91@journalism.cuny.edu, or Gabriel Poblete at gabriel.polete35@journalism.cuny.edu.
