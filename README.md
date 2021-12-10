# AI

With the advent of environmental issues, not only companies and governments but also individuals’ effort has been emphasized. Still, it’s difficult to put into action due to not only insufficient will to act but also lack of real-life intimate measures. So as to solve the problem, we propose a practical solution that can shorten shower time to reduce carbon emission. Reducing 1 minute of shower for a year saves 4.3kg of CO2, which is the same as the carbon footprint 0.6 pine trees reduce. The method’s key function is to stimulate people to cut down their shower time by setting a limit of shower time. With AI speakers and smart mirrors, we check, alarm and present shower time to the user. Afterward, people can check the total amount of reduced carbon emission through the application. In terms of data, we need personal characteristics to present customized service. People can input their information into our application, including the age, sex, average number of shower per day, job of every member in the house. We predict every person’s shower time based on this personal information and the season using the regression models. With the predicted value, two things are decided; the alarm interval and target shower time. Through this, we aim to propose pro-environmental actions for individuals to reduce carbon emission.

🌍 Why ESG ?

Environmental problems and COVID-19, which have intensified around the world, are calling on companies to have a new success strategy in the era of uncertainty. Technology is recognized as a top priority for the safety and protection of mankind. Thus, the management paradigm of companies has shifted from growth-oriented to sustainable, pursuing on environment, society, and people rather than profits. This has established a management philosophy that decisions that harm the environment and society is inappropriate for stable corporate management. Since it is difficult to compare the level of sustainable management performance with financial information, ESG, a common criterion for objectively measuring and evaluating it, is used. Socially responsible investments are made through comparing ESG indicators between companies and businesses. For example, BlackRock, the world's largest asset management company, declared sustainability investments and sold all listed securities to companies with more than 25% sales generated from coal power generation. In modern society, climate risk is an investment risk, and capital is expected to be redistributed according to climate change. Therefore, our team started project planning at ESG, an important management evaluation index.

📈 In Korea

According to the Korea's 2050 Long-term Low Carbon Development Strategy Report, the government submitted a long-term low-carbon development strategy to the UN Climate Change Convention through extensive social discussions based on the 2050 Greenhouse Gas Reduction Goals and Challenges. According to a poll of 1,500 people proportionally allocated by applying regional, gender, and age population ratios conducted by Macromille Embrain, 90.5% said climate change was serious, with 52.7% of "increasing environmental pollution" and 46.3% of "increasing natural disasters and abnormal weather." In addition, 96.4% of the respondents said climate change will affect their lives over the next 30 years, and 93.2% of the respondents said Korea needs to consider achieving carbon neutrality with the goal of reducing greenhouse gases in 2050.

👨‍👩‍👧‍👦 Eco-friendly Home

The efforts of individuals as well as companies are emphasized in solving environmental problems. In modern society, where individuals' efforts to cope with global warming are not a matter of choice, but a matter of right, individuals are aware of the seriousness of the problem. Still, it is not easy to put it into practice due to lack of will and ignorance. However, in real life, individuals can reduce carbon emissions in a variety of ways. For instance, if the average shower time per person is reduced by one minute, annual CO2 emissions will be reduced by 4.3kg, the same effect as planting 0.6 pine trees. If it spreads to the whole country, it has the effect of planting 33.08 million pine trees every year, which is 68% of the Korea Forest Service's target tree planting in 2021. In addition, if the heating function of the electric rice cooker, which is used for an average of 9 hours a day, is reduced to an average of 4 hours a day, annual CO2 emissions are reduced by 142 kg. In addition, there are various solutions to environmental problems in real life, such as maintaining the proper amount of refrigerator, practicing recycling, adjusting the use of energy in each room, and using low-carbon products.

## Objective

Our team's service recognizes environmental problems in everyday life, proposes realistic ways to reduce carbon emissions, and helps users practice them. Users can check the group's average carbon emissions and reductions. Here, a group of people is a cluster of people who has the same gender and age. This group is the basis for action recommendation and its practice. Items which emits higher carbon emissions than the average of the group are presented to the user as recommended behavior. In this process, our team applied artificial intelligence to the [reduction of shower time] behavior recommendation function. Based on the personal data and weather data, a model that is trained for the prediction predicts the amount of shower time reduction (unit: seconds). And this time is set as the user's target reduction time. Additionally, the timer is linked to the smart mirror to help the user achieve the target shower time.

## Data Description

The data set consists of gender, age, occupation, shower duration, sleeping time, shower time, month, temperature, and reduction. It is based on 2020 census conducted by the National Statistical Office and a "your washing habit?" poll carried out by Doit Survey. In addition, the temperature reflects Meteorological Administration's climate statistics analysis. Data set consists of a total of 49,027 rows, and gender, age, and shower time data are proportionally allocated based on the researches as mentioned. We predicted based on a number of machine learning models targeting reduction, and calculated its effect by converting the predicted time to carbon emission reduction.

## Preprocessing

Train_test_split divided the entire data into training data, validation data, and test data. Then, those data are pre-processed using StandardScaler to convert the average of each feature to 0 and the variance to 1.

```python
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)
X_val = scaler.transform(X_val)
```

## Performance Evaluation Metrics

Since the target value is composed of continuous real value, regression analysis was performed and R-Squared, MAE, and RMSE were used as model evaluation indicators.

R-Squared

R-squared (R2) is a statistical measure that represents the proportion of the variance for a dependent variable that's explained by an independent variable or variables in a regression model. The closer to 1, the higher the prediction accuracy of the model.

MAE (Mean Absolute Error)

It is a value averaged by adding all the absolute values to the difference between the predicted and actual values and dividing them by the total number. The average of the differences between the predicted and actual values makes it easy to determine the degree of learning of the entire data. In terms of taking the absolute value, the difference value does not fluctuate significantly compared to MSE, so it has the advantage of roasting to outliers and the disadvantage of losing the direction of error. The closer to zero, the higher the prediction accuracy of the model.

RMSE (Root Mean Squared Error)

This is the value obtained by squaring the difference between the predicted and actual values, adding them all, and dividing them by the total number. RMSE's formula is the same as the standard deviation, and is implemented by applying square root to the MSE value. Like MAE, the closer to zero, the higher the prediction accuracy of the model.
