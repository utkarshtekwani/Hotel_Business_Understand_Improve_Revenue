# Hotel Bookings Forecasting & Analytics Dashboard

This Power BI dashboard provides a detailed view of historical hotel booking behavior, cancellation patterns, no-show rates, booking lead times, and future demand projections. It is designed to support hotel managers in understanding demand dynamics, managing revenue risks, and making informed operational decisions.

## Forecasting Method

Forecasting is implemented using Power BI's native time series forecasting features.

- **Main forecast measure**: `Forecast Bookings Next Months` — estimates expected bookings for the upcoming period based on historical data from the Bookings table.
- **Headline forecast number**: Shows **810.02** expected bookings in the near future (displayed in a prominent card visual).
- Forecast performance is visualized in line + bar charts, comparing actual vs predicted bookings across Spring, Summer, and Winter seasons.
- The model reflects seasonal patterns and continues the directional trends seen in recent historical data.

## Cancellation and Lead Time Analysis

### Cancellations
- Measured monthly via `Sum of Cancellations by Month` (displayed as bars).
- Highest cancellation months: January (~20), July (~17), February (~15), March (~12).
- Presented both in absolute numbers and scaled percentages (with an 85–100% reference band for easier comparison).

### No-Shows
- **Average No-Shows per Month** (line chart): Shows a gradual improvement, dropping from ~1.4 early in the period to ~1.1 in more recent months.
- **Total No-Shows per Month**: Highest in January (~40), lowest in March (~28), with a slight increase to ~35 in July.
- **Daily No-Show Pattern**: Clear spike in the first 10 days of each month (up to 8 no-shows), then stabilizes at lower levels (typically 2–6) for the remainder.

### Booking Lead Time
- Compared between **Direct** and **OTA** channels using `Count of Lead_Time by Bookings and Booking_Channel`.
- Lead times increased noticeably early in the dataset (peaking around March), then dropped sharply in later months.
- Direct bookings generally show slightly longer lead times compared to OTA channels.

## Key Observations

1. **Improving No-Show Performance**  
   Average monthly no-shows are trending downward — a positive sign that may reflect stronger confirmation processes or better guest quality.

2. **Seasonal Demand Shape**  
   Bookings peak in Spring/Summer and are lowest in Winter. The forecast of ~810 bookings indicates this softening trend is likely to continue.

3. **Cancellations Concentrated in High-Demand Months**  
   January and July show the most cancellations — likely linked to peak season overbooking or price sensitivity.

4. **Rapidly Shortening Lead Times**  
   Customers are increasingly booking closer to arrival date across both channels. This reduces predictability and makes revenue management more challenging.

5. **Early-Month No-Show Concentration**  
   No-shows are significantly higher during the first ~10 days of each month — possibly tied to arrival day patterns or confirmation/payment timing.

6. **Forecast Slightly Conservative**  
   The forecast line appears flatter than the recent downward movement in actual bookings, suggesting the model may be under-weighting the latest trend.

## Business Recommendations

- **Handle Peak-Season Volatility**  
  High cancellation rates in January and July suggest the need for more conservative overbooking policies or stronger cancellation penalties during high-demand periods.

- **Adapt to Last-Minute Booking Trend**  
  Shorter lead times require agile pricing, last-minute offers, strong OTA partnerships, and real-time availability control.

- **Capitalize on Falling No-Show Rate**  
  Continue reinforcing practices that have driven this improvement (e.g. automated reminders, deposit requirements, better pre-arrival communication).

- **Prepare for Lower Demand**  
  The projected ~810 bookings signal potential occupancy challenges. Consider targeted promotions, off-season packages, or cost optimization in weaker periods (especially Winter).

- **Strengthen Direct Channel**  
  Longer lead times from direct bookings offer more predictability — maintain or increase incentives for direct reservations (loyalty benefits, exclusive rates).

- **Staffing & Operations**  
  Plan for higher uncertainty at the beginning of each month due to elevated no-show risk in the first 10 days.

The dashboard should be refreshed with new bookings data regularly to track whether the softening demand continues, stabilizes, or reverses, and to evaluate if forecast settings need adjustment.

**Data current as of**: July (based on the latest visible data in visuals)