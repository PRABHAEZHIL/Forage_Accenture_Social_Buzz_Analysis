# Forage Accenture Social Buzz Analysis and Visulalization
Accenture Social Buzz Analysis
![Screenshot 2024-08-18 110945](https://github.com/user-attachments/assets/687aabdf-88d3-4b26-8c1b-7c48ef4a4cc3)
# Forage Accenture Analysis
# [Live DashBoard](https://app.powerbi.com/groups/me/reports/10a35f16-58ac-472e-b7ab-49ecf892b063/e0175f649fec1d19e196?experience=power-bi)
### The Project Goal
____
**Social Buzz** is fast growing technology unicorn that need to adapt quickly to its global scale. 
Accenture has started working on the following activities during a three-month POC:
1. An examination of Social Buzz’s use of big data
2. Strategies for a prosperous initial public offering(IPO)
3. An examination to determine the top 5 content category on Social Buzz

### Data Extraction

Total 7 Data Sets:<br>
Among the 7 Data Sets 3 major DataSets is used for analysis<br>
    1. Contents <br>
    2. Reaction Types<br>
    3. Reactions<br>
    
### Data Cleaning

1. Removed unwanted columns, like url, User Id
2. Removed the blank rows
3. Used VLOOKUP to join reactions, reactiontype and contents
   
### Data Loading

Date Table is created by using DAX `Date = CALENDARAUTO()`<br>

Total 6 Measures are created. <br>
1. Top Month = To get Top Month of highest Score
2. Top Category = To get Top Category of hightest Score
3. Top Reaction Type= To get Top Reaction Type of highest Score
4. Top Score by Category= To get table of category with summation score
5. Top Score by Month= To get table of Month with summation of score
6. Top Score by ReactionType= To get table of Reaction Type with summation of Score.
   
Getting Top Reaction Type with the highest  in Score<br>
 
`TotalScoreByReactionType =SUMX(VALUES('Reactions'[Reaction Type]),CALCULATE(SUM('Reactions'[Score])))`<br>
`TopReactionType = 
VAR TopReactionTable =SUMMARIZE('Reactions','Reactions'[Reaction Type],"TotalScore", [TotalScoreByReactionType])
VAR TopReaction =TOPN(1,TopReactionTable,[TotalScore],DESC)
RETURN
MAXX(TopReaction, 'Reactions'[Reaction Type])`<br>

### Analysis
“Animals” and “Science” are two most popular categories of content showing that people “real-life” and “actual” content the most.
### Insight
Food was common theme with the top 5 categories with the highest “health eating” ratings. This may give the audience an indication of the “social buzz” user base. “Social Buzz” can use insights to create campaigns and work with healthy food brands to increase user engagement.



