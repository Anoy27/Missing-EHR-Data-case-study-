# Missing Encounters Analysis


## Objective of this Case Study
The goal was to identify and analyze encounters from the client's EHR dataset that were not successfully imported into the Normandy database.

## Data Exploration 
In the initial exploration of the datasets, I found some anomalies. 2 out of the 25956 values had null values in the client EHR dataset. On the other hand, there were no missing data in the imported dataset called Normandy.  

Apart from missing data some other data anomalies were related to data types and column names. 

## Data Standardization 
To compare the dataset standardization was needed on the cpt_code column name. Moreover, the date columns were transformed into datetime format and client EHR dataset was needed to be grouped by to get a set in the cpt_code column. Lastly, a new column was created with the unique attributes of both dataset so that they can be compared.  

## Findings
Here are some of the findings 
Total Missing Encounters
282 encounters were identified as missing from the Imported dataset. Here is the Missing Encounters Data: missing_encounters_data.csv
## Key Reasons for Missing Encounters

### 1. NORCM Procedure Code:

![image alt](https://github.com/Anoy27/Missing-EHR-Data-case-study-/blob/main/CPT%20Codes.jpg)

Although, CPT codes like ‘97140’ and ‘97110’ are highly present within the missing encounters. Further research, has shown that they are standard procedure codes and are highly present in our imported database. 
However, The CPT code NORCM is not found anywhere. It also does not appear in the imported database. 

Moreover, it appeared in 203 out of 282 missing encounters which is 72% significantly contributing to the discrepancy. 
On the other hand, when provider, missing encounters, and CPT code with NORCM are grouped it shows that 81 out of 95 missing encounters which is 85% of missing encounters with the provider Aiden King have NORCM present. In the case of Elijah Johnson it is as high as 100%.

![image alt](https://github.com/Anoy27/Missing-EHR-Data-case-study-/blob/main/NORCM.jpg)

This suggests that encounters containing NORCM might not be recognized by our database or it’s flagged out by a database trigger. Moreover, there is no certain information about NORCM code in the public domain. So, it can either be a provider-specific new code or an error. 
As a result, this might be one of the main reasons behind missing encounters.

### 2. Provider Trends:
The providers with the highest number of missing encounters include:
1. Aiden King: 95 encounters
2. Noah Lee: 52 encounters
3. Sebastian Miller: 37 encounters

![image alt](https://github.com/Anoy27/Missing-EHR-Data-case-study-/blob/main/Provider.jpg)

This points to potential provider-specific data issues or errors in their system that might cause import issues. 

### 3. Date Trends
Missing encounters are spread across multiple dates, but some clustering was observed. For instance, the highest number of encounters occurred on 2024-09-25, suggesting that there might be a server issue on certain dates.

![image alt](https://github.com/Anoy27/Missing-EHR-Data-case-study-/blob/main/Month.jpg)

Moreover, the highest number of missing encounters happened in September and missing encounters are on the rise month to month.  

### 4. EHR Issues
Research into the public domain suggests that EHR systems can cause some issues while importing data [1] which causes data loss. It can be responsible for a small portion of the missing data. 
Detailed Code and Documentation: 

#### Citations 
[1]- Data Quality and Integration Issues in Electronic Health Records,  PY  - 2009/12/10, SP  - 55, EP  - 95, SN  - 9781420090383, T1  -,  DO  - 10.1201/9781420090413-c4, JO  - Information Discovery on Electronic Health Records.

