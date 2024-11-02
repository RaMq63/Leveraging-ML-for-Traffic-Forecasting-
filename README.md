# Leveraging-ML-for-Traffic-Forecasting-
The project uses Random Forest regression, with Gradient Boosting for comparison, on a 66,000+ row dataset from 5 key Middle Eastern cities (Riyadh, Dubai, Cairo, Doha, and Kuwait). It aims to support traffic managers and urban planners by optimizing traffic flow and reducing congestion, enhancing urban mobility in the region.

2.1. Data Acquisition
 
      The Traffic Index dataset obtained from kaggle, containing 66,639 rows and 9 columns, with 8 key features, including attributes such as TrafficIndexLive (real-time traffic index), JamsCount (number of traffic jams), JamsLength (length of traffic jams), TrafficIndexWeekAgo (traffic index from the previous week), TravelTimeHistoric (historical travel time), and TravelTimeLive (real-time travel time). Collected at hourly intervals across several cities in Saudi Arabia and the Middle East, including Cairo, this dataset provides a rich source of traffic-related data. This dataset can be merged with IBM weather data and vacation calendar, and can be analyzed to understand the reasons behind the traffic. Preprocessing steps will handle missing values, normalize continuous variables, and encode categorical data, preparing the dataset for effective traffic prediction modeling.
 
1. Index: The number of the row
2. City: The location where traffic data is recorded.
3. DateTime: The timestamp of each traffic measurement.
4. TrafficIndexLive: The current traffic congestion index.
5. JamsCount: The number of traffic jams at each recorded time.
6. JamsDelay: The total delay caused by jams
7. JamsLength: The cumulative length of all traffic jams.
8. TravelTimeHistoric: The historical average travel time.
9. TravelTimeLive: The live travel time.
 
    The dataset was generally well-structured, though some missing values required handling. Its comprehensive coverage across different cities and times made it suitable for building a predictive model, and no significant challenges were encountered during the acquisition but it took us a while to find a dataset with this quality.
  
2.2. Training Methodology
 
  Three models were trained to predict traffic congestion levels from our dataset.The main model will be Random Forest regression, chosen for its ensemble learning approach that improves prediction accuracy by leveraging multiple decision trees. In addition to Random Forest, Linear Regression and Gradient Boosting Regression models will be developed for comparison. These models will help ensure that the best algorithm is selected based on their performance on the traffic dataset.
 
2.3. Workflow
 
2.3.1 Data Preprocessing: The dataset will be cleaned and preprocessed to handle missing values, normalize continuous variables, and encode categorical features. Exploratory Data Analysis (EDA) will identify correlations and relationships between variables.
 
2.3.2 Model Development: Define and import for each model, then  start experimenting
 
2.3.3 Model Training: The three selected models will be trained on traffic data from Saudi Arabia and the Middle East to enable accurate predictions of future traffic conditions.
 
2.3.4 Evaluation: Compare The  Results of the three models using RMSE (Root Mean Square Error), MAE (Mean Absolute Error), and R-squared. And a comparison of the models' performance will be conducted to determine the most accurate model.
 
2.4. System Design
 
    The system was designed by using a backend that utilized Python scripts and Scikit-learn to implement Random Forest, Gradient Boosting, and Linear Regression models. Data preprocessing addressed missing values and transformed categorical city names into numerical formats. Evaluation metrics such as R², MSE, and RMSE were employed to compare model performance. While no external user interface was developed, a command-line script was created to prompt users for input, facilitating traffic predictions directly within the workspace.
 
3. Results
 
3.1. Data Preprocessing
 
● Missing values were found as 6 of the 11 cities had information of only 6 months. These cities had to be removed as they were incomplete.
● (Year, Month, Day, Hour) were extracted from the Datetime column.
● JamsDelay, JamsCount, JamsLength, TrafficIndexWeekAgo, and Time of Day columns had to be removed from the dataset as they were irrelevant.
● Cities names had to be turned into numbers. To make the input simpler and avoid one-hot encoding, city names were converted into numbers, which helped streamline the model's requirements
 
3.2. Exploratory Data Analysis (EDA)
 
      During EDA, we noticed that some cities have only data for 6 months as we plotted a graph to see how the traffic index differs from each city in different months. When we did so,  also that some cities had more results than other cities (as shown below):
 
Other findings from the EDA phase were:
 
● Higher Traffic Index In months of [August, September, October, November, December]
● Dubai & Jeddah have the highest total jams.
● Cairo has the Lowest Jams Delay.
● The traffic index is lower in the Month of [July] In all cities.
● The traffic index is lower on Friday in all cities as it is the weekend
(except Abu Dhabi & Dubai the lowest day is Saturday, later we found out that the weekend there is Saturday and Sunday which matches our findings).
● Most jams occur from 12 pm To 12 am.
● Average travel time is close to 1 hour In all cities.
● Cairo has the highest travel time with an average of 80+ Min
 
3.3. Modeling
 
     Three machine learning models were explored to predict traffic congestion levels: Random Forest Regressor, Gradient Boosting Regressor, and Linear Regression. Each model was evaluated based on Mean Squared Error (MSE) and R-squared to determine its predictive accuracy.
 
3.3.1 Random Forest Regressor:
This model is known for capturing complex data relationships.
It achieved the lowest MSE (29.21) and highest R-squared (0.86)
making it the most accurate model for this dataset.
 
            3.3.2 Gradient Boosting Regressor:
This model is effective in capturing data patterns.
had a higher MSE (55.49) and a lower R-squared (0.73)
indicating a slightly lower accuracy compared to Random forest Regressor, and equal MSE to Linear Regression
 
3.3.3 Linear Regression:
Used as a baseline model,
had the highest error MSE of 55.49 and THE LOWEST R-squared (0.39)
proving insufficient for modeling the dataset’s complexity.
 
Given its superior performance, the Random Forest model was selected as the final predictive model for the system, providing reliable traffic congestion predictions
 
3.4. User Interface
 
       While we did not create an external user interface for our system, we implemented a script that prompts users to input their data directly within the workspace. This approach allows users to enter the necessary parameters interactively, facilitating a smooth experience without the need for a separate graphical interface. By guiding users through the input process in this manner, we ensure that they can easily provide the required information for traffic predictions.
 
 
3.5. Testing and Improvements
 
The system was tested for accuracy and usability on test data, with key improvements implemented:
 
• Hyperparameter Tuning:
Adjusting model parameters, like tree depth, improved the accuracy of the Random Forest model.
• Enhanced Preprocessing:
Improved handling of missing values and feature creation optimized data quality for better predictions.
 
• Error Handling:  
User prompts and validation were added to ensure correct inputs, increasing reliability.
These refinements enhanced the system’s accuracy and usability, making it a reliable tool for traffic congestion prediction.
 
 
4. Projected Impact
 
4.1. Accomplishments and Benefits
 
      One of the significant achievements of this model is its capability to predict the traffic index for multiple cities using the available traffic index dataset. It has reached an impressive accuracy of 86%. Additionally, the model includes a valuable feature that enables users to check the congestion index in any city by simply inputting the city name, date, and specific time. This functionality greatly enhances the user experience by providing accurate and trustworthy information about traffic conditions. Consequently, our project could be particularly useful for logistics and delivery companies, researchers and urban developers, transport authorities, TMS developers, and commuters.
 
4.2. Future Improvements
 
      Future improvements to this project could significantly enhance its capabilities and user experience. Incorporating weather prediction data would allow the model to account for weather-related traffic variations, leading to more accurate forecasts. Additionally, assessing environmental impacts could help users understand how traffic patterns contribute to pollution and congestion, promoting more sustainable transportation choices. Integrating safety ratings for different routes would provide valuable insights into the safest travel options. Furthermore, including detailed data about city streets could refine the model's predictions, making them more context-aware. To enhance user interaction, we could implement a feature that allows users to input their starting point and destination, enabling the model to predict the best route based on traffic conditions and other factors. These enhancements would not only improve the model's predictive accuracy but also provide a comprehensive tool for urban mobility planning.
