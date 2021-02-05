# NC-Elections-Demographics-Dashboard
This project contains a dashboard allowing the user to analyze N.C. county-level voting results alongside demographic trends. The dashboard contains three exhibits and a table. The first exhibit is a map, which demonstrates the county level voting patterns, with more Democratic voting areas shown in blue and Republican shown in red. The map can also be set to view voting counts and participation. Hovering over the map shows demographic values, which can be used to contextualize voting patterns. The second exhibit is a bar chart, which showcases Dem vs. Rep voting for the largest counties in the state (having 100,000+ residents). The third exhibit is a bar chart, visualizing demographic trends for the largest counties.  All data is downloadable and verifiable via the data source links below.

![dashboard_wake_up](https://github.com/drussel4/NC-Elections-Demographics-Dashboard/blob/master/img/dashboard_wake_up.png?raw=true)

## Usage
The program accomplishes four main things: (1) reads in election results data from [North Carolina State Board of Elections (NCSBE)](https://www.ncsbe.gov/results-data/election-results/historical-election-results-data#by-precinct) text files, (2) queries data from the [American Community Survey (ACS)](https://www.census.gov/programs-surveys/acs) API, (3) joins those data sets at a county level, and (4) builds an ipywidgets-powered dashboard to interrogate the data.

### NCSBE Election Results

The primary goal of this dashboard is to give the user election results data, as defined by votes cast for Democratic and Republican candidates (excludes other parties). The NCSBE provides county level [election results with detailed breakdowns here](https://www.ncsbe.gov/results-data/election-results/historical-election-results-data#by-precinct) as text files, which can be read similarly to a csv using pandas or other packages. We read these in and filter to the five races we are interested in: Presidential, US Senate, US House, NC Senate, and NC House.

![2020_election_results](https://github.com/drussel4/NC-Elections-Demographics-Dashboard/blob/master/img/2020_election_results.png?raw=true)

### American Community Survey (ACS) Demographic Trends

Looking at results alone tells us very little about voting trends. So the dashboard also showcases demographic trends, such as age, race, gender, and income. The American Community Survey is conducted every year, as well as more robustly on five year intervals - for this dashboard we leverage the yearly survey. This survey data is convenient available through the ACS API, which can be confusing at first but extremely useful once you've learned it. Try this [query as an example](https://api.census.gov/data/2019/acs/acsse?get=NAME,K200101_001E&for=county:*&in=state:37), retrieving North Carolina's population by county for 2019.

![acs_api_population](https://github.com/drussel4/NC-Elections-Demographics-Dashboard/blob/master/img/acs_api_population.png?raw=true)

For more on learning the ACS API, I recommend starting with this [tutorial video](https://www.youtube.com/watch?v=0NzNllnmTLA&t=2485s).

### Building the ipywidgets Dashboard

![dashboard_wake_up](https://github.com/drussel4/NC-Elections-Demographics-Dashboard/blob/master/img/dashboard_wake_up.png?raw=true)

![map](https://github.com/drussel4/NC-Elections-Demographics-Dashboard/blob/master/img/map.png?raw=true)

![elec_bar](https://github.com/drussel4/NC-Elections-Demographics-Dashboard/blob/master/img/elec_bar.png?raw=true)

![demo_bar](https://github.com/drussel4/NC-Elections-Demographics-Dashboard/blob/master/img/demo_bar.png?raw=true)

![table_controls](https://github.com/drussel4/NC-Elections-Demographics-Dashboard/blob/master/img/table_controls.png?raw=true)

![summary_table](https://github.com/drussel4/NC-Elections-Demographics-Dashboard/blob/master/img/summary_table.png?raw=true)

![detail_table](https://github.com/drussel4/NC-Elections-Demographics-Dashboard/blob/master/img/detail_table.png?raw=true)

![csv_download](https://github.com/drussel4/NC-Elections-Demographics-Dashboard/blob/master/img/csv_download.png?raw=true)

And that wraps it up! This is a decent example of the power of ipywidgets and interactive controls.

## License

MIT © Dave Russell
