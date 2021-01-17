### This Repository contains the project for the course [Data Mining and Text Mining](https://www11.ceda.polimi.it/schedaincarico/schedaincarico/controller/scheda_pubblica/SchedaPublic.do?&evn_default=evento&c_classe=691572&polij_device_category=DESKTOP&__pj0=0&__pj1=17f53de47fb15c45b12fba90714f19a6)
________________________
- Academic year 2020-2021
- 1st semester of 2st year
- [Politecnico di Milano](https://www.polimi.it/)
________________________
#### Professors
* [Lanzi Pierluca](https://www4.ceda.polimi.it/manifesti/manifesti/controller/ricerche/RicercaPerDocentiPublic.do?evn_didattica=evento&k_doc=88664&polij_device_category=DESKTOP&__pj0=0&__pj1=f435c06e8d2aab326cc7a730bde8ad9c)
________________________
#### Teaching Assistance
* [Fernando Benjamin Perez Maurera](https://www.deib.polimi.it/eng/people/details/1189928)
________________________
#### Collaborators
* Saeid Rezaei
* Abdolvakil Fazli
* Tara Tandel
* Ghodrat Rezaei
________________________
## Introduction 

This report is aimed at explaining the methodology that was chosen to analyze and do the classification based on Predictive Maintenance data set for prediction of faults on air conditioning equipment installed mobile network transition site in a 14-days forecast window. Available information is related to weather conditions (past and forecast), alarms and faults occurred on site, statistic features of the site. Generally, we have 621299 number of observations and 136 features for two years (2019-2020) time intervals which in each date there are set of observation falling and the class target(aircon_sum_wo_target_next_14d) is binary values of 0 and 1 which shows the presence of a fault in the following 14 days.

##	Data Visualizing and Preprocessing 
### Data Quality Assurance

As the first step in the data processing and preparation, the attribute (‘Site ID’, ‘Date’) were dropped, because they were less informative toward the target and also the attribute ’N_TRANSPORTED_SITES’ was dropped because it is used as probability weighted of 0.8 for Daily group in the final step. Then we checked whether there are missing to remove them. There was no missing value.
Having two kinds of features which are Categorical Features which has been already one hot encoded (CELL_TYPE_X, GEOGRAPHICAL CLUSTER x) and Numerical attributes which have integer or float values(mean/max/min_w_prevXd, mean/max/min_w_f_nextXd, cat_sum_alarms_prevXd, cat_mean/max/min_persistance_prevXd, skew_cat_alarms_prev14d, kurt_cat_alarms_prev14d), we sepearted them into two group.
Visualization of numerical data was also represented in histograms was taken to better understand of the distribution of data. Since some features may have the outlier and have different distributions different from normal distribution, Power Transformation Scaler was used to transform so-called distributions to Gaussian distribution. Having all the numerical attribute in small scale, we were able to detect outlier better and thereby to replace them with upper and lower bound.
###	 Feature Aggregation
Since numerical features have statistical properties, we did analytical calculations and implementation on them.
Due to the recent weather conditions (3 or 7 days) have high informativity with respect to the (14 days), we did average weighted on them(figure 1).
 <p float="left">
  <img src="Images/equation.png" width="600" height="600" />
</p>
