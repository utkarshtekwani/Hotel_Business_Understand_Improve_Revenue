# Hotel Bookings Forecasting and Analysis Dashboard

This Power BI report analyzes historical hotel booking patterns, no-shows, cancellations, lead times, and generates forecasts for future bookings. It helps hotel management understand demand trends, revenue risks, and optimize operations.

## Forecasting Approach

The forecasting in this report uses Power BI's built-in time series forecasting capabilities (likely based on an exponential smoothing or similar statistical model provided by Power BI's analytics pane).

- **Forecast measure**: `Forecast Bookings Next Months` — projects bookings for the upcoming months based on historical patterns in the `Bookings` table.
- **Key displayed forecast**: A single aggregated value of **810.02** forecasted bookings for the "Next Months" period (visible in the card visual).
- The line + bar combination visuals compare actual bookings vs. forecast bookings across seasons (Spring, Summer, Winter), showing both historical actuals (orange/blue lines) and forecasted trends.
- Seasonality appears incorporated, as forecasts are segmented by Season and show continuation of downward/upward patterns observed in recent months.

## Cancellation and Lead-Time Analysis Logic

- **Cancellations**:
  - Calculated as `Sum of Cancellations by Month` (bar chart).
  - Highest in January (~20), followed by July (~17), February (~15), and March (~12).
  - Visualized both as absolute counts and percentage-scaled bars (85%–100% reference line for context).

- **No-Shows**:
  - Tracked via `Average of No-Shows by Month` (line chart): Shows a general declining trend from ~1.4 in early months to ~1.1 in later months.
  - `Sum of No-Shows by Month`: Peaked at ~40 in January, dropped sharply to ~28 in March, then rose slightly to ~35 in July.
  - `Sum of No-Shows by Day`: Daily pattern shows spikes (up to 8) in the first ~10 days of the month, then lower and fluctuating around 2–6 for the rest of the month.

- **Lead Time**:
  - `Count of Lead_Time by Bookings and Booking_Channel` (line chart): Compares Direct vs. OTA channels.
  - Both channels show an increase in lead time early in the period, peaking around March (~40 days?), then declining sharply afterward.
  - Direct bookings tend to have slightly longer lead times than OTA in most months.

## Key Insights Derived from Forecasting and Trend Analysis

1. **Declining No-Show Rate**: Average no-shows per month have decreased over time (from ~1.4 to ~1.1), which is a positive trend — possibly due to better confirmation policies or customer quality.
2. **Seasonal Booking Patterns**: Actual bookings show a downward trend across seasons (highest in Spring/Summer → lowest in Winter). The forecast (810.02) suggests this softening demand may continue into the next period.
3. **Cancellations Peak in Peak Seasons**: January and July (likely high-demand/winter-escape/summer periods) show the highest cancellations, indicating possible overbooking or price sensitivity.
4. **Lead Time Compression**: Lead times have shortened significantly in recent months for both Direct and OTA channels — customers are booking much closer to arrival, which increases forecasting uncertainty and last-minute revenue management challenges.
5. **Day-of-Month Pattern in No-Shows**: No-shows are noticeably higher in the first 10 days of each month — this could relate to weekend/weekday arrival patterns or payment/confirmation timing.
6. **Forecast vs Actual Gap**: The forecast line remains relatively flat while actuals are declining — indicating the model may not fully capture the recent downward momentum.

## Business Implications of Observed Patterns

- **Revenue Risk Management**: Higher cancellations and no-shows in January/July suggest over-optimistic initial demand — consider more aggressive overbooking strategies or stricter cancellation policies during peak periods.
- **Shift to Short Lead Times**: With bookings happening closer to stay dates, hotels should strengthen dynamic pricing, last-minute promotions, and real-time inventory adjustments (especially for OTA channels).
- **Positive No-Show Trend**: The declining no-show rate reduces revenue leakage — continue investing in confirmation emails, deposits, or pre-arrival communication.
- **Demand Softening Forecast**: The projected 810 bookings for next months (vs higher historical levels) signals potential occupancy pressure — proactive measures like targeted marketing, partnerships, or rate adjustments in weaker seasons (especially Winter) are recommended.
- **Channel Strategy**: Direct bookings show longer lead times → continue incentivizing direct channels (loyalty programs, best-rate guarantees) to secure earlier, more predictable demand.
- **Operational Planning**: Higher early-month no-shows imply staffing/cleaning adjustments should account for front-loaded uncertainty in the month.

This dashboard should be refreshed regularly with new data to monitor whether the downward trend persists or reverses, and to refine the forecasting model parameters if needed.

**Last updated**: Based on data up to July (as visible in visuals).