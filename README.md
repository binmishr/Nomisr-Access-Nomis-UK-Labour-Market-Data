# Nomisr-Access-Nomis-UK-Labour-Market-Data

The details of the codeset and plots are included in the attached Microsoft Word Document (.docx) file in this repository. 
You need to view the file in "Read Mode" to see the contents properly after downloading the same.

Parlitools - A Brief Introduction
==================================

# parlitools

A collection of useful tools for UK politics, including base maps and datasets. Initially inspired by Bhaskar Karambelkar's [`tilegrams`] package, but with the ability to create a hexagonal map of UK parliamentary constituencies and local authorities. The package also includes functions for data retrieval of current MPs and their consituency details (as it requires calls to two different APIs, this function is not included in [`hansard`] or [`mnis`] packages), and local government composition. There are inbuilt datasets from the 2015 and 2017 UK General Elections and 2011 Census, courtesy of the British Election Study, estimates of EU referendum votes from Chris Hanretty, and hex codes for different party colours.

## Installing

`parlitools` is available on CRAN. To install on CRAN run:

```
install.packages("parlitools")
```

Or, if you use [pacman](https://cran.r-project.org/package=pacman):

```
pacman::p_load(parlitools)
```

## Functions and Data

For more details see [the full documentation](https://docs.evanodell.com/parlitools/reference) or the [vignettes](https://docs.evanodell.com/parlitools/articles/).

### Included Data

`party_colour` - A tibble with the ID, name and hex code for the official colour of a variety of political parties, taken from Wikipedia. Includes all political parties with MPs and a number without MPs. (Sources: https://en.wikipedia.org/wiki/Wikipedia:Index_of_United_Kingdom_political_parties_meta_attributes, [`mnis::ref_parties()`](https://cran.r-project.org/package=mnis))

`bes_2015` - A tibble with the British Election Study 2015 Constituency Results Version 2.2. For information on all the variables in this dataset, see the [bes-2015 vignette](http://docs.evanodell.com/parlitools/articles/bes-2015.html) (Source: http://www.britishelectionstudy.com/data-object/2015-bes-constituency-results-with-census-and-candidate-data/)

`bes_2017` - A tibble with Great Britain constituencies results from the 2017 general election. This data can be linked to 2011 census information in [`census_11`](https://docs.evanodell.com/parlitools/reference/bes.html).

`census_11` - A tibble with constituency-level census data.

`leave_votes_west` - The percentage of votes cast for leave in the 2016 EU referendum. Some constituencies have actual results and others only have estimates by Chris Hanretty; in cases where the actual cote count is known, both the estimates and the actual results are reported. (Sources: Hanretty, C. (2017). Areal interpolation and the UK???s referendum on EU membership. _Journal of Elections, Public Opinion and Parties_, 27(4), 466???483. https://doi.org/10.1080/17457289.2017.1287081,  http://www.bbc.co.uk/news/uk-northern-ireland-36616830)

### Data Retrieval Functions

`current_mps` - Uses functions from `hansard` and `mnis` to create a tibble with data on all current MPs, their party affiliation and their constituency.

`mps_on_date` - Uses functions from `hansard` and `mnis` to create a tibble with data on all MPs from a given date, their party affiliation and their constituency.

`west_hex_map` - A hexagonal cartogram, stored as a simple feature and data frame, of Westminster parliamentary constituencies. `west_hex_map` can be used to create maps like this:

```{r, out.width= '456px', echo=FALSE}
knitr::include_graphics("tools/hex_map.png")
```

`local_hex_map` - Hexagonal cartogram, A hexagonal cartogram, stored as a simple feature and data frame, of all Local Authorities in England, Wales and Scotland.

### Using `parlitools`

For more details, please see the [introductory vignette](https://docs.evanodell.com/parlitools/articles/introduction.html), [using `parlitools` with `cartogram`](https://docs.evanodell.com/parlitools/articles/using-cartograms.html), [mapping local authorities](https://docs.evanodell.com/parlitools/articles/mapping-local-authorities.html) and the vignette detailing [British Election Study 2015](https://docs.evanodell.com/parlitools/articles/bes-2015.html) variables.

## Data Sources

There are a variety of potentially relevant data sources and datasets on UK politics, far too many for me to include them all in this package.

* [Electoral Commission](http://www.electoralcommission.org.uk/our-work/our-research/electoral-data) - Electoral results dating back to 2005.

* [British Election Study](http://www.britishelectionstudy.com/data/) - A large selection of open data, including panel surveys, linked data and aggregated Twitter data, covering elections and referenda.

* My [`hansard`](https://cran.r-project.org/package=hansard) & [`mnis`](https://cran.r-project.org/package=mnis) data retrieval packages for parliamentary APIs.

* [Open Council Data](http://opencouncildata.co.uk/) has data on the names, parties, and wards of all UK councillors, updated more or less weekly. `parlitools` uses this site to power the `council_seats()` function.

