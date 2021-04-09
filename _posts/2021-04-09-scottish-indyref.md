---
title: "2014 Scottish Independence Referendum results by Westminster constituency"
last_modified_at: 2021-04-09GMT:10:00-00:00
tags:
  - Scotland
  - Scottish independence
---

One thing it would be useful to know about (Scottish) Westminster constituencies is how they voted in the 2014 Scottish independence referendum. But the votes in that referendum were counted and reported at a local authority level, not at the level of Westminster constituencies. So this information isn't readily available (except in the 10 cases where local authorities perfectly overlap with Westminster constituencies, and the 5 Edinburgh constituencies for which individual counts were reported by Edinburgh City Council).

The votes in the 2016 referendum on EU membership were also counted at a local authority level. But after the referendum, Prof Chris Hanretty of Royal Holloway generated [estimates]("https://medium.com/@chrishanretty/final-estimates-of-the-leave-vote-or-areal-interpolation-and-the-uks-referendum-on-eu-membership-5490b6cab878") of how each Westminster constituency had voted, based on the overlap between local authorities and constituencies, and their demographic make-up. 

I don't know of any equivalent estimates for the Scottish IndyRef, so I've borrowed Prof Hanretty's method and applied it to that referendum. The full Hanretty methodology is described [here]("https://pure.royalholloway.ac.uk/portal/files/28724566/article.pdf"), but in summary the steps are:
1. Take the results of the referendum at the **local authority level**, and demographic data on each local authority, to infer a relationship between demographic variables and the number of people who voted each way in the referendum. 
2. Use this relationship, and demographic data on the **areas of intersection between local authorities and Westminster constituencies**, to generate estimates for the number of people who voted each way in the referendum in each area of intersection.
3. Scale these estimates up or down so that, when you add up all the areas of intersection in a particular local authority, you get the correct number of votes reported for either side of the referendum for that local authority. (This makes sure that, where local authorities and Westminster constituencies overlap entirely, the estimate matches the actual result; and it is also likely to lead to better estimates elsewhere.)
4. Add up the scaled estimates for each area of intersection within a particular **Westminster constituency** to generate estimates for the number of people who voted each way in the referendum in that constituency.
5. Use these estimated vote totals to calculate the percentage of voters who voted each way in the referendum in each constituency,

There's one difference in how I applied the model vs the paper - I used a different set of demographic variables for the model in step 1. That's because the variables that are correlated with Euroscepticism aren't necessarily the same as those that are correlated with support for Scottish independence (or that were at the time of the referendum). [Analysis at the time]("https://whatscotlandthinks.org/2014/09/voted-yes-voted/") suggested that support for independence was correlated with:
* **Gender** - Men were more likely to support independence than women.
* **Age** - Younger people were more likely to support independence than older people (though it wasn't a straight line relationship - e.g. while over 65s were the least likely age group to vote Yes, 25-34 year olds were more likely to vote Yes than 16-24 year olds).
* **Economic circumstances** - Voters in more deprived circumstances were more likely to support independence than those in more affluent circumstances.
* **Birth country** - Those born in Scotland were more likely to support independence than those born in the rest of the UK.

I therefore chose variables for the model that reflected these characteristics (though I excluded gender, since the gender split doesn't vary much geographically and so it shouldn't explain any differences between the results in different local authorities). The full set of demographic variables I used for each characteristic is set out in Table 1.

**Table 1 - Demographic variables used in model**

| Characteristic         | Variable - % of the population...                                          |
|------------------------|----------------------------------------------------------------------------|
| Age                    | Aged 16-19</br>Aged 20-24</br>Aged 25-29</br>Aged 30-44</br>Aged 45-59</br>Aged 60-64</br>Aged 65+ |
| Economic circumstances | In managerial or professional jobs </br> Unemployed                              |
| Birth place            | Born in Scotland </br> Born in the rest of the UK                                |

On top of this, and as per the Hanretty method, I also included the population of each local authority as a variable in the model, since this clearly influences the number of voters and hence count of total votes. 

In the analysis, I treated each Westminster constituency in the Edinburgh area as a local authority, since results were available at the constituency level.

Data sources were as follows:
* **Demographic and population data**: [Scottish Census data]("https://www.scotlandscensus.gov.uk/ods-web/data-warehouse.html#bulkdatatab") at the 'Census Output Area' level (the lowest-level area for which data is available, and into which all local authorities and Westminster constituencies can be decomposed).
* **Referendum results**: Local authority results compiled by the [University of Edinburgh]("https://datashare.ed.ac.uk/handle/10283/2614"), plus constituency-level results for all Westminster constituencies within the Edinburgh area from [Edinburgh City Council]("https://www.edinburgh.gov.uk/downloads/file/24558/analysis-of-voting-totals-in-the-city-of-edinburgh-area").

The model predicted results at the local authority to within an average of 2.6% of the actual figures (i.e. a 'mean absolute error' of 2.6%).[^1] So I judged that the model was good enough to be used to predict results in the areas of intersection (step 2 of the method), which would then go on to be used in steps 3-5 to ultimately generate estimates for Westminster constituencies.

I've made my Python code, input data and full results available [here]("https://github.com/sixhundredandfifty/charts/tree/master/2021-04-09") for reference. 

Here are the results, in table and map form - I'll be using these in various bits of analysis in future posts.

**Table 2 - Estimated 2014 Scottish IndyRef results by Westminster constituency**

| Constituency                                | Yes   | No    |
|---------------------------------------------|-------|-------|
| Aberdeen North                              | 46.0% | 54.0% |
| Aberdeen South                              | 36.5% | 63.5% |
| Airdrie and Shotts                          | 56.9% | 43.1% |
| Angus                                       | 50.2% | 49.8% |
| Argyll and Bute                             | 41.5% | 58.5% |
| Ayr, Carrick and Cumnock                    | 45.9% | 54.1% |
| Banff and Buchan                            | 42.2% | 57.8% |
| Berwickshire, Roxburgh and Selkirk          | 36.8% | 63.2% |
| Caithness, Sutherland and Easter Ross       | 50.9% | 49.1% |
| Central Ayrshire                            | 46.2% | 53.8% |
| Coatbridge, Chryston and Bellshill          | 53.9% | 46.1% |
| Cumbernauld, Kilsyth and Kirkintilloch East | 51.6% | 48.4% |
| Dumfries and Galloway                       | 35.7% | 64.3% |
| Dumfriesshire, Clydesdale and Tweeddale     | 33.4% | 66.6% |
| Dundee East                                 | 50.8% | 49.2% |
| Dundee West                                 | 51.5% | 48.5% |
| Dunfermline and West Fife                   | 45.4% | 54.6% |
| East Dunbartonshire                         | 32.0% | 68.0% |
| East Kilbride, Strathaven and Lesmahagow    | 45.1% | 54.9% |
| East Lothian                                | 38.3% | 61.7% |
| East Renfrewshire                           | 36.8% | 63.2% |
| Edinburgh East                              | 47.3% | 52.7% |
| Edinburgh North and Leith                   | 40.0% | 60.0% |
| Edinburgh South                             | 34.7% | 65.3% |
| Edinburgh South West                        | 38.4% | 61.6% |
| Edinburgh West                              | 34.5% | 65.5% |
| Na h-Eileanan an Iar                        | 46.6% | 53.4% |
| Falkirk                                     | 45.4% | 54.6% |
| Glasgow Central                             | 52.6% | 47.4% |
| Glasgow East                                | 42.8% | 57.2% |
| Glasgow North                               | 58.0% | 42.0% |
| Glasgow North East                          | 51.8% | 48.2% |
| Glasgow North West                          | 51.1% | 48.9% |
| Glasgow South                               | 51.4% | 48.6% |
| Glasgow South West                          | 51.4% | 48.6% |
| Glenrothes                                  | 51.0% | 49.0% |
| Gordon                                      | 41.0% | 59.0% |
| Inverclyde                                  | 49.9% | 50.1% |
| Inverness, Nairn, Badenoch and Strathspey   | 46.5% | 53.5% |
| Kilmarnock and Loudoun                      | 46.8% | 53.2% |
| Kirkcaldy and Cowdenbeath                   | 46.1% | 53.9% |
| Lanark and Hamilton East                    | 46.9% | 53.1% |
| Linlithgow and East Falkirk                 | 45.4% | 54.6% |
| Livingston                                  | 46.1% | 53.9% |
| Midlothian                                  | 43.7% | 56.3% |
| Moray                                       | 42.4% | 57.6% |
| Motherwell and Wishaw                       | 54.7% | 45.3% |
| North Ayrshire and Arran                    | 46.5% | 53.5% |
| North East Fife                             | 36.1% | 63.9% |
| Ochil and South Perthshire                  | 41.3% | 58.7% |
| Orkney and Shetland                         | 34.6% | 65.4% |
| Paisley and Renfrewshire North              | 47.0% | 53.0% |
| Paisley and Renfrewshire South              | 47.4% | 52.6% |
| Perth and North Perthshire                  | 41.6% | 58.4% |
| Ross, Skye and Lochaber                     | 44.2% | 55.8% |
| Rutherglen and Hamilton West                | 47.7% | 52.3% |
| Stirling                                    | 40.2% | 59.8% |
| West Aberdeenshire and Kincardine           | 38.2% | 61.8% |
| West Dunbartonshire                         | 54.0% | 46.0% |

**Chart 1 - Map of estimated Scottish IndyRef results by Westminster constituency**

<div class="flourish-embed flourish-map" data-src="visualisation/5672536"><script src="https://public.flourish.studio/resources/embed.js"></script></div>

[^1]: For reference, the mean absolute error of the Hanretty model used in the EU referendum estimates was 2.5%. 
