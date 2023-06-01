# limelight
Predicting weekly gross for Broadway theatres

## Description

[Broadway theatre](https://en.wikipedia.org/wiki/Broadway_theatre), or Broadway, are the theatrical performances presented in the 41 professional theatres, each with 500 or more seats, located in the Theater District and the Lincoln Center along Broadway, in Midtown Manhattan, New York City. 

About 80% of the 41 theaters considered to be \"on Broadway\" are owned by 3 groups (see chart below). These groups have significant resources to allocate and how they decide to do so is an expensive question for them. It is plausible they are willing to expend a small amount of those resources to ensure they allocate large amounts in a prudent manner.\n",
    
    "![Broadway Owners](https://drive.google.com/uc?id=1yqvLg8S7xjKlcfJpWY7IcCO8rXeLswlb)\n",
    

<!-- MarkdownTOC autolink="true" autoanchor="true" -->

- [The Problem](#the-problem)
- [Data Dictionary](#Data-dictionary)
- [Methodology](#methodology)
    - [AR (Auto Regressive) Model](#AR-Model)
    - [SARIMA Model](#SARIMA-Model)
    - [Prophet Model](#Prophet-Model)
- [Results](#results)
- [Conclusions](#Conclusion)


<!-- /MarkdownTOC -->



<a id="the-problem"></a>
## The Problem


<a id="Data-dictionary"></a>
## Data Dictionary

`grosses.csv` contains weekly box office grosses from [playbill.com](https://www.playbill.com/grosses)
For more information about the web scraping of this data using R please see https://github.com/rfordatascience/tidytuesday/tree/master/data/2020/2020-04-28.

| variable             | description                                                  |
| :------------------- |  :----------------------------------------------------------- |
| week_ending          |  Date of the end of the weekly measurement period. Always a Sunday. |
| week_number          |  Week number in the Broadway season. The season starts after the Tony Awards, held in early June. Some seasons have 53 weeks. |
| weekly_gross_overall |  Weekly box office gross for all shows                        |
| show                 | Name of show. Some shows have the same name, but multiple runs. |
| theatre              |  Name of theatre                                              |
| weekly_gross         |  Weekly box office gross for individual show/theatre                  |
| potential_gross      | Weekly box office gross if all seats are sold at full price. Shows can exceed their potential gross by selling premium tickets and/or standing room tickets. |
| avg_ticket_price     |  Average price of tickets sold                                |
| top_ticket_price     |  Highest price of tickets sold                                |
| seats_sold           |  Total seats sold for all performances and previews           |
| seats_in_theatre     |  Theatre seat capacity                                        |
| pct_capacity         |  Percent of theatre capacity sold. Shows can exceed 100% capacity by selling standing room tickets. |
| performances         |  Number of performances in the week                           |
| previews             |  Number of preview performances in the week. Previews occur before a show's official open. |


<a id="methodology"></a>
## Methodology


<a id="AR-Model"></a>
### AR (Auto Regressive) Model


<a id="SARIMA-Model"></a>
### SARIMA Model


<a id="Prophet-Model"></a>
### Prophet Model


<a id="results"></a>
## Results


<a id="Conclusion"></a>
## Conclusions
