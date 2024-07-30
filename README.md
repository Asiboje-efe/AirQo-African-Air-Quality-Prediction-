# AirQo-African-Air-Quality-Prediction-

Background <br/>
  • Overview <br/>
  • Project question <br/>
  • Evaluation metrics<br/>
Findings<br/>
Conclusion<br/>

## Background 
### Overview
AirQo African Air Quality Prediction aims to predict air quality around Africa using Sentinel 5P satellite data. The project focuses on estimating pm2_5 levels from satellite observations based on Aerosol Optical Depth (AOD) for four cities in four African countries. Air pollution is a major environmental health risk globally, it contributes to 7 million premature deaths globally each year with developing countries being the most affected [World Health Organization (2021)](https://apps.who.int/iris/handle/10665/345329). <br/>
### Project Question
Can Sentinel 5P data be used to predict air quality around Africa for environmental justice?<br/>
### Evaluation Metrics
The performance of the air quality prediction models will be evaluated using Root Mean Squared Error (RMSE), Mean Absolute Error (MAE) and R-squared.<br/>

## Findings
• The dataset contains 8,071 rows and 80 columns. It is multi-dimensional dataset with numerous environmental variables.<br/>
• The data covers 4 countries: Nigeria, Kenya, Burundi, and Uganda. It includes 4 cities: Lagos, Nairobi, Bujumbura, and Kampala. This indicates a focus on urban air quality in East and West Africa.<br/>
• PM2.5 is the main air quality indicator,  with levels ranging from 1.2 to 456.19 μg/m³. Other pollutants measured include sulphur dioxide, carbon monoxide, nitrogen dioxide, formaldehyde, and ozone.<br/>

#### Target variable (pm2_5) has values skewed to the right
![image](https://github.com/user-attachments/assets/363d9613-45c5-4f5a-afb7-c511cc70c7e2)

#### The target variable (pm2_5) has some outliers
![image](https://github.com/user-attachments/assets/ca089942-919a-4192-8db3-9a9a6fcf95ea)

####  Correlation heatmap of target varaible (pm2_5) and other variables
There are weak positive and negative associations between pm2_5 and other variables 
![image](https://github.com/user-attachments/assets/c0a85596-d5b7-40fc-b843-baaa24cef81d)

#### Original distribution of pm2_5 and log transformed pm2_5
The original distribution of PM2.5 is heavily right-skewed, indicating a long tail of high values. The log transformation effectively reduces the skewness in the data, making the distribution more bell-shaped. 
![image](https://github.com/user-attachments/assets/7e93c29a-3628-47e1-9e4b-28184aad2ec2)


Key variables to consider including alongside pm2_5_log for model building:
• Carbon monoxide, nitrogen dioxide, sulphur dioxide, and ozone levels
• UV aerosol index and layer height
• Cloud fraction and height
• Geographical factors (longitude, latitude)
• Temporal factors (month)

#### Comparing Light Gradient Boost Model and Random Forest Regressor model Root Mean Square Error 
![image](https://github.com/user-attachments/assets/122b759b-d466-433b-85d0-46f387f0abaf)
LGBM1  -  Dataset with 70% of values not missing. <br/>
LGBM2 - Dataset with 50% values not missing. <br/>
RFR1 -  Dataset with 70% of values not missing. <br/>
RFR2 -  Dataset with 50% values not missing. <br/>

LGBM1<br/>
Local RMSE: 0.3478497379628386 
Local MAE: 0.24050128990859415 
Local R-squared: 0.694571147219366

LGBM2<br/>
Local RMSE: 0.34265949605616375 
Local MAE: 0.2373739664155015 
Local R-squared: 0.7036177139370208

RFR1<br/>
Local RMSE: 0.38267975647796953 
Local MAE: 0.2569106204011341 
Local R-squared: 0.6303440698535643

RFR2<br/>
Local RMSE: 0.3751721482918112 
Local MAE: 0.2541770240920235 
Local R-squared: 0.6447059945584902


## Conclusion 
Light Gradient Boost Model was able to predict air quality around Africa using Sentinel 5P satellite data. It had the lowest RMSE and MAE, highest R-squared value compared to Random Forest Regressor. This indicates that the LGBM model  made predictions closer to the actual values as it captured the underlying patterns in the data more effectively.
