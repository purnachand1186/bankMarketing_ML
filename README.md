# Bank-Marketing-Practical-Application
## Dataset
The data is related with direct marketing campaigns (phone calls) of a Portuguese banking institution. The classification goal is to predict if the client will subscribe a term deposit (variable y).

https://archive.ics.uci.edu/dataset/222/bank+marketing

## Attribute Information  

Input variables:
#### bank client data:
1-age (numeric)  
2-job : type of job (categorical: 'admin.','blue-collar','entrepreneur','housemaid','management','retired','self-employed','services','student','technician','unemployed','unknown')  
3-marital : marital status (categorical: 'divorced','married','single','unknown'; note: 'divorced' means divorced or widowed)
4-education(categorical:'basic.4y','basic.6y','basic.9y','high.school','illiterate','professional.course','university.degree','unknown')
5-default: has credit in default? (categorical: 'no','yes','unknown')  
6-housing: has housing loan? (categorical: 'no','yes','unknown')  
7-loan: has personal loan? (categorical: 'no','yes','unknown')  
#### related with the last contact of the current campaign:
8-contact: contact communication type (categorical: 'cellular','telephone')  
9-month: last contact month of year (categorical: 'jan', 'feb', 'mar', ..., 'nov', 'dec')  
10-day_of_week: last contact day of the week (categorical: 'mon','tue','wed','thu','fri')  
11-duration: last contact duration, in seconds (numeric). Important note: this attribute highly affects the output target (e.g., if duration=0 then y='no'). Yet, the duration is not known before a call is performed. Also, after the end of the call y is obviously known. Thus, this input should only be included for benchmark purposes and should be discarded if the intention is to have a realistic predictive model.  
#### other attributes:
12-campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)  
13-pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric; 999 means client was not previously contacted)  
14-previous: number of contacts performed before this campaign and for this client (numeric)  
15-poutcome: outcome of the previous marketing campaign (categorical: 'failure','nonexistent','success')  
#### social and economic context attributes
16-emp.var.rate: employment variation rate - quarterly indicator (numeric)  
17-cons.price.idx: consumer price index - monthly indicator (numeric)  
18-cons.conf.idx: consumer confidence index - monthly indicator (numeric)  
19-euribor3m: euribor 3 month rate - daily indicator (numeric)  
20-nr.employed: number of employees - quarterly indicator (numeric)  

Output variable (desired target):  
21-y - has the client subscribed a term deposit? (binary: 'yes','no')

## Process Followed:

1. Import 'bank-additional-full.csv' from the data folder
2. Understand data by exploring data through diagrams
   Observations:
     1. The data provided has unbalanced data in the target column 'Y'
     ![image](https://github.com/user-attachments/assets/b770b73c-79ad-4888-9fc3-93d086e5d580)
     2. Outliers exists in 'Duration' & 'Compaign' Columns, cleanup data using IQR.
       
        ![image](https://github.com/user-attachments/assets/883dc91e-4491-44e9-8f2b-f5975d3f132f)
       
        ![image](https://github.com/user-attachments/assets/23806de3-a302-4734-b828-fb0587a70100)

3. perform data engineering on Category columns using LabelEncode, after encoding the a correlational map/diagram shows the relationship among the features
        
   ![image](https://github.com/user-attachments/assets/0b6a20a5-214f-4be9-8108-3d3c9fb4e43a)

4. Using Random Forest Regression, found our the importance of features in the data set
        
   ![image](https://github.com/user-attachments/assets/74cde816-a337-4fdd-ba4d-b83b6c85da72)

5.  Used KNN, Decision Trees, SVM, Logistric regression models with default parameters, and the performance of these models are mesaured as below
        
   ![image](https://github.com/user-attachments/assets/fe5ad27e-9f5a-4784-877b-91da88dcfffd)

6.  Finally Using Grid Search CV, passed multiple parameters for the above mentioned models and found out best scores with best parameters
        
    ![image](https://github.com/user-attachments/assets/4523f352-cf80-4d95-84c4-ceab7d54b7ed)
   
    ![image](https://github.com/user-attachments/assets/847fb09c-ddc7-4121-af1f-839c1ba02069)
         
## Observations: 

1. SVM Model always takes more time to fit the data, but in most cases the accraucy scores are better
2. Decision Tree Classicification Model took less time than SVM but returned second or third best scores
3. KNN & Logistric regressions does returned good scores but in my observation, but they are the least preffered choices for my future analysis.
4. People with University Degree, has a home loan tend to sunscribe to Bank marketing campaigns.

