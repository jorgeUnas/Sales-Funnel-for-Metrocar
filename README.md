# Sales Funnel for Metrocar

<p align= "center">
<img src="https://github.com/jorgeUnas/Sales-Funnel-for-Metrocar/blob/main/logo.jpg" height="200"> 
</p>

## Summary
The user ride activity data from Metrocar (a ride-sharing app similar to Uber) was manipulated and organized to obtain the sales funnel for users who downloaded the app in 2021. I determined the customer stages that did not perform as expected and provided some recommendations to improve them. The data was manipulated using **`SQL`**, and the funnel was designed in **`Tableau`**. The final Tableau dashboard can be easily interpreted by any stakeholder to make data-driven decisions.

<a> [Video Presentation](https://drive.google.com/file/d/1576YoDvIjJ6fX3c5hFb9RWOMPAWaMXw5/view?usp=sharing) </a>

<a> [Tableau Dashboard](https://public.tableau.com/app/profile/jorge.humberto.unas.daza3556/viz/Metrocar-funnel-analysis/Story1?publish=yes) </a>

## Context
Video presentation
Metrocar is interested in analysing its sales during 2021 to increase its revenue and user engagement for the upcoming years. Part of its business strategy is to identify the most frequent consumers, the platforms they use the most, and establish a dynamic pricing model to stimulate drivers to get on the road and increase their earnings. Additionally, I have created two sales funnels to identify the stages with the most drop-offs and can suggest recommendations to stakeholders.
The data collected is condensed in the ERD of Figure 1. There are no missing values in this dataset, and each column contains the correct data type. Null values correspond to missing timestamps, for example, drop-off timestamps for rides that were not completed.

My strategy to address the company's request was to reduce the amount of data by aggregating the dataset at the user-level granularity using SQL, thereby facilitating the visualization of the sales funnel in Tableau. Reducing the size of big datasets sacrifices granularity, but in some cases, there is no need for a high level of detail to drive data decisions, as is the case here, where grouped data can provide enough information to track sales effectively.
The user funnel includes the following stages:

**`Downloads`**: The count of app downloads from the App Store or Google Play Store.
**`Sign-up`**: The number of accounts created on the app (assuming each account belongs to a unique user). Ride Request: The number of users who open the app to request a ride.
**`Ride Completed`**: The number of users who get in the car and ride to their destination.
**`Review`**: The number of users who leave a review to share their ride experience.
Additionally, I have established a ride funnel using the number of rides in the following stages:
**`Ride Request`**: The number of rides requested.
**`Driver Acceptance`**: The number of rides accepted by the drivers.
**`Ride Completed`**: The number of rides where users get in the car and reach their destinations. Payment: The number of rides with an approved payment status.
**`Review`**: The number of rides reviewed.

## Results
The query used to aggregate the dataset at the user-level granularity is attached as a separate file (main_query.sql). The Figure 2 shows a segment of the table generated by this query. This table contains a reduced dataset with 105 rows and is organized by funnel stages, making it relatively easy to interpret.

With this reduced dataset, I have created a Tableau dashboard that can be found here. Paired bar plots were implemented to obtain the funnel shape using the count (COUNT()) of users or rides to construct each type of funnel. In addition to the funnel, I have included treemaps to showcase the number of users or rides by platform and age range. Finally, I present an individual bar plot to analyze the hours with the highest number of ride requests, with the intention of establishing a simple price-surging strategy.
### User Funnel
This funnel describes the user journey from the moment they download the app to the moment they make a review sharing their ride experience (Figure 3).

The biggest drop-offs in this funnel occur between download and sign-up and between ride request and ride completed. The first drop-off of users is practically unavoidable because a considerable number of people download the app just to take a look at the layout. Some of them are current users of other similar apps like Uber or Lyft and simply want to compare how user-friendly this app is compared to others. Additionally, some people install the app in emergency situations but end up using other transportation means, such as taxis. This drop-off could be slightly reduced by modifying the landing page of the app, perhaps by utilizing A/B testing to launch appealing features like banners or pop-ups with promotions and discounts.
On the other hand, the drop-off between ride request and ride completed represents users who requested at least one ride, canceled it, and never completed a ride. These users were not engaged with the app, and some of them may have uninstalled it. This drop-off can be correlated with several factors, such as long waiting times for users, a lack of drivers at specific times, drivers rejecting rides, or bugs in the app.
According to the treemap (FIgure 4), most of Metrocar's users use iOS devices to install the app, and the majority of them are between 35 and 44 years old. This age range is also the most common among users on other platforms. This behavior is expected because these individuals use ride apps more frequently for commuting to their workplaces compared to younger people (18-24 years old), and they rely more on technology than previous generations (people in the 45-54 age range).

### Ride Funnel
Figure 4.
I found it interesting to design a special funnel that describes the trajectory of the rides from the moment they are requested to the moment they are reviewed (Figure 5), allowing us to identify stages where we are experiencing significant drop-offs in the number of rides.

Looking at the rides funnel, we discovered that the biggest drop-off occurred between rides requested and rides accepted. Two main factors can lead drivers to cancel rides frequently: low-fare rides and traffic congestion. The second factor does not depend on Metrocar, but the first can be reduced using a price-surging strategy. This strategy consists of increasing the price of the rides temporarily during times of high demand. In the Figure 6, we can see that the hours with the most ride requests were between 8 and 9 and between 16 and 17. This gives us an idea of the best hours to increase the prices and stimulate the ride-sharing options included in the app. Evidently, more sophisticated machine learning
models could address this goal in a more dynamic way, but this is a good starting point to increase sales and encourage drivers to complete more rides.

When it comes to the platforms and age ranges (Figure 7), I observed a similar behavior in the number of rides compared to the behavior in the number of users in Figure 4. Most of the rides are requested on iOS devices by users between 35 and 44 years old. Consequently, they are our target group, and I recommend keeping them engaged with excellent customer service and creating engaging content such as promotions or ride suggestions. This recommendation can be extended to users between 25 and 34 years old because this is the next group with the highest number of rides, and we could stimulate this group to use our app more frequently, thereby increasing our revenue as a result.

## Recommendations
● I recommend using A/B testing to implement modifications on the landing page, such as launching banners or pop-ups with promotions and discounts, in order to increase our user conversion rate.
● To reduce the number of users who sign up but never complete a ride, we could study how to mitigate factors like long waiting times for rides, lack of drivers at specific times, drivers rejecting rides, or bugs in the app.
● A price surging strategy could decrease the number of rides that are not accepted by drivers and, consequently, are not completed. This approach offers drivers the possibility to earn more during times of high demand, keeping them engaged with the app.
● Since users aged between 35 and 44 who use iOS devices are the most frequent and also the ones who request the highest number of rides, we should treat them as our target audience. Additionally, we could explore the possibility of increasing the number of rides in other age groups, such as users between 25 and 34, with the aim of increasing our revenue.


## Annexes
The bar plot was obtained from the following query:

