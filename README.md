
# Halloween Candy Rankings

This is my submission for the [Maven Analytics Challenge](https://mavenanalytics.io/challenges/maven-halloween-challenge/701f06a2-a19b-41e9-95d3-37a0dcc5492f) for the Halloween Candy Ratings Dataset, Oct 2024

### Problem Statement: 
 
Using online votes ranking 85 types of candy, your task is to find the 3 treats you'll give out on Halloween to guarantee that trick-or-treaters of all tastes find something they'll love and present the data to back up your decision.
## About Dataset

The provided dataset is a collection of candy characteristics, offering insights into various properties that might influence their popularity or success. The dataset consists of 85 entries and includes 13 columns.

The memory usage of the DataFrame is approximately 8.8 KB.

### The columns include:
1. **competitorname:** A string representing the name of the candy.
2. **chocolate:** A binary integer (1 or 0) indicating whether the candy contains chocolate.
3. **fruity:** A binary integer (1 or 0) indicating if the candy is fruity.
4. **caramel:** A binary integer (1 or 0) showing if the candy contains caramel.
5. **peanutyalmondy:** A binary integer (1 or 0) indicating if the candy contains peanuts or almonds.
6. **nougat:** A binary integer (1 or 0) indicating whether the candy has nougat.
7. **crispedricewafer:** A binary integer (1 or 0) indicating if the candy includes crisped rice or wafers.
8. **hard:** A binary integer (1 or 0) indicating if the candy is hard.
9. **bar:** A binary integer (1 or 0) indicating if the candy is in bar form.
10. **pluribus:** A binary integer (1 or 0) indicating whether the candy is sold in multiples (e.g., M&Ms).
11. **sugarpercent:** A float value representing the percentage of sugar in the candy.
12. **pricepercent:** A float value indicating the relative price of the candy compared to others.
13. **winpercent:** A float value representing the popularity or win rate of the candy, which could be used to gauge its overall success.

This dataset can be further analyzed to explore correlations between candy ingredients and their success or consumer preferences
## Methodology

### 1. Data Preparation
Firstly, I ensured there were no Null values in the columns using Microsoft Excel. Then, using the formula the following formula I found out the Average Winpercent for each candy flavour: =AVERAGEIF(C1:C86,1,M1:M86)

Where C1:C86 is the flavour column, 1 is the criteria and M1:M86 is the Winpercent Column.

Then, using python, I created an excel sheet containing the same competitornames but with columns such as category 1, category 2, category 3 and so on. This is because the competitornames had boolean value 1 for more than 1 columns, i.e, they are multilabelled. In order to understand the primary categories and group them accordingly, I created an excel sheet using the primary data given.

The code which I used is given in - [halloween_candy.ipynb](https://github.com/abioz-aiz/halloween_candy_ranking/blob/main/halloween_candy.ipynb)


### 2. Data Visualization
I created an outer join on competitorname in tableau using sheet 1 which is the primary data given by maven and the secondary data that I generated using python.

Furthermore, I created a calculated field to allot primary categories to the candies.

I used the following code for doing that:


    IF [Crispedricewafer] = 1 THEN 'Crispedricewafer'

    ELSEIF [Chocolate] = 1 THEN 'Chocolate'

    ELSEIF [Caramel] = 1 THEN 'Caramel'

    ELSEIF [Fruity] = 1 THEN 'Fruity'

    ELSEIF [Nougat] = 1 THEN 'Nougat'

    ELSEIF [Peanutyalmondy] = 1 THEN 'Peanutyalmondy'

    END

I excluded the other characteristics such as “hard”, “pluribus” because they do not classify as flavours.

To give more info about a candy and to classify it further, I created another calculated field called flavour profile. I used the following code to do this:

    IFNULL([Category 1], '') +

    IF LEN(IFNULL([Category 2], '')) > 0 THEN ', ' + [Category 2]   ELSE '' END +

    IF LEN(IFNULL([Category 3], '')) > 0 THEN ', ' + [Category 3] ELSE '' END +

    IF LEN(IFNULL([Category 4], '')) > 0 THEN ', ' + [Category 4] ELSE '' END

Lastly, I chose Vertical bar charts and scatter plot as the best options to visualize the data.
### Tools Used

**Only Office Sheets Editor**

**Tableau**

**SQL**

## Resultant Dashboard

![Candy Clash](Dashboard 1 (1).png "Candy Clash")
## Challenges

It was challenging to work with multilabelled data in tableau. As this was my first project, it was difficult to understand how to structure the dashboard. 
## Future Work

You are free to give any feedback or suggest improvisations by requesting for changes. 
## Authors

- [Zoiba](https://github.com/abioz-aiz)

