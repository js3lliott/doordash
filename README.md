# DoorDash Delivery Duration Prediction

In this project, the aim is to predict the total delivery time for DoorDash orders. When a consumer places an order on DoorDash, they are shown the expected time of delivery - it is very important that the service gets this time right as it has a big impact on consumer experience and can affect if they continue using the service or not. The time is calculated from when the consumer submits the order to when the order is delivered to the conusmer.

The dataset we have are deliveries made in 2015, and we will be creating a machine learning model to predict the total delivery time for new orders.

## Results

After pre-processing the data and performing some feature engineering, various regression models were trained with the best one being a combination of LightGBM and Linear Regression. The model achieved an RMSE of 986.70 seconds on the test data.

We can see through some analysis that the most important features for predicting the delivery time were the estimated order place duration and the estimated store to consumer driving duration.

## Limitations and Future Improvements

An obvious limitation to our approach is that we've only used data from 2015. If we want a more robust and up to date dataset, then we should be using data from 2015 until present day. Another limitation is that we only created a handful of new features stemming from the original duration and price features. What could be done in the future is add more features by aggregating values based on the most important features for our models. We can also improve our approach by performing hyperparameter tuning in an efficient and non-compute intensive way to achieve better results.

## Data Description

The dataset provided is `historical_data.csv`. Each row in the file corresponds to one unique delivery, and each column corresponds to a feature explained below:

- `market_id`: A city/region in which DoorDash operates, e.g., Los Angeles, given in the data as an id
- `created_at`: Timestamp in UTC when the order was submitted by the consumer to DoorDash. (Note this timestamp is in UTC, but in case you need it, the actual timezone of the region was US/Pacific)
- `actual_delivery_time`: Timestamp in UTC when the order was delivered to the consumer
- `store_id`: an id representing the restaurant the order was submitted for
- `store_primary_category`: cuisine category of the restaurant, e.g., italian, asian
- `order_protocol`: a store can receive orders from DoorDash through many modes. This field represents an id denoting the protocol
- `total_items`: total number of items in the order
- `subtotal`: total value of the order submitted (in cents)
- `num_distinct_items`: number of distinct items included in the order
- `min_item_price`: price of the item with the least cost in the order (in cents)
- `max_item_price`: price of the item with the highest cost in the order (in cents)
- `total_onshift_dashers`: Number of available dashers who are within 10 miles of the store at the time of order creation
- `total_busy_dashers`: Subset of above total_onshift_dashers who are currently working on an order
- `total_outstanding_orders`: Number of orders within 10 miles of this order that are currently being processed.
- `estimated_order_place_duration`: Estimated time for the restaurant to receive the order from DoorDash (in seconds)
- `estimated_store_to_consumer_driving_duration`: Estimated travel time between store and consumer (in seconds)

The target variable for our prediction task is the `actual_total_delivery_time`, which is the time between `created_at` and `actual_delivery_time`.


## Conclusion:

The project aimed to develop a machine learning model to predict delivery time for DoorDash orders using data from early 2015. After extensive pre-processing and feature engineering, a combination of LightGBM and Linear Regression was found to be the best model, achieving an RMSE of 986.70 seconds on the test data.

The analysis showed that the estimated order place duration and the estimated store to consumer driving duration were the most important features for predicting delivery time. However, there were limitations to the approach, including the use of only 2015 data and a limited number of newly engineered features.

To improve the model in the future, it would be beneficial to incorporate more recent data and generate additional features based on important predictors. Additionally, hyperparameter tuning can be performed more efficiently to obtain better results. Overall, the developed model provides a solid foundation for future development in predicting delivery times for DoorDash orders.