# Easy Fulfillment

### Introduction
An Order Fulfillment application. This application mocks the complete Order Fulfillment Operation. This application is 
intended to be used by Internal Teams to see the flow of packages in real time, to show the summary regularly,
to create new Fulfillment Stores near the places of interest, Suggests new fulfillment centers near customers where
a large amount of shipments.

___
### Features
1. Shows the Fulfillment Stores around the selected State
2. Showing the flow of Shipments in selected FS in real time
3. Generate Reports of Shipments for selected FS for given time frame
4. Suggest new FS near customers according to volume of order and time taken from the nearest FS
5. Suggest closing of FS based on volume order and time taken from the nearest FS
6. Inventory of Each Item, shipped by Seller. It is possible to inventory to deplete or no inventory at all for item
7. Upcoming feature is also possible based on future shipment Procurements
8. Upcoming Shipments to selected FS, also supporting filters by Sellers
9. Is delivery possible or not for a given pincode. This is done by finding if there is FS present in same district
10. Analyze and predict the time taken and Path followed when a shipment from seller to given FS
11. Analyze and predict the time taken and Path followed when a user orders something, and it is possible to
    reach the location
12. A single order by Customer can be divided into multiple parts internally to fulfill the quantity if one 
    FS is not enough. The final delivery is still done by consolidating the sub orders into final FS


___
### Endpoints for Integration
There is no authorization required. It is completely open
1. **GET** Real time data of chosen FS. This shows current number of items Grouped by Category. Separately
   grouped by Sellers
2. **GET** See the upcoming Seller Shipments in selected FS
3. **GET** Current Inventory of a Seller
4. **POST** Upcoming Shipment to Selected FS
5. **GET** Analysis and Prediction of Order of item from a Delivery Code. Can be used for estimation also with filters
6. **GET** Analysis and Prediction of moving Item between 2 FS
7. **GET** All FS in a State
8. **POST** Create Report of FS for given Time Frame
9. **GET** Suggested Closing of existing FS
10. **GET** Suggested Opening of new FS
11. **GET** Is delivery Possible for given PIN Code and given Item

___
### Some Assumptions
This list can be reduced as time and development goes on.

1. Each Airport is accessible by every other airport by direct flights
2. There is zero time to Packaging. As soon as order is placed it is possible to start delivery if conditions meet
3. The zero time in packaging allows **Same Day Delivery** possible as option.
4. **AS OF NOW ONLY CHATTISGARDH STATE IS SUPPORTED**. So all the shipments can only be stored to FS which is nearest to
   Airport
5. Each Fulfillment Center has unlimited Storage Space
6. Delivery is only possible within same District of FS
7. Delivery time is calculated for PIN CODE basis and not address basis 
8. Returns are not supported
9. No Cancel feature as of Now
10. Each FS should be named after nearest Airport
11. There are only Fulfillment Centers. No delivery hubs. This reduces complexity
12. There are unlimited Delivery Partners in each FS. As soon as Shipment comes, it is possible for customer delivery.
    **No time restriction on Delivery Partners**
13. The time taken from FS to pincode is predictable. Based on Distance between Pincode of FS and Delivery Pincode
14. Transportation between FS happens only between 10PM to 8AM. The speed is such that in that time, it is possible to
    reach the next FS in same night, and all the shipments are delivered, meaning unlimited Storage 
15. Transportation b/w FS starts at 10PM if any shipments, and the destination is always reached at sharp 8AM with 
    all goods
16. There is no time to unload. As soon as shipment reaches FS, the entries are updated instantly
17. From Airport to FS shipments can move at any time. Even during day. With unlimited capacity, the time
    is predictable with same formula as from FS to delivery location
18. All the distance are actually displacement. The time is predictable to cover the distance
19. If the destination PIN code is same as Source PIN Code then the time is always 1 unit. This is true for every type of
    delivery. Including FS to FS, Airport to FS, FS to Delivery location
20. There are no auto movements of goods between FS. The goods will remain in place forever in same FS as seller chose,
    till an Order is placed