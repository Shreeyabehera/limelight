# limelight
Predicting weekly gross for Broadway theatres

## Description

[Broadway theatre](https://en.wikipedia.org/wiki/Broadway_theatre), or Broadway, are the theatrical performances presented in the 41 professional theatres, each with 500 or more seats, located in the Theater District and the Lincoln Center along Broadway, in Midtown Manhattan, New York City. 

About 80% of the 41 theaters considered to be \"on Broadway\" are owned by 3 groups (see chart below). These groups have significant resources to allocate and how they decide to do so is an expensive question for them. It is plausible they are willing to expend a small amount of those resources to ensure they allocate large amounts in a prudent manner.
   
![Broadway Owners](https://raw.githubusercontent.com/Shreeyabehera/limelight/main/img/sunburst_plot_broadway_theatres_owners.png)

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

* Theater-owning conglomerates (our main stakeholders) have an interest in accurate predictions of not just their annual box office gross for the coming year, but also how it is likely to fluctuate week-to-week (our main KPI), so they can budget accordingly. For example, if their cashflow is likely to plummet in a particular week, they want to anticipate this in order to keep enough cash on hand to maintain normal operations (e.g. making payroll). Alternatively, if they can anticipate high sales in a coming week, they can make arrangements for how to spend that money so it put to good use as quickly as possible (e.g. paying off a loan).

* Playbill data offers valuable metrics such as the percentage of theatre seats sold weekly, which can inform decisions about maintenance scheduling, efficient workforce management, and other cost-saving measures.

* Each theatre under a conglomerate has distinct attributes affecting its consumer appeal. As such, conglomerates might assign shows expected to perform well to their more appealing theatres. Therefore, separate models to predict each theatre's sales pattern individually would be beneficial.

* The focus of the models in this context are the Gershwin and Majestic Theatres, chosen due to their data containing the least number of missing values. Significant week-to-week variation in the sales data makes imputation of missing values using traditional methods potentially problematic. Finally, because Gershwin and Majestic are owned by different conglomerates, the performance of the models can be evaluated against possible variations in sales patterns between the two theatres.



<a id="Data-dictionary"></a>
## Data Dictionary

`grosses.csv` contains weekly box office grosses from [playbill.com](https://www.playbill.com/grosses)

For more information about the web scraping of this data please see https://github.com/rfordatascience/tidytuesday/tree/master/data/2020/2020-04-28

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
We used the following data as our train and test data.

Train data: 5 years (2013-06-02 - 2018-05-27)
Test data: 1 year (2018-06-03 - 2019-05-26)

We have tested several time series algorithms to arrive at our final model with varying levels of complexity.

<a id="AR-Model"></a>
### AR (Auto Regressive) Model



<a id="SARIMA-Model"></a>
### SARIMA Model
The Seasonal Autoregressive Integrated Moving Average (SARIMA) is an enhancement to the ARIMA model for handling seasonality. Like an ARIMA(p, d, q), a SARIMA model also requires (p, d, q) to represent non-seasonal orders. Additionally, a SARIMA model requires the orders for the seasonal component, which is denoted as (P, D, Q, S). Combining both components, the model can be written as a SARIMA(p, d, q)(P, D, Q, s).
..to be updated

<a id="Prophet-Model"></a>
### Prophet Model


<a id="results"></a>
## Results

In our comprehensive time series analysis on weekly Broadway sales grosses, we employed the Root Mean Square Error (RMSE) as the yardstick for evaluating the performance of our models. The RMSE provides an estimate of the average discrepancy between our model's predictions and the actual sales grosses. Essentially, a lower RMSE implies a model that is able to more accurately predict Broadway sales on a week-by-week basis. We trained and tested three distinct models: Autoregressive Model (AR), Seasonal Autoregressive Integrated Moving Average (SARIMA), and the Prophet Model. Their respective RMSE results were X, Y, and Z. Based on these metrics, we selected the Prophet Model as our final model, as it achieved an average RMSE of Z. Upon visualizing the forecasted time series on the test data, it was evident that the Prophet model's predictions closely adhered to the observed behavior. We strongly recommend the Prophet Model to our stakeholders. Not only does it adeptly handle seasonality and trends, but it also incorporates irregularities such as holiday spikes. This advanced level of precision offers a significant advantage for theater owners in forecasting their revenue. A reliable revenue estimate aids in efficient financial planning and expense management. Additionally, an accurate revenue prediction model can result in increased profitability by reducing the risk of over or under budgeting. This leads to optimized operations and potentially increased profitability.

### Gershwin Theater


| Errors           | AR Model     | SARIMA         | Prophet                       |
| :----------------|  :-----------|---------------- | -----------------------------|
| RMSE             | 382071       |   173964        |                              |
| MAE              | 260860       |   108365        |                              |
| MAPE             | 0.137628     |   0.058077      |                              |

### Majestic Theater

| Errors           | AR Model     | SARIMA         | Prophet                       |
| :----------------|  :-----------|--------------- |-------------------------------|
| RMSE             |    167139    |  133343         |                              |
| MAE              |    124601    |  101572         |                              |
| MAPE             |    0.129     |  0.100935       |                              |


<a id="Conclusion"></a>
## Conclusions
