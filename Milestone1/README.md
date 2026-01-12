## Dataset Description

The dataset contains **daily hotel operations, revenue, marketing, and cost data**.  
It is designed to analyze:

- **Occupancy trends** – room usage patterns across weekdays, weekends, and seasons.  
- **Revenue performance** – total revenue, ADR, RevPar, and profit metrics.  
- **Guest behavior** – bookings, cancellations, no-shows, guest type, and country.  
- **Profitability and costs** – fixed costs, variable costs, and overall profit.  

The dataset combines **booking activity, guest segmentation, marketing spend, and financial metrics** to enable **data-driven decision-making** and **insights for hotel management**.

## Modelling Steps


### Step 1: Create the Bookings Table
1. Duplicated the original **Hotel_book** table to create **Bookings Table**.  
2. Removed unnecessary columns: `Profit`, `RevPar`, `Total Costs`, and `Room_Revenue_All`.

---

### Step 2: Calculate Key Metrics
3. Added **Profit** column: `[Total_Revenue] - [Total_Costs]`.  
4. Added **RevPar** column: `[ADR] * [Occupancy_Rate]`.  
5. Added **ADR_Managed_Guests** column: `[RevPAR_Managed_Guests] / [Occupancy_Managed_Guests]`.  
6. Added **Total Costs** column: `[Variable_Costs] + [Fixed_Costs]`.  
7. Added **ADR_All** column: `[RevPAR_All] / [Occupancy_All]`.  
8. Changed type and rounded **ADR_All** and **ADR_Managed_Guests** to 2 decimals.

---

### Step 3: Indexing and Date Key
9. Added **Index Column** starting from 1 → renamed as `booking_id`.  
10. Added **date_key** column: `Date.Year([Date]) * 10000 + Date.Month([Date]) * 100 + Date.Day([Date])`.

---

### Step 4: Room and Guest Mapping
11. Duplicated `Reserved_Room` → renamed `room_id` → mapped values: 6→1, 7→2, …, 12→7.  
12. Duplicated `Guest Country` → renamed `country_id` → mapped France→F1, USA→U1, UK→UK1, Germany→G1, Spain→S1, Italy→I1.  
13. Duplicated `Guest Type` → renamed `guest_id` → mapped Business→B01, Leisure→L01.  
14. Merged `country_id` + `guest_id` → `hotel_id` (no separator).

---

### Step 5: Create Dimension Tables
15. Duplicated **Bookings Table** 4 times → created dimension tables:  
    - **Room Dimension** → keep `room_id` & `Reserved_Rooms`, remove duplicates.  
    - **Date Dimension** → keep `date_key` & `Date`, remove duplicates.  
    - **Customer Dimension** → keep `Guest_Type` & `Guest Country`, remove duplicates, add `customer_id` as index.  
    - **Hotel Branch Dimension** → keep `hotel_id`, remove duplicates, renamed as `Bin`.

---

### Step 6: Merge Dimension Tables
16. Merge **Customer Dimension** → left join on `guest_type` + `guest_country` → expand `customer_id`.  
17. Merge **Hotel Branch Dimension** → left join on `hotel_id` → replace original `hotel_id`.  
18. Merge **Date Dimension** → left join on `date_key`.  
19. Merge **Room Dimension** → left join on `room_id`.

---

### Step 7: Hotel Branch Mapping & Clean Up
20. Removed `Season` column from Bookings Table.  
21. Duplicated `Guest Country` → renamed `hotel_branch_id` → mapped USA→U01, France→F01, Germany→G01, Italy→I01, Spain→S01, UK→UK01.  
22. Created **Hotel Branch Dimension** table → keep `hotel_branch_id` & `Guest Country`, remove duplicates.  
23. Merged **Hotel Branch Dimension** → replaced original `hotel_branch_id`.  
24. Disabled loading for intermediate **Bin** table to optimize performance.

---

### Step 8: Final Checks
25. Verified all calculated columns: `Profit`, `RevPar`, `ADR`, `ADR_Managed_Guests`, `ADR_All`, `Total Costs`.  
26. Confirmed all relationships: `booking_id`, `customer_id`, `room_id`, `hotel_id`, `date_key`, `hotel_branch_id`.  
27. Bookings Table is now **ready for star-schema modeling and Power BI dashboards**.



## Key Observations – Hotel Bookings Dataset

1. **Count of Profit by Month (Line Chart)**  
   - Fewer transactions
   - Possible low season  


2. **Count of RevPAR by Month (Line Chart)**  
   - Drop in the same month confirms:
        Lower occupancy 

3. **Count of Guest Type by Guest Country (Donut Chart)**  
   - No single country dominates heavily
