<div align="center" style=" font-size: 80%; text-align: center; margin: 0 auto">
<img src="https://raw.githubusercontent.com/Explore-AI/Pictures/master/Python-Notebook-Banners/Code_challenge.png"  style="display: block; margin-left: auto; margin-right: auto;";/>
</div>

<br>

# Exam 1: Data Visualisation (Power BI)
© ExploreAI Academy

## Instructions to students

This section will test your knowledge on Visualising Data and Power BI.

This markdown contains the instructions, some starter code, as well as questions. 

Perform the necessary steps within Power BI to find the answers to the questions below. Select the corresponding answer on Athena. The questions included in this notebook are numbered according to the Athena questions. The options for each question have also been included (however the order of the options may differ to Athena).

Be sure to save your Power BI (.pbix) file upon completion, then, zip the file and upload it at the end of your exam when prompted (part of the multiple-choice test).

**_Good luck!_**

## Honour code

By submitting your Power BI file you confirm that the solutions in the file are a result of your own work and that you abide by the EDSA honour code (https://drive.google.com/file/d/1bl28j1Qe5jNyfnd7Tcuyilj-NBEQP_Tt/view?usp=sharing).

Non-compliance with the honour code constitutes a material breach of contract. 

>⚠️ Sharing or uploading this assessment anywhere (other than onto Athena), as whole or in part, is a violation of the honour code.

## **Introduction**

**United Nations Sustainable Development Goal: End Poverty**

Ending poverty in all its forms is one of the greatest challenges faced by society because it is affected by many factors. The COVID-19 pandemic had a profound impact on global economies, and South Africa was no exception. 

This exam will help us understand the shifts in poverty levels between 2017 and 2021\. You will create visualisations using Power BI to explore how location, age and poverty changed during this period. 

## **Data and features overview**

#### The instructions in this document will guide you in creating columns, measures, and visuals that will enable you to answer the MCQs.

#### You are supplied with two datasets to work with:

* The National Income Dynamics Study (NIDS) Wave 5 2017, which we'll refer to as the 2017 dataset; and

* The NIDS Coronavirus Rapid Mobile (CRAM) Survey Wave 5 2021, which we'll refer to as the 2021 dataset.

Both of these datasets include sample survey data. Because of the nature of sample survey data, some consideration should also be given to the type of questions asked. For example, the difference between a household and an individual. In the 2017 dataset, multiple individuals per household were interviewed, even those younger and older than the labour force participation age. However, in the 2021 dataset, we assume that only one individual of labour force participation age (18-64, inclusive) per household was interviewed. Remember to attentively read if the instructions and MCQs refer to households versus individuals.

#### Download the VD Exam \- student folder from Athena. The folder contains the following:

* A Power BI file (VD\_Student.pbix) that already includes five tables. The relationships between the tables have already been created. 
* The five tables used in the analysis. Ensure that the tables are downloaded to your computer and linked to the relevant tables on Power BI. (Edit this in Data source settings).  
* A feature description PDF is provided for the column names, feature descriptions, data types, data mappings, and keys of the two datasets. (Note: we do not use the Employment tables in this analysis)  
* A JSON file that will be needed for the questions below. (Instructions will be given on what to do with this file)

#### 

### **2017 dataset**

#### You are supplied with two tables that include 54 features from the NIDS Wave 5 2017 dataset.

* `HHRoster_2017`   This table connects an individual's unique id with a unique household id. Other features included in this table are population group, gender, interview month, date of birth, and marital status.

* `Household_2017`   This table provides information on households such as the household income, the province and geographical type of the household, and if the household has access to water and electricity.

### **2021 dataset**

#### You are supplied with two tables that include 38 features from the NIDS-CRAM Wave 5 2021 dataset:

* `Personal_2021`   This table has the same function as `HHRoster_2017` in the 2017 dataset. However, because only a single individual was interviewed per household, no household id is used.

* `Household_2021`   Similarly, this table has the same function as `Household_2017`. Similar questions were asked about the households in both datasets, however, some features are the same but have different column names and data mappings.

**Additionally**:

* `Province`  
  A link table containing information about the provinces that we created to allow us to filter across the 2017 and 2021 tables. 

## **Relationships**

Once all the data sources have been set up correctly, go to the Model pane to view the Entity Relationship Diagram (ERD). Looking at the ERD you will notice the following:

The 2017 dataset includes both household and person data; therefore, the cardinality between HHRoster\_2017 and Household\_2017 is one to many (1:\*). The cross-direction filter between HHRoster\_2017 and Household\_2017 is set to both so you can filter across the two tables.

Since the 2021 dataset only includes a person id, the cardinality between the two tables is one to one (1:1). The relationship also has a cross-direction filter set to both so you can filter across the two tables.

Note, although the 2017 and 2021 datasets have similar features, there are no direct relationships between the tables of the two datasets. Therefore we have created the Provinces table as a link table to filter across the 2017 and 2021 tables. 

<div style="text-align: center;">
  <img src="https://raw.githubusercontent.com/Explore-AI/Pictures/master/VD-exam-erd.png" alt="ERD Diagram" style="width: 60%;">
</div>

<div style="text-align: center;">
  <i>Figure 1: The ER Diagram</i>
</div>

## **Instructions overview**

In the following sections, you are instructed on three main topics: location, age and poverty. To create features relating to these topics, you will need to create new columns, measures, tables and visualisations.  

## **Section 1: Location**

Download and open up the VD\_Student.pbix in Power BI and ensure all data sources are connected correctly on your computer. 

Analyse the ERD in the Model pane.

1.  **What is the cardinality and cross-direction filter of the relationship between `Provinces and Household_2017`?**  
   * A) One-to-Many, Single  
   * B) Many-to-One, Single  
   * C) One-to-One, Both  
   * D) Many-to-Many, Both 

#### **Task:**

To visualise features about the provinces of South Africa, create a shape map. You will need to activate the use of this visualisation in the Power BI settings and import the JSON shape map provided (`south-africa-provinces.json`). You will need to create two maps, one for 2017 and one for 2021\.

#### **MCQs:**

2.  **Which feature should be used to define the location for the Shape Map visualisation?**  
   * A) Province\_Code 
   * B) prov\_code  
   * C) prov\_name  
   * D) Region\_Name  

Some province(s) may not link automatically. You will need to debug what the issue is.

3.  **What was the bug in the** `Provinces` **table?**  
   * A) The prov\_code is incorrect 
   * B) A null value  
   * C) A spelling error  
   * D) There is no relationship between the table  


## **Section 2: Age**

Age, in conjunction with gender and geographical location, influences both poverty and unemployment rates because they are indicators of access to resources and opportunities related to economic activity, equality, and standard of living.

For this exam, we consider the **working age as between 18 and 64, inclusive.**

To investigate unemployment, you will need to determine if an individual is of working age and, therefore, part of the labour force. However, the ages of individuals are not given in either the 2017 or 2021 datasets. You will need to calculate this.

We will also investigate the effects of poverty on specific age groups and how the mean age of the sample changes when focusing on a specific feature such as poverty level, status, and province.

#### Since both the interview and date of birth months are given as the month name, you will need to convert both to numbers to calculate age.

**Task:**

* Use the following code to create a new Table called “Months”. Ensure you rename the columns to *`month_num` and `month`.*

  `{(1, FORMAT(DATE(1,1,1), "MMMM")),(2, FORMAT(DATE(1,2,1), "MMMM")),(3, FORMAT(DATE(1,3,1), "MMMM")), (4, FORMAT(DATE(1,4,1), "MMMM")), (5, FORMAT(DATE(1,5,1), "MMMM")), (6, FORMAT(DATE(1,6,1), "MMMM")), (7, FORMAT(DATE(1,7,1), "MMMM")), (8, FORMAT(DATE(1,8,1), "MMMM")), (9, FORMAT(DATE(1,9,1), "MMMM")), (10, FORMAT(DATE(1,10,1), "MMMM")), (11, FORMAT(DATE(1,11,1), "MMMM")), (12, FORMAT(DATE(1,12,1), "MMMM"))}`

* In `HHRoster_2017` and `Personal_2021`, create **two** new columns in **each** called `dob_m_num` and `intrv_m_num` that convert the month name to a number using the new table you created and the `LOOKUPVALUE()` query.

* Note: we don’t need relationships between these tables if we use LOOKUPVALUE (relationships here will create a circular dependency error).  


4.  Which of the following statements are DML (Data Manipulation Language) statements?  
* (i) `UPDATE HHRoster_2017 SET dob_y = '2021' WHERE dob_y = '0'`  
* (ii) `DELETE FROM Household_2021 WHERE province = 'Western Cape'`  
* (iii) `ALTER TABLE HHRoster_2017 ADD COLUMN age INT`  
  * **A)** ⁠(i) and (ii)
  * **B)** ⁠(i) and (iii)  
  * **C)** ⁠(i), (ii), and (iii)  
  * **D)** ⁠(ii) and (iii)

#### **Task:**

* Use the following DAX code to create a column called `age` in `HHRoster_2017` and `Personal_2021,` that calculates the age of individuals based on their date of birth (`dob_y`) and interview month (`intrv_m_num`).  
  * In HHRoster\_2017, create a new column called age:  
   `age = IF([dob_y] == BLANK(), BLANK(), IF([dob_y] == 2017, 0, (2017 - [dob_y] - ([intrv_m_num] < [dob_m_num]))))`  
  * In Personal\_2021, create a new column called age:  
   `age = IF([dob_y] == BLANK(), BLANK(), IF([dob_y] == 2021, 0, (2021 - [dob_y] - ([intrv_m_num] < [dob_m_num]))))`

#### **MCQs:**

5.  What does the following code snippet do?

    `([intrv_m_num] < [dob_m_num])`

  * A) Accounts for the fact that if the interview occurred before the individual's birthday in that year, their age is actually one year less.  
  * B) Compares the birth month to the current month to determine whether the individual has turned one year older in the current year.  
  * C) Ensures that individuals born after the interview date are not included in the data set.  
  * D) Adjusts the age calculation by adding one year if the interview occurred after the individual's birthday.  


6.  **What is the average (mean) age of the survey group in 2017 and 2021?**  
  * A) 2017: 48.7, 2021: 25.2
  * B) 2017: 18.3, 2021: 36  
  * C) 2017: 27.2, 2021: 41.3 
  * D) 2017: 30.1, 2021: 57.3  

  
The mean ages between the two years are significantly different. This is because they only interviewed people of working age for 2021\. We cannot make comparisons between the years accurately with this difference. Therefore, we need a way to filter the sample to only focus on those who form part of the labour force. This will also allow us to further analyse the effect on different age groups within the labour force. The labour force is defined as individuals between the ages of 18 and 64 inclusive (i.e., 17 \< age \< 65).   

**Task:**

* Write a DAX query to create a new column called `age_grp` that categorises the ages calculated in the previous step into the following six age groups in both `HHRoster_2017` and `Personal_2021`.  
* Age groups: *0-17, 18-24, 25-39, 40-54, 55-64, 65+.*

*Hint:*
* Use an `IF()` statement OR a `SWITCH()` statement with `TRUE()`  
* Remember to account for `BLANK()` values.

* Create two Clustered bar charts, one for 2017 and one for 2021, that shows the percentage distribution between each of the workforce age groups, i.e, 18-24, 25-39, 40-54, 55-64. Remember to use filters on the visualisation to only show these age categories. This visualisation will help you understand how the workforce is distributed across age categories.  
* Note: Ensure you are calculating the percentage using the count of the age\_grp the value.

#### **Use the visualisation to answer the following questions:**

7.  **What is the largest age group in the 2021 dataset?**  
  * A) 65+  
  * B) 18-24  
  * C) 0-17  
  * D) 25-39 

8.  **Which age group from which year has 23.74% of the workforce?**  
  * A) 18-24, 2017  
  * B) 40-54, 2017 
  * C) 18-24, 2021  
  * D) 25-39, 2021  

9.  **What does the difference in the distribution of ages in the 2017 and 2021 workforce imply?**  
  * A) There was no significant change in the age distribution between 2017 and 2021
  * B) More people enter the workforce in 2021  
  * C) The percentage of workforce over 40 significantly dropped in 2021 
  * D) Fewer people entered the workforce in 2021    

Earlier, we calculated the average (mean) age for the entire samples from 2017 and 2021\. However, this did not tell us much, as the age groups included in the survey differed. Now, let’s look at the difference in the labour force specifically (only those whose age falls into 18 \- 64, inclusive)

**Task:**

* Create a new measure in both the `HHRoster_2017` table (called `mean_labour_force_age_2017`) and the `Personal_2021` table (called `mean_labour_force_age_2021`) to store these values.

10.   Which of the following is the most appropriate visualisation to display the mean age for 2017 on a dashboard?  
  * A.) 
<div style="text-align: left;">
  <img src="https://raw.githubusercontent.com/Explore-AI/Pictures/master/VD_mean_age_num.png" alt="Option 1" style="width: 14%;">
</div>

  * B.)
<div style="text-align: left;">
  <img src="https://raw.githubusercontent.com/Explore-AI/Pictures/master/VD_mean_age_scatter.png" alt="Option 2" style="width: 14%;">
</div>  

  * C.)
<div style="text-align: left;">
  <img src="https://raw.githubusercontent.com/Explore-AI/Pictures/master/VD_mean_age_bar.png" alt="Option 3" style="width: 14%;">
</div>  

  * D.)
<div style="text-align: left;">
  <img src="https://raw.githubusercontent.com/Explore-AI/Pictures/master/VD_mean_age_semi.png" alt="Option 4" style="width: 14%;">
<br><br>
</div>  


11.   What is the mean age difference between 2017 and 2021 (remember to filter for: 17 \< age \< 65)?  
  * A.) 13.3  
  * B.) 10.1  
  * C.) 2.1 
  * D.) 5.4    
    


## **Section 3: Poverty**

#### 

The international poverty line is useful to consistently measure poverty across different countries. Because this project is limited to the study of poverty in South Africa, the national poverty lines are more useful.

The poverty lines take into consideration both food and, in some cases, non-food consumption of an individual in a household. Due to changes in the cost of living, the national government makes regular adjustments to these lines.

To determine if an individual is living below any of the three poverty lines, namely the Food Poverty Line (FPL), Lower-Bound Poverty Line (LBPL), and Upper-Bound Poverty Line (UBPL), or above all of these (None), we need to calculate the number of persons per household and the household income per person. We will be using the following values to determine the poverty line:

  <p align="center">
  <img src="https://github.com/Explore-AI/Pictures/blob/59c3d19c5034b3e2d8e3d839a4615e0968ec77e1/SDG_1_Visualisation_Predict/nationa_poverty_lines.png?raw=True"
      alt="poverty lines plots"
      style="padding-bottom=0.5em"
      width=400px/>
      <br>
      <em>Figure 2: The inflation-adjusted national poverty lines (in Rands per person per month).</em>
  </p>


#### 

### **Section 3.1: Determine poverty for households in 2017**

**Task:**  
We will start by looking at the **poverty in 2017**. 

#### We will be categorising households into the four poverty levels (FPL, LBPL, UBPL, or None) based on the inflation-adjusted national poverty lines (Figure 2\) and the number of persons per household.

* In `Household_2017`, use the code below to create a new column called `nopres,` that calculates the number of people living in a household using the number of occurrences of the household ID (`hhid)` in `HHRoster_2017`.   
**DAX code**: `nopres = CALCULATE(COUNT(HHRoster_2017[hhid]))`

* In `Household_2017`, use the code below to create a new column called `hhinc_pp`, that calculates the income per person per household based on the household income `tinc` and the number of persons per household.   
**DAX code**: `hhinc_pp = IF([nopres] <> BLANK(), [tinc]/[nopres], BLANK())`

* Next, *in `Household_2017`, create a new column called `poverty_level_2017`* that determines if the household is living under the Food Poverty Line (FPL), Lower-Bound Poverty Line (LBPL), Upper-Bound Poverty Line (UBPL), or None, based on the inflation-adjusted national poverty lines for 2017\. You can use the flow diagram below to help you. Remember to account for `BLANK()` values.


    <p align="center">
    <img src="https://github.com/Explore-AI/Pictures/blob/febe378a61a50b099f7201283d7cd6f7bc6124f2/SDG_1_Visualisation_Predict/poverty_levels_flow_diagram.jpg?raw=True"
        alt="poverty levels flow diagram"
        style="padding-bottom=0.5em"
        width=800px/>
        <br>
        <em>Figure 3: The flow diagram for calculating the poverty levels in 2017.</em>
    </p>


12.  What is the purpose of this part of the `IF()` condition `IF([hhinc_pp] == BLANK(), BLANK(), ...)`?  
  * A) To ensure households with missing or blank income per person values are excluded from the poverty level categorisation.  
  * B) To assign the "None" category to households with income per person below the FPL.  
  * C) To categorise households with zero income per person as BLANK().  
  * D) To check if the household makes use of a government grant.  

### **Section 3.2: Determine poverty for households in 2021**

#### 

You will need to follow a similar process to determine poverty for households in 2021, however, since the 2021 dataset already provides the number of persons per household, you do not need to calculate it.

#### 

**Task:**

* In `Household_2021`, use the code below to create a new column called `hhinc_pp`,  that calculates the income per person per household based on the household income `hhinc` and the number of persons per household `nopres`.   DAX code:

  `hhinc_pp = IF([nopres] <> BLANK(), [hhinc]/[nopres], BLANK())`

* In `Household_2021`, create a new column called `poverty_level_2021` that determines if the household is living under the Food Poverty Line (FPL), Lower-Bound Poverty Line (LBPL), Upper-Bound Poverty Line (UBPL), or None, according to the inflation-adjusted national poverty lines for 2021 (Figure 2). You can use the same logic given in the 2017 flow diagram (Figure 3), but ensure you update it to the 2021 values.

* Remember to account for `BLANK()` values.


13.  **In 2021, which poverty line does a household with an income per person of R890 a month fall under?**  
  * A) None  
  * B) LBPL  
  * C) FPL  
  * D) UBPL 


### **Section 3.3: Visualise poverty for 2017 and 2021**

Task:

To compare the poverty levels in 2017 and 2021, we will need to connect *`Household_2017`* and *`Household_2021`* with a link table.

* Create the following Table called Poverty\_Level that stores the poverty levels for 2017 and 2021\.   
  
  <div style="text-align: left;">
  <img src="https://raw.githubusercontent.com/Explore-AI/Pictures/master/VD-poverty-level-table.png" alt="Poverty_level_table" style="width: 26%;">
  </div>

  Ensure you have set the following relationships.

  <div style="text-align: left;">
  <img src="https://raw.githubusercontent.com/Explore-AI/Pictures/master/VD-poverty-level-relationships.png" alt="Poverty_level_table" style="width: 50%;">
  </div>


* Next, create two treemaps (one for 2017 and one for 2021\) to visualise the proportion of households in each poverty level for 2017 and 2021 (FPL, LBPL, UBPL, None).
* Note: You need to add a filter to each visual to only include the data for the labour force, i.e, filter to only include 18-24, 25-39, 40-54, 55-64 age categories.
* *Hint:* Use the *`poverty_level`* column you created for the values.


#### **MCQs:**

14.  **What percentage of households in 2017 were living under the Food Poverty Line (FPL)?**  
  * A) 12.49%  
  * B) 11.62%  
  * C) 28.95%  
  * D) 46.93%  

15.  **In 2021, which poverty level had the largest proportion of households?**  
  * A) FPL  
  * B) LBPL  
  * C) UBPL  
  * D) None  

16.  **What are the major differences between the 2017 and 2021 poverty levels?**  
  * A.) 2021 has significantly more people in the LBPL and UBPL  
  * B.) The percentage of people living below the FPL increased in 2021, but there were also more no longer in poverty (in the None category)  
  * C.) 2021 has significantly more people living below the FPL and less people not in poverty (in the None category) 
  * D.) The poverty level dropped in 2021   

      

You should now have six visuals, three for each year, which are: the map of South Africa, the age distribution and the tree map. (You may have also created a visual for the mean working age for each year). Use these visuals to answer the following questions.

17. **What was the percentage point increase in the proportion of households living under the Food Poverty Line (FPL) in KwaZulu-Natal (KZN) from 2017 to 2021?**  
  * A) 12.87%  
  * B) 5.22%  
  * C) 24.42%
  * D) 20.1%  


18. **How did Covid-19 impact the poverty levels for the 18-24 age group?**  
  * A) Covid-19 pushed many more young people into FPL, while the percentage of people above the poverty line dropped significantly.  
  * B)  Covid-19 resulted in a significant increase in the number of young people no longer in poverty.  
  * C) Covid-19 mostly affected those in the LBPL and UBPL, and a dramatic increase was seen in these categories.  
  * D) Covid-19 had little to no impact on the poverty levels for young people, with the percentages remaining relatively stable across all categories.  



### **Section 4: Gross National Income (GNI)**

The Gross Domestic Product (GDP) is a global indicator used to measure the performance of a country's economy. However, GDP is a geographical concept – it considers any value added within the country, no matter by whom. It, therefore, includes income from foreigners and foreign companies on South African soil. Since our surveys are limited to South Africans, we can rather consider the Gross National Income (GNI), which is the total amount of money earned by the country's people and businesses. By inference, then, the GNI will always be lower than the GDP.

#### **Task:**

We now need to calculate the average Gross National Income (GNI) per capita per month, in other words, the sum of household incomes divided by the number of people. When considering the number of people to divide with, remember to only consider individuals for which the household income information is available.

* In `Household_2017`, create two new measures called `nopres_hhincnotblank_2017` and `GNI_percapita_2017`.  
  * `nopres_hhincnotblank_2017` should calculate the total number of people (`nopres`) in households where the income per person (`hhinc_pp`) is not blank.  
  * `GNI_percapita_2017` should calculate the Gross National Income (GNI) per capita for 2017 by dividing the total household income (`tinc`) by the total number of people in households where income per person is not blank.  
* Do the same calculations for the 2021 data, i.e., In `Household_2021`, create two new measures called `nopres_hhincnotblank_2021` and `GNI_percapita_2021.`


#### **MCQs:**

19. **What insights can we obtain by comparing the GNI per capita for 2017 and 2021?**  
   
    <div style="text-align: left;">
      <img src="https://raw.githubusercontent.com/Explore-AI/Pictures/master/VD-GNI-1.png" alt="GNI comparison" style="width: 20%;">
      <br><br>
    </div>

  * A) The GNI per capita remained the same between 2017 and 2021, showing no effect from Covid-19 on income.  
  * B) The GNI per capita decreased significantly from 2017 to 2021, indicating a decline in the average income per person potentially from the impact of Covid-19.
  * C) The GNI per capita increased slightly in 2021 compared to 2017, suggesting economic growth during this period.  
  * D.) The GNI per capita decreased significantly from 2017 to 2021, suggesting that the number of people unemployed decreased in 2021\.  

On each map (2017 and 2021), add the GNI features you calculated to Color Saturation to visualise household income per capita by province. 

20. **After adding the feature, which province shows the highest income per capita in 2017 and 2021 respectively?**  
  * A) 2017: Gauteng, 2021: Gauteng
  * B) 2017: Gauteng, 2021: Western Cape   
  * C) 2017: KwaZulu-Natal, 2021: Western Cape  
  * D) 2017: Western Cape, 2021: Western Cape  


#  

<div align="center" style=" font-size: 80%; text-align: center; margin: 0 auto">
<img src="https://raw.githubusercontent.com/Explore-AI/Pictures/master/ExploreAI_logos/EAI_Blue_Dark.png"  style="width:200px";/>
</div>