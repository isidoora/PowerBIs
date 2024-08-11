## Diversity and Inclusion
#### Description
Human Resources at our telecom client needs assistance in understanding and improving diversity and inclusion among their employees. Despite their efforts to enhance gender balance at the executive management level, they have not seen significant progress. The main objectives are to:
- Define relevant KPIs in hiring, promotion, performance and turnover, and create a visualisation
- Write what you think some root causes of their slow progress might be
#### Data Preparation
The dataset was provided by the company. To make the data more accessible and easier to analyze, I renamed columns for clarity and usability, modified certain values to simplify analysis and removed columns that were not needed for the analysis.
Additionally, I used DAX (Data Analysis Expressions) to calculate key performance indicators (KPIs). Some of the DAX formulas used are as follows:
- \# women = CALCULATE(COUNT(Performance[Employee ID]), Performance[Gender] = "Female")
- \# men = CALCULATE(COUNT(Performance[Employee ID]), Performance[Gender] = "Male")
- \# new hires (FY20) = COUNTROWS(FILTER(Performance, Performance[New hire FY20?] = "Yes"))
- \# promoted (FY20) = CALCULATE(COUNTROWS(Performance), Performance[Promotion in FY20?] = "Yes")
- \# promoted (FY21) = CALCULATE(COUNTROWS(Performance), Performance[Promotion in FY21?] = "Yes")
- % promoted (FY20) = 
 DIVIDE(
    CALCULATE(DISTINCTCOUNT(Performance[Employee ID]), Performance[Promotion in FY20?] = "Yes"),
    CALCULATE(DISTINCTCOUNT(Performance[Employee ID]), Performance[In base group for turnover FY20] = "Yes"))
  % promoted (FY21) = 
 DIVIDE(
    CALCULATE(DISTINCTCOUNT(Performance[Employee ID]), Performance[Promotion in FY21?] = "Yes"),
    CALCULATE(DISTINCTCOUNT(Performance[Employee ID]), Performance[In base group for Promotion FY21] = "Yes"))
- % turnover (FY20) = DIVIDE(CALCULATE(COUNTROWS(Performance), Performance[FY20 leaver?] = "Yes"),
  DIVIDE(CALCULATE(COUNTROWS(Performance), Performance[In base group for turnover FY20] = "Yes") +
        CALCULATE(COUNTROWS(Performance), NOT ISBLANK(Performance[Job Level after FY20 promotions])), 2))
-Average performance rating (FY20): women = 
CALCULATE(
    AVERAGE(Performance[FY20 Performance Rating]),
    Performance[Gender] = "Female")
- Average performance rating (FY20): men = 
CALCULATE(
    AVERAGE(Performance[FY20 Performance Rating]),
    Performance[Gender] = "Male")
#### Visualization
![First](Screenshot.png)
<!-- [Drugi]() -->
<!-- [Treci]()  -->

#### Key Takeaways
1. Commitment to Gender-Neutral Recruitment: The company’s hiring practices demonstrate a strong commitment to gender-neutral recruitment, which should positively impact diversity in promotions over the coming years.
2. Lack of Diversity in Certain Departments: Departments such as Sales and Marketing, Strategy, and Internal Services are notably less diverse.
3. Increased Promotions for Women: Over the past year, there has been an increase in the percentage of women promoted, indicating a strong effort to foster an inclusive work environment and support women’s career advancement.
4. Higher Turnover Rate Among Women: Women employees have a higher turnover rate compared to men, suggesting potential dissatisfaction or challenges unique to their experience. Factors could include work-life balance, corporate culture, or career growth opportunities.
5. Gender Representation in Senior Roles: The underrepresentation of women in senior roles points to systemic barriers or a lack of support that hinders women’s advancement into leadership positions.
