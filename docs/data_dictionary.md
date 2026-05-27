# 📖 Data Dictionary — Amazon Sales Dataset

## Source File
`Amazon_Sales_data.csv`  
Rows: 1,717 | Columns: 11 | Date Range: 2010–2017

---

## Column Definitions

### Country
- **Type:** String  
- **Description:** The country where the order was placed or delivered  
- **Example Values:** `United States`, `India`, `Germany`, `Japan`, `Saudi Arabia`  
- **Total Unique Values:** 100+ countries across 7 regions

---

### Item Type
- **Type:** String  
- **Description:** Product category of the item sold  
- **Allowed Values:**

| Item Type | Description |
|-----------|-------------|
| Baby Food | Infant and toddler food products |
| Beverages | Drinks and liquid consumables |
| Cereal | Breakfast cereals and grains |
| Clothes | Apparel and garments |
| Cosmetics | Beauty and personal care products |
| Fruits | Fresh and packaged fruits |
| Household | Home and kitchen items |
| Meat | Fresh and packaged meat products |
| Office Supplies | Stationery and office consumables |
| Personal Care | Hygiene and grooming products |
| Snacks | Packaged snack foods |
| Vegetables | Fresh and packaged vegetables |

---

### Order Date
- **Type:** Date (`DD/MM/YY`)  
- **Description:** The date the customer placed the order  
- **Range:** January 2010 – December 2017

---

### Order ID
- **Type:** Integer  
- **Description:** Unique 9-digit identifier assigned to each order  
- **Example:** `669165933`  
- **Note:** Each row represents one unique order

---

### Order Priority
- **Type:** String  
- **Description:** Priority level assigned to the order, which determines shipping speed  

| Code | Priority | Expected Shipment |
|------|----------|-------------------|
| C | Critical | 1–5 days |
| H | High | 5–15 days |
| M | Medium | 15–30 days |
| L | Low | 30–60 days |

---

### Region
- **Type:** String  
- **Description:** Geographic sales region grouping of the country  
- **Allowed Values:**

| Region | Countries Included |
|--------|--------------------|
| Asia | India, Japan, Singapore, China, South Korea, and 27 more |
| Europe | UK, Germany, France, Italy, Spain, and 40 more |
| North America | United States, Canada |
| Australia and Oceania | Australia, New Zealand, Fiji, and 11 more |
| Central America and the Caribbean | Mexico, Honduras, Jamaica, and 18 more |
| Middle East and North Africa | Saudi Arabia, UAE, Egypt, and 16 more |
| Sub-Saharan Africa | South Africa, Nigeria, Kenya, and 44 more |

---

### Sales Channel
- **Type:** String  
- **Description:** Whether the sale occurred through an online or offline channel  
- **Allowed Values:** `Online`, `Offline`

---

### Ship Date
- **Type:** Date (`DD/MM/YY`)  
- **Description:** The date the order was dispatched for delivery  
- **Rule:** Always >= Order Date  
- **Gap Logic:** Determined by Order Priority (see above)

---

### Total Cost
- **Type:** Float (2 decimal places)  
- **Description:** Total cost of goods for the order (Unit Cost × Units Sold)  
- **Unit:** USD  
- **Example:** `933903.84`

---

### Total Revenue
- **Type:** Float (2 decimal places)  
- **Description:** Total revenue generated from the order (Unit Price × Units Sold)  
- **Unit:** USD  
- **Rule:** Always > Total Cost (ensures positive profit)  
- **Example:** `1158502.59`

---

### Units Sold
- **Type:** Integer  
- **Description:** Number of units of the product sold in the order  
- **Range:** 100 – 10,000

---

## Calculated Fields (Created in Tableau)

### Profit
```
[Total Revenue] - [Total Cost]
```
Net profit generated from each order in USD.

---

### Shipment Days
```
[Ship Date] - [Order Date]
```
Number of days between order placement and shipment. Used to calculate the Average Shipment Days KPI.

---

### Highlight (Window Calculation)
```
IF SUM([Profit]) = WINDOW_MAX(SUM([Profit])) 
THEN 'color' 
ELSE 'no color' 
END
```
Table calculation used to highlight the highest-performing bar in the Profit-Wise Region chart.

---

## Data Quality Notes

- Zero null values across all 11 columns
- All Ship Dates are after Order Dates (no negative shipment gaps)
- All Total Revenue values exceed Total Cost (no negative profit rows)
- Order Priority distribution is balanced: ~430 orders per priority level
- Sales Channel split is near-equal: Online (864) vs Offline (853)
