---
title: "Labour's battleground for the 2024 election"
last_modified_at: 2020-05-28GMT:21:37-00:00
tags:
  - 2024 election
  - Labour
  - Battlegrounds
---

In a previous post I looked back at the 2019 election, and how the sense of the Conservatives’ pro Brexit strategy became clear when you looked at the battleground they were facing in terms of seats. 

In this post I’m going to look forward, and examine what Labour’s battleground will look like at the next election.

## The basic battleground 
Chart 1 shows the basic picture. Taking the 2019 election (where Labour won 202 seats to the Conservatives’ 365) as the starting point[^1], it shows how big a ‘swing’ Labour would need to take - or lose - each seat (‘swing’ being the average of the increase in Labour vote share and decrease in its main challenger’s vote share in that seat). Each point represents a seat and is coloured according to the party that won it in 2019. The plot is restricted to seats which are within a 20% swing of being won or lost by Labour.

Labour needs to gain 124 seats to win a majority, and the dashed line marks out this threshold - i.e. assuming that Labour wins seats in order of the ‘swing’ required to take them, it will need to gain all the seats from the centre of the chart out to this dashed line.[^2]  

**Chart 1 - Labour’s electoral battleground for 2024**
<iframe id="igraph" scrolling="no" style="border:none;" seamless="seamless" src="https://sixhundredandfifty.github.io/charts/2020-05-28/chart1_2020_05_28.html" height="600" width="825"></iframe>
<sup>Source: British Election Study</sup>

A few points to make about this basic picture:

* 124 is a lot of seats to gain in a single election. This kind of advance has only been made twice since the Second World War: in Clement Attlee’s Labour landslide in 1945 (+239 seats), and in Blair’s landslide in 1997 (+145 seats).
* The 2010 election offers an interesting parallel. The Conservatives then had been out of office for 13 years (Labour will have been 14 years in opposition in 2024) and faced a similar battleground in terms of seats to the one Labour faces: before the election they were on 210 seats to Labour’s 349, and needed 116 gains to win. But far more of their target seats were marginal compared to Labour’s situation today (see Chart 2), and so they only needed around an average 6% swing for a majority, compared to 11% for Labour in 2024; and they failed to achieve this, averaging only a 4.5% swing and ending up 19 short of a majority. [^3]
* Most of Labour’s target seats are held by the Conservatives but realistically it is also going to need to take a large number of seats from the SNP. Clearly these are two very different opponents, so it’s going to need a strategy with (at least) two prongs.
* One point of trivia: take a look at the third point from the bottom in the ‘8%’ swing column. This seat is Uxbridge and South Ruislip - the Prime Minister’s constituency. Obviously Labour doesn’t have to take every particular seat on its target list to win the election - it could win some ‘safer’ seats on bigger swings instead. But if it’s to have any hope of winning a majority, it may well need to unseat the PM in the process.

**Chart 2 - The Conservatives’  electoral battleground in 2010 (Conservative gains / losses in bold)**
<iframe id="igraph" scrolling="no" style="border:none;" seamless="seamless" src="https://sixhundredandfifty.github.io/charts/2020-05-28/chart2_2020_05_28.html" height="600" width="825"></iframe>

<sup>Source: British Election Study</sup>

## Characterising the battleground 
That’s the basic picture. But it’s not very informative - we need to know more about the battleground seats than just who won them at the last election. We need to know about the voters who make them up.

Professional psephologists know this stuff inside out. But I’m an amateur - I don’t know my Blyth Valley from my Colne Valley. So to get a better handle on what each seat ‘looks like’, I did two things.

First, I downloaded constituency-level data on voter demographics, which the British Election Study compiles using census data.

Second, I asked a data scientist friend whether there was a clever machine-learning method that could help me categorise seats into groups based on this data - and fortunately there was. It’s called KMeans clustering. I won’t go into all the gory details here, but basically I fed a load of the demographic variables for each seat into an algorithm, which then categorised those seats into 5 groups in a way that minimised the within-group differences in the input variables. I specified 5 groups, as this seemed enough to be meaningful, but not so many as to be incomprehensible.[^4]

This is not an exact science, and even if it were I’m not an expert practitioner. But I’m not trying to do anything definitive here - I’m just looking for a way in to the problem. With that caveat in mind, I ran the algorithm, eyeballed the seats in each group and came up with a phrase to characterise them, based on a few constituencies I did know about in each group and the overall distribution of demographic variables. 

Chart 3 shows the results.

**Chart 3 - Labour’s 2024 battleground colour-coded by seat demographic category**
<iframe id="igraph" scrolling="no" style="border:none;" seamless="seamless" src="https://sixhundredandfifty.github.io/charts/2020-05-28/chart3_2020_05_28.html" height="600" width="825"></iframe>

<sup>Source: British Election Study</sup>

The five different categories are summarised in Table 1 (a full summary table of the median of all the demographic variables is shown in Table 2 at the end):

**Table 1 - The five demographic groups and a high-level summary of their populations**

| Group                                 | Age                 | Social Class                            | Qualifications                                   | Leave/Remain    |
|---------------------------------------|---------------------|-----------------------------------------|--------------------------------------------------|-----------------|
| **Cities and large towns**                | Relatively young    | Balanced working class vs middle class  | Balanced number with no qualifications vs degree | Balanced        |
| **Working class towns**                   | Middle-aged         | Highly working class                    | Large number with no qualifications              | Strongly Leave  |
| **Affluent suburbs and leafy city seats** | Older / middle-aged | Highly middle class                     | Large number with degree                         | Balanced        |
| **Middle Britain**                        | Older / middle-aged | Balanced working class vs middle class  | Balanced number with no qualifications vs degree | Strongly Leave  |
| **Affluent cities**                       | Young               | Highly middle class                     | Large number with degree                         | Strongly Remain |


As chart 3 demonstrates nicely, Labour’s strongholds (on the left hand side) are a mixture of cities and working class towns, while the Conservatives’ (who make up most of the right hand side of the chart) are in affluent leafy suburbs and ‘Middle Britain’. 

Following their big election win in 2019, the Conservatives now also occupy a solid number of seats across all categories, having made large inroads into Labour’s working class seats which voted heavily ‘Leave’ in the referendum (and a number of ‘Middle Britain’ seats which Labour also held until the election). Correspondingly, Labour has been pushed back to its strongholds and has relatively little presence outside cities and working class towns (where it is still well-represented, despite the losses of 2019).

So where might Labour go from here? That’s a question I’ll explore in more depth in future posts as I do more analysis, but here are two initial observations:

* **Labour’s target seats are very diverse**: Labour’s target seats (the ones up to the dashed line) are made up of 43 working class towns, 43 Middle Britain seats, 21 affluent suburbs and leafy city seats, 21 city / large town seats, and 6 affluent city seats. The people in these types of seat typically vote very differently, but Labour will have to appeal to all of them if it’s to win a majority without achieving some enormous swings elsewhere. And of these seats, 21 are in Scotland, where they’re fighting the SNP rather than the Conservatives: as noted earlier, a very different opponent.
* **Changes in Labour support in each type of seat have followed a clear pattern in the past decade**. Chart 4 shows how the Labour and Conservative vote share in England and Wales has changed since 2010, when the Conservatives came to power. Since then, we’ve seen the collapse of the Lib Dems, the rise and fall of UKIP, and the reallocation of most of those votes to the Conservatives or Labour - so there’s a lot behind the movements in this chart. But the broad picture is clear: Labour has consolidated its strength in cities, and gained ground in more affluent areas; while at the same time it has haemorrhaged support in working class and Middle Britain seats. It’s these second two groups that make up the lion’s share of target seats. So Labour either needs to arrest its slide in these last two categories, or it needs to turbo-charge its upward march in cities and affluent, traditionally Conservative seats (which would require swings upward of 15% to reap returns).

**Chart 4 - Change in Labour and Conservative vote share from 2010 to 2019 in seats colour-coded by seat demographic category**
<iframe id="igraph" scrolling="no" style="border:none;" seamless="seamless" src="https://sixhundredandfifty.github.io/charts/2020-05-28/chart4_2020_05_28.html" height="600" width="825"></iframe>

<sup>Source: British Election Study</sup>

## What’s next?

A lot can change in four years. By the time of the election, there might be a totally different way to view the battleground. And the categorisation above is just a starting point - as well as knowing the make-up of the voters in each seat, you also need to know what those voters think and want. But the above is, I think, a useful way in to the problem. 

I’ll return to this topic in a future post.

**Table 2 - Full summary of demographic variables (numbers show median percentage of the population across each group that have each characteristic)**

| Variable            | Working class towns        | Middle Britain | Cities and big towns | Affluent suburbs and leafy city seats | Affluent city seats |
|---------------------|----------------------------|----------------|----------------------|---------------------------------------|---------------------|
| Young (18-45)       | 35                         | 32             | 43                   | 33                                    | 53                  |
| Middle Aged (46-64) | 27                         | 28             | 22                   | 28                                    | 19                  |
| Over 65             | 16                         | 20             | 13                   | 18                                    | 9                   |
| Working Class       | 41                         | 35             | 31                   | 26                                    | 21                  |
| Self Employed       | 8                          | 10             | 7                    | 10                                    | 8                   |
| Intermediate Class  | 13                         | 13             | 12                   | 14                                    | 9                   |
| Middle Class        | 23                         | 30             | 28                   | 39                                    | 39                  |
| No Qualifications   | 30                         | 24             | 21                   | 18                                    | 15                  |
| GCSEs               | 32                         | 31             | 27                   | 28                                    | 18                  |
| A Level             | 11                         | 12             | 12                   | 12                                    | 10                  |
| Degree              | 18                         | 25             | 27                   | 33                                    | 45                  |
| Voted Leave          | 60                         | 58             | 48                   | 48                                    | 28                  |

<sup>Mapping to Census 2011 variables as follows: Working Class = Routine, Semi-Routine and Lower Supervisor workers; Middle Class = Higher Professional, Higher Manager and Lower Manager; Self-Employed = Small Employer; GCSE = Level 1 and Level 2; A Level = Level 3; Degree = Level 4. 'GCSEs' refers to the percentage of the population whose highest level of qualification is GCSE, etc.</sup>

[^1]: In theory you start afresh at every election, so looking back at the previous one shouldn’t tell you anything. But obviously in practice it tells you a lot - the results of the last election tell you how many minds you have to change in order to win. If a seat had just under a 2% Conservative majority over Labour in 2019, then Labour would only need to convince one Conservative voter in a hundred to vote for it and it would gain the seat. If the majority were 20%, Labour would need to convince ten voters per hundred. And in practice, election results bear this out - marginal seats are far more likely to change hands than safer ones.

[^2]: Technically the line should be somewhere between 10 and 11, but for clarity on the chart I’ve just put it at 11.

[^3]: The constituency boundaries changed between the 2005 and 2010 elections, so these aren’t actually the numbers of seats won in 2005, but the equivalents had that election been fought on 2010 boundaries.

[^4]: For full transparency on my working, I’ve saved the Python code I used [here](https://github.com/sixhundredandfifty/charts/blob/master/2020-05-28/Kmeans%20clustering%20with%20BES%20demographics.py).
