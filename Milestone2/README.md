## Revenue and Occupancy Metrics 
1. REVPAR_NEW = DIVIDE( [Room Revenue],  [Rooms Available] )
2. Occupancy = DIVIDE([REVPAR_NEW], [ADR], 0) 
3. ADR was already given to us and we calculated these terms 'REVPAR_NEW' and 'Occupancy'.
4. Value of REVPAR_NEW is 1.32M , Occupancy average is 680.

## Guest classify
1. Guest by classified using guest_country,booking_duration and booking channel
2. Through that we know bookings are of direct or ota, from which country and also how much duration of each category.

## Segmentation
1. Based on customer_id if the customer id is repeating then its loyal
2. If its new id then first visit and if the repeatation is greater than the number 10 then its high spender.


## Key insights and observations
1. Maximum guest are from USA.
2. Bookings are more done through the OTA.
3. Ratio of bookings through season is almost near to 1. 

