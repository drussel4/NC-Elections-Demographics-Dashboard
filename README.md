[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/drussel4/NC-Elections-Demographics-Dashboard/HEAD)

# NC-Elections-Demographics-Dashboard
This project contains a dashboard allowing the user to analyze N.C. county-level voting results alongside demographic trends. The dashboard contains three exhibits and a table. The first exhibit is a map, which demonstrates the county level voting patterns, with more Democratic voting areas shown in blue and Republican shown in red. The map can also be set to view voting counts and participation. Hovering over the map shows demographic values, which can be used to contextualize voting patterns. The second exhibit is a bar chart, which showcases Dem vs. Rep voting for the largest counties in the state (having 100,000+ residents). The third exhibit is a bar chart, visualizing demographic trends for the largest counties.  All data is downloadable and verifiable via the data source links below.

![dashboard_wake_up](https://github.com/drussel4/NC-Elections-Demographics-Dashboard/blob/master/img/dashboard_wake_up.png?raw=true)

## Usage
The program accomplishes four main things: (1) reads in election results data from [North Carolina State Board of Elections (NCSBE)](https://www.ncsbe.gov/results-data/election-results/historical-election-results-data#by-precinct) text files, (2) queries data from the [American Community Survey (ACS)](https://www.census.gov/programs-surveys/acs) API, (3) joins those data sets at a county level, and (4) builds an ipywidgets-powered dashboard to interrogate the data.

### NCSBE Election Results

The primary goal of this dashboard is to give the user election results data, as defined by votes cast for Democratic and Republican candidates (excludes other parties). The NCSBE provides county level [election results with detailed breakdowns here](https://www.ncsbe.gov/results-data/election-results/historical-election-results-data#by-precinct) as text files, which can be read similarly to a csv using pandas or other packages. We read these in and filter to the five races we are interested in: Presidential, US Senate, US House, NC Senate, and NC House.

![2020_election_results](https://github.com/drussel4/NC-Elections-Demographics-Dashboard/blob/master/img/2020_election_results.png?raw=true)

### American Community Survey (ACS) Demographic Trends

Looking at results alone tells us very little about voting trends. The dashboard also showcases demographic trends, such as age, race, gender, and income, which can inform movement towards one party or another. The Decenniel Census would be the natural first place to look for this data, and it is the most robust, but as of the creation of this project the last available was 2010, which is far too stale. Alternatively, the American Community Survey is conducted every year, as well as more robustly on five year intervals. For this dashboard we leverage the yearly survey data, which is convenient available through the ACS API. The API can be confusing at first but is extremely useful once you've learned it. Try this [query as an example](https://api.census.gov/data/2019/acs/acsse?get=NAME,K200101_001E&for=county:*&in=state:37), retrieving North Carolina's population by county for 2019.

![acs_api_population](https://github.com/drussel4/NC-Elections-Demographics-Dashboard/blob/master/img/acs_api_population.png?raw=true)

For more on learning the ACS API, I recommend starting with this [tutorial video](https://www.youtube.com/watch?v=0NzNllnmTLA&t=2485s).

### Building the ipywidgets Dashboard

So we've acquired and joined the data to power our dashboard. The next step is to build the interactive dashboard, made of ipywidgets, to empower the user to interrogate.

## The Dashboard, Exhibits, and Tables

The dashboard loads with four selection options: (1) metric, (2) race aka contest, (3) demographic overlay, and (4) voting method. The user begins by making their selections and hitting the Update button. After a few seconds, the Exhibits and Table tabs load with the requested data.

![dashboard_wake_up](https://github.com/drussel4/NC-Elections-Demographics-Dashboard/blob/master/img/dashboard_wake_up.png?raw=true)

Metrics:
+ Margin Percent - the percentage vote that the Democratic candidate exceeded/(trailed) the Republican candidate.
+ Margin Count - the raw vote count that the Democratic candidate exceeded/(trailed) the Republican candidate.
+ Votes Cast - the raw vote count cast in that contest regardless of party
+ Vote % of Pop - the percentage of people casting votes of the population (note: percent of registered voting population would be a better metric, but I have not integrated that data yet. Stay tuned.)

Races:
+ Presidential
+ US Senate
+ US House
+ NC Senate
+ NC House

Demographics:
+ Gender
+ Age
+ Race
+ Educational Attainment
+ Income
+ Health Insurance

Voting Methods:
+ Total (Early + Election Day)
+ Early
+ Election Day

The first exhibit is a map, showing the voting results on a county level. Bluer counties had more Democratic vote, redder had more Republican vote. (Note: there are some counties missing in the dataset, causing omissions in the map. Stay tuned for this fix.) Hovering over a county reveals the FIPS code, election results data, and demographic data.

![map](https://github.com/drussel4/NC-Elections-Demographics-Dashboard/blob/master/img/map.png?raw=true)

Where the map is useful for comparing counties geographically, the first bar chart is a better view of magnitude. It filters to only counties having 100,000+ residents, for the sake of having a concise graph (N.C. has 100 counties, far too many to fit cleanly on a single bar chart).

![elec_bar](https://github.com/drussel4/NC-Elections-Demographics-Dashboard/blob/master/img/elec_bar.png?raw=true)

The second bar chart shows the magnitude of the demographic trend, also for the counties having 100,000+ residents.

![demo_bar](https://github.com/drussel4/NC-Elections-Demographics-Dashboard/blob/master/img/demo_bar.png?raw=true)

The next tab, Tables, contains the same data as the exhibits but laid out in tabular form with filters to modify the tables in place. The controls include: (1) years multi-select, (2) columns multi-select, (3) winning party radio buttons, (4) population slider, (5) margin count slider, (6) margin percent slider, (7) votes cast slider, and (8) votes & of population slider. Engaging with these widgets filters the tables, shown below.

![table_controls](https://github.com/drussel4/NC-Elections-Demographics-Dashboard/blob/master/img/table_controls.png?raw=true)

The Yearly Summary Table shows the voting and demographic results grouped at an annual level.

![summary_table](https://github.com/drussel4/NC-Elections-Demographics-Dashboard/blob/master/img/summary_table.png?raw=true)

The County Detail Table shows the voting and demographic results at a county level, across years.

![detail_table](https://github.com/drussel4/NC-Elections-Demographics-Dashboard/blob/master/img/detail_table.png?raw=true)

The data behind the exhibits and tables is downloadable as a csv from the Download button, in case the user needs to analyze the data in a style or precision not possible within the dashboard.

![csv_download](https://github.com/drussel4/NC-Elections-Demographics-Dashboard/blob/master/img/csv_download.png?raw=true)

And that wraps it up! This is a decent example of the power of ipywidgets and interactive controls. Demographics are commonly modeled by political scientists and operatives to inform their campaign and policy decisions. This dashboard offers the opportunity to interrogate North Carolina county trends.

## License

MIT © Dave Russell
