# Insights Summary

Key takeaways from each page of the Marketing & E-commerce Analytics Dashboard.

---

## 1. Executive Overview
- Revenue climbed from **$0.62M (Feb)** to a year-high of **$0.88M (Dec)**, with a sharp uplift in the final quarter.
- **Affiliate** is the top revenue channel (24.06%), followed by Paid Search (22.95%), Home-related channels (20.31%), and Email (18.x%).
- Funnel drop-off: **157.63K views → 36.3% click-through → 74.37% add-to-cart → 36.28% purchase**.
- **Affiliate campaigns drove the highest revenue** of any channel.
- The conversion rate from **Add to Cart → Purchase is 36.9%**, indicating strong purchase intent once users engage that deep in the funnel.

---

## 2. Campaign Analysis
- Campaigns generated **$6.68M** in attributed revenue with an average uplift of **8.67%**.
- **Affiliate** and **Paid Search** are the top two channels by revenue ($1.61M and $1.53M respectively), and Affiliate also sits in the best-performing quadrant of the Uplift-vs-Revenue scatter plot (high uplift *and* high revenue).
- Across objectives, **Reactivation** and **Retention** campaigns generated the most total revenue (₹19.55L and ₹18.15L respectively), suggesting existing-customer campaigns currently outperform pure acquisition spend.
- **Active Campaigns measure fix:** the original DAX measure had a date-comparison bug (`14-04-2023` was evaluated as arithmetic, not a date), which silently counted all campaigns instead of filtering. The corrected, dynamic measure (`end_date >= MIN(end_date)`) confirms all **50 campaigns** in the dataset are active, and will self-maintain if the dataset is refreshed. See [`dax/measures.md`][📊 View Insights Summary](Docs/Insights_summary.md) for the full fix.

---

## 3. Customer Insights
- Gender split is nearly even: **48.05% Male, 48.01% Female, 3.94% Other**.
- Age distribution peaks in the **30–40** range, indicating the core customer base skews toward early-career/established professionals.
- **Bronze tier (60,276 customers)** is by far the largest loyalty segment — more than double Silver (24,912), and far ahead of Gold (11,794) and Platinum (3,018).
- **To convert Bronze customers into Gold or Platinum**, a retention strategy is recommended — personalized marketing such as product recommendations based on past purchase or browsing behavior, delivered via email and notifications.
- The **United States (34,931 customers)** and **India (20,089)** are the two largest markets by customer count.

---

## 4. User Behavior & Event Analysis
- **View** is by far the dominant event (0.2M+ impressions), followed by Click, Add to Cart, Bounce, and Purchase in descending order.
- Session duration share is heavily weighted toward **View events (52.22%)**, with Click (19%), Add to Cart (14.08%), Bounce (9.52%), and Purchase (5.18%) trailing behind.
- Device usage is **desktop-dominant** across all months, ahead of mobile, tablet, and unknown device types.
- **Improvement strategy:** to increase total purchases, the checkout process should be simplified with no hidden charges, trust should be reinforced by encouraging customers to review their purchases, and **desktop optimization** is highlighted as a priority given the large volume of desktop traffic.

---

## 5. Product Performance
- **2,000+ products** generated **$8.37M** in revenue across **93K orders**, at an average price of **$72.17**.
- **Electronics dominates category revenue at 41.22%**, well ahead of Home (23.84%), Fashion (15.5%), Sports (11.53%), and Beauty (4.41%).
- **Brand_16** leads the Top 5 products by revenue, followed by Brand_6, Brand_70, Brand_56, and Brand_24.
- **Key insight:** since Electronics contributes disproportionately compared to other categories, a **cross-selling strategy** is recommended to lift revenue from the remaining underperforming categories.

---

## 6. Transaction & Geographical Revenue Analysis
- The **United States is the largest single market**, contributing **$3.0M in revenue from ~32K orders** — nearly double the next-largest market (India, $1.7M / 19K orders).
- **Refund Rate is 2.92%, well within the 5% target**, indicating healthy product and service quality.
- **Average Order Value is highest in the United Kingdom and United States** (~$91–92) and gradually declines across Brazil, Germany, Canada, and Australia (~$89).
- **Recommendation:** to grow revenue outside the US, increasing marketing campaign investment in the other six countries is suggested as the primary lever to attract more customers.

---

## Cross-Page Themes
- **Retention over acquisition:** Reactivation/Retention campaigns and Bronze-to-Gold loyalty conversion both point toward existing-customer engagement as the highest-leverage growth area.
- **Desktop-first behavior:** both the Product Performance and User Behavior pages support prioritizing desktop UX before mobile.
- **Category concentration risk:** Electronics' 41.22% share is a strength today but a diversification opportunity going forward via cross-selling.
- **Geographic headroom:** revenue is heavily US-concentrated; the other six countries represent the clearest expansion opportunity.
