# limelight
Predicting weekly gross for Broadway theatres

## Description

[Broadway theatre](https://en.wikipedia.org/wiki/Broadway_theatre), or Broadway, are the theatrical performances presented in the 41 professional theatres, each with 500 or more seats, located in the Theater District and the Lincoln Center along Broadway, in Midtown Manhattan, New York City. 

About 80% of the 41 theaters considered to be \"on Broadway\" are owned by 3 groups (see chart below). These groups have significant resources to allocate and how they decide to do so is an expensive question for them. It is plausible they are willing to expend a small amount of those resources to ensure they allocate large amounts in a prudent manner.
   
    ![Broadway Owners](https://drive.google.com/uc?id=1yqvLg8S7xjKlcfJpWY7IcCO8rXeLswlb)

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

Theater-owning conglomerates (our main stakeholders) have an interest in accurate predictions of not just their annual box office gross for the coming year, but also how it is likely to fluctuate week-to-week (our main KPI), so they can budget accordingly. For example, if their cashflow is likely to plummet in a particular week, they want to anticipate this in order to keep enough cash on hand to maintain normal operations (e.g. making payroll). Alternatively, if they can anticipate high sales in a coming week, they can make arrangements for how to spend that money so it put to good use as quickly as possible (e.g. paying off a loan).

While the models we build here predict gross sales, the Playbill data includes other potential outcome variables that could be of interest that could be easily predicted using similar models. Reliable forecasts of the percentage of theater seats sold on a weekly basis can serve as valuable information for theater owners. This data can aid in planning activities such as renovations or facility maintenance, timed strategically during weeks with lower occupancy. Moreover, this knowledge can contribute to efficient workforce management, enabling the reduction of staff during less busy weeks, thus leading to cost savings.


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

In our comprehensive time series analysis on weekly Broadway sales grosses, we employed the Root Mean Square Error (RMSE) as the yardstick for evaluating the performance of our models. The RMSE provides an estimate of the average discrepancy between our model's predictions and the actual sales grosses. Essentially, a lower RMSE implies a model that is able to more accurately predict Broadway sales on a week-by-week basis. We trained and tested three distinct models: Autoregressive Model (AR), Seasonal Autoregressive Integrated Moving Average (SARIMA), and the Prophet Model. Their respective RMSE results were X, Y, and Z. Based on these metrics, we selected the Prophet Model as our final model, as it achieved an average RMSE of Z. Upon visualizing the forecasted time series on the test data, it was evident that the Prophet model's predictions closely adhered to the observed behavior. We strongly recommend the Prophet Model to our stakeholders. Not only does it adeptly handle seasonality and trends, but it also incorporates irregularities such as holiday spikes. This advanced level of precision offers a significant advantage for theater owners in forecasting their revenue. A reliable revenue estimate aids in efficient financial planning and expense management. Additionally, an accurate revenue prediction model can result in increased profitability by reducing the risk of over or under budgeting. This leads to optimized operations and potentially increased profitability.


<a id="Conclusion"></a>
## Conclusions
