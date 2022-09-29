# Kickstarting with Excel

## Overview of Project

Louise’s play Fever came close to its fundraising goal in a short amount of time. Now, she wants to know how different campaigns fared in relation to their launch dates and their funding goals. To better understand the trends, the Kickstarter dataset was used. Firstly, the relation between the success of campaigns in the parent category theater and the launch month is investigated and visualized by a line graph. Secondly, the relation between the success of campaigns in the subcategory plays (which is subcategory of theater) and their funding goals is analyzed and visualized by an other line graph. In this report, Analysis of Outcomes Based on Launch Date and Analysis of Outcomes Based on Goals are discussed; challenges and difficulties encountered during the study together with how they were overcome are explained. Finally, conclusions driven from the graphs, the limitation of the dataset and what can be done more are discussed.

### Purpose

The purpose of this project is aimed to assist Louise to better ensure a successful campaign for the play Fever. By utilizing Excel Pivot Tables and Pivot Charts, the data was able to be transformed further to highlight tendencies. Upon analysis of data of similar Kickstarter campaigns, recommendations were made on how Louise could move forward to ensure a successful Kickstarter campaign for her play. While Louise did not quite reach her goal, she was able to raise most of her goal amount in a short period of time. Looking forward, Louise then asked for an exploration on how successful other Kickstarter campaigns were based on their launch dates and funding goals.

## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date

In order to analyze Outcomes based on the launch date a pivot table and a pivot chart based on that table were used. The original data did not have parent category  for a header so this column was created using the category and subcategory column. This was needed to be filtered according to theater in the pivot table. Launch date was given originally in the unix timestamps format which was not readable, so converting to the format: day/month/year, 

> =(((J2/60)/60)/24)+DATE(1970,1,1)

Additionally, two more column were created to be able to analyze the data. Therefore "Years" and "Months" column were created using the following respectively,

> = YEAR(Q2)

> = TEXT(Q2,"mmm")

Note that Q is the column headed as "Date Created Conversion". Next, using the dataset, the main finding is the following line graph:

![Outcomes Based on Launch Date](https://user-images.githubusercontent.com/62758795/192857666-49fe6d4b-4dd8-4630-a992-cab89e41c2aa.png)

In this graph it can be clearly observed that in every month the number of successful campaigns of theater is larger than that of failed campaigns. The successes in the May is the highest. Also note that, there's high successes in June as well as July. Although, the success in February and April are the same, the fail in February is lower than that in April. Thus, February would be a good month to launch a theater campaign. Similarly, the success in the month of April and August are almost identical. Observe that the fail in April is lower than the fail in August, which means that April would be a good month to launch a theater campaign rather than August. This information with the percentage of success is  visualized in the following table:

|Outcomes        |May    |June   |July   |February |April  |August |
|:-----          |:-----:|:-----:|:-----:|:-----:  |:-----:|:----- |
|Successful      |111    |100    |87     |71       |71     |72     |
|Failed          |52     |49     |50     |39       |40     |47     |
|Canceled        |3      |4      |1      |3        |2      |4      |
|% of Successful |67%    |65%    |63%    |63%      |63%    |59%    |
 
All in all, it can be recommended that, Louise launch the campaign in May, and if not possible it may be launched in June, July, February, April or August respectively.

### Analysis of Outcomes Based on Goals

In order to analyze outcomes based on the goals, the range of goals was divided into subintervals as "less than 1000","1000 to 4999","5000 to 9999","10000 to 14999", "15000 to 19999","20000 to 24999","25000 to 29999", "30000 to 34999", "35000 to 39999", "40000 to 44999", "45000 to 49999" and "50000 or more".The original data did not have subcategory column so it was created by using category and subcategory column first. Because it was needed to put the condition "plays" (which is a subcategory of theater) in the **COUNTIFS()** function. Four conditions are argued in **COUNTIFS()** function:lower bound of interval in the column headed as "Goals", upper bound of interval in the column headed as "Goals", "successful" or "failed" or "canceled" in the column headed as "Outcomes" and "plays" in the column headed as "Subcategory". Percentages of "successful", "failed" and "canceled" campaigns of "plays" are computed and displayed in the same table also. Based on the table the line graph named "Outcomes Based on Goals" was created. The concerned graph is the following:

![Outcomes_vs_Goals](https://user-images.githubusercontent.com/62758795/192656834-fe0e6b97-f2b5-467c-bcc5-e8df43b4e360.png)

One quick look in this graph shows that the success and fail in plays campaigns are equivalent if the amount of goal is between $15000 and $19999. If the amount of goal is less than 15000 there is more chance for the campaign being successful than being failed. SO, the probability that a play campaign will be successful is larger than the probability of a play campaign being failed when the amount of the goal is between $35000 and $45000. The following table shows the trend of percentage of success:

|The intervals of Goals  |The percentage of Successful |
|:----------------------:|:---------------------------:|
|Less than 1000          |76%                          |
|1000 to 4999            |73%                          |
|5000 to 9999            |55%                          |
|10000 to 14999          |54%                          |
|15000 to 19999          |50%                          |
|20000 to 24999          |45%                          |
|25000 to 29999          |20%                          |
|30000 to 34999          |27%                          |
|35000 to 39999          |67%                          |
|40000 to 44999          |67%                          |
|45000 to 49999          |0%                           |
|50000 or more           |13%                          |

The above table presents the percentage order of Successful Goals, however in the intervals 35000 to 39999 and 40000 to 44999, it increases unexpectedly. This might be due to the outliers in the dataset. In fact, the Goal has 28 outliers in the plays campaign, which means all goals in last three interval and 2 goals in fourth interval from last are outliers of outcomes. Which factors causes this result we do not now. There might be some goals written mistakenly, it might be because of some factors which were given in the dataset but were not analyzed in this project, such as backers_count; or it might be because of some other factor which were not considered in the dataset. These should be answered, but this is out of scope of the project. Therefore, it might be recommended to Louise to arrange a campaign such that the amount of goal is no more than $15000.

### Challenges and Difficulties Encountered

One challenge was using the function COUNTIFS() and also writing up this report.
 
## Results

The analysis of Outcomes Base on Launch Date indicated that the best month of the year to campaign for a play is May. In every month of the year, the number of successful campaigns is more than the number of failed campaigns. That are, June, July, February, April and August are appropriate months to launch a campaign, respectively.If we consider the analysis of Outcomes based on Goals, an evidential conclusion can be made as the best amount of goals for more success chance is the one less than or equal to $15000. Although, the percentage successful for the amount of goals, from 35000 to 45000, is high enough; this does not fit with the general trend. This, we can not trust this information, it is needed to be more deeply analyzed in different perspectives. Outcomes can be analyzed based on the duration of the campaign. The number in cell of the new column is the difference of numbers in the corresponding cells of columns "deadline" and "launched_at". The created column is the column of duration. For this, a table and a line graph can be arranged as we did for analysis of Outcomes based on Goals. We can analyze Outcomes based on Backers_count similar to the analysis of Outcomes based on goals that we did. Finally, for accuracy, we can make outlier analysis, the dataset is large enough so that some data may be included mistakenly, there might be outliers for some other reasons to be investigated.
