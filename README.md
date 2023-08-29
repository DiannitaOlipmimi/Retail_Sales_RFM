# Retail_Sales_RFM

**User Segmentation on Customer Shopping Dataset**


**🌏User Segmentation**

dalam bisnis, setiap user memiliki karakteristik yang berbeda. karakter-karakter ini dapat dikelompokan berdasarkan kemiripannya. dengan pengelompokan ini dapat selanjutnya dilakukan tindakan yang lebih tepat sehingga user tidak meninggalkan platform (churned)

terdapat beberapa segmentasi yang umum digunakan

- geografi (lokasi/wilayah)
- demografi (umur/jenis kelamin)
- budaya (terkait event suku)
- kebiasaan (habit user)

**🌏RFM Analysis**

salah satu bentuk user segmentasi berdasarkan kebiasaan. RFM menggunakan 3 karakteristik yaitu kebiasaan transaksi dimana:

- Recency (kebaruan)
- Frequency (seberapa sering)
- Monetary (value uang)

**⛳Deskripsi Masalah:**

Welcome to the shopping world of Istanbul! Our dataset contains shopping information from 10 different shopping malls between 2021 and 2023. We have gathered data from various age groups and genders to provide a comprehensive view of shopping habits in Istanbul.

**⛳Tujuan:**

The objective of RFM analysis is to segment and understand customer behavior based on their purchase history. RFM stands for Recency, Frequency, and Monetary Value. By analyzing these three key factors, businesses can gain valuable insights into their customer base, identify high-value customers, tailor marketing strategies, and enhance customer retention efforts.

## 📌Table of contents
- [Dataset dan Variabel]()
- [Result]()
- [Links]()


## 🧵Data dan Variabel:

**📒Dataset:**
 The dataset includes essential information such as invoice numbers, customer IDs, age, gender, payment methods, product categories, quantity, price, order dates, and shopping mall locations. We hope that this dataset will serve as a valuable resource for researchers, data analysts, and machine learning enthusiasts who want to gain insights into shopping trends and patterns in Istanbul. Explore the dataset and discover the fascinating world of Istanbul shopping!

| invoice_no | customer_id | gender | age | category | quantity | price   | payment_method | invoice_date | shopping_mall  |
| ---------- | ----------- | ------ | --- | -------- | -------- | ------- | -------------- | ------------ | -------------- |
| I138884    | C241288     | Female | 28  | Clothing | 5        | 1500.4  | Credit Card    | ########     | Kanyon         |
| I317333    | C111565     | Male   | 21  | Shoes    | 3        | 1800.51 | Debit Card     | ########     | Forum Istanbul |
| I127801    | C266599     | Male   | 20  | Clothing | 1        | 300.08  | Cash           | ########     | Metrocity      |
| I173702    | C988172     | Female | 66  | Shoes    | 5        | 3000.85 | Credit Card    | ########     | Metropol AVM   |
| I337046    | C189076     | Female | 53  | Books    | 4        | 60.6    | Cash           | ########     | Kanyon         |

**📒Variabel:**

- `invoice_no`: Invoice number. Nominal. A combination of the letter 'I' and a 6-digit integer uniquely assigned to each operation.
- `customer_id`: Customer number. Nominal. A combination of the letter 'C' and a 6-digit integer uniquely assigned to each operation.
- `gender`: String variable of the customer's gender.
- `age`: Positive Integer variable of the customers age.
- `category`: String variable of the category of the purchased product.
- `quantity`: The quantities of each product (item) per transaction. Numeric.
- `price`: Unit price. Numeric. Product price per unit in Turkish Liras (TL).
- `payment_method`: String variable of the payment method (cash, credit card or debit card) used for the transaction.
- `invoice_date`: Invoice date. The day when a transaction was generated.
- `shopping_mall`: String variable of the name of the shopping mall where the transaction was made.

## 🧵Result

**Analysis**

✅ Recency Calculation:

Calculate the time gap between the most recent purchase date and the current date for each customer.
Assign a recency score based on recency values, with higher scores for more recent purchases.

✅ Frequency Calculation:

Count the total number of transactions for each customer.
Assign a frequency score based on transaction counts, with higher scores for more frequent buyers.

✅ Monetary Value Calculation:

Calculate the total monetary value of all transactions for each customer.
Assign a monetary score based on monetary values, with higher scores for higher spending customers.

✅Segmentation:

Create segments by combining the scores from the recency, frequency, and monetary value calculations.
For instance, customers with high recency, frequency, and monetary scores could be labeled as "Champions."

✅ Results and Insights:
Based on the RFM analysis, customers are segmented into various groups, such as:

- Champions: Customers with recent, frequent, and high-value purchases.
- Loyal Customers: Frequent buyers who may not have made a recent purchase.
- Potential Loyalists: Recent buyers who need encouragement to become more frequent shoppers.
- At-Risk Customers: High spenders who haven't made recent purchases.
- Dormant Customers: Infrequent buyers who made their last purchase a while ago.

**Actionable Insights:**

- Champions could receive exclusive offers or loyalty rewards to maintain their engagement.
- Loyal Customers might be targeted with upsell offers or loyalty programs.
- Potential Loyalists could be encouraged to make more purchases with limited-time promotions.
- At-Risk Customers may be re-engaged with special discounts to prevent churn.
- Dormant Customers could receive reactivation campaigns to bring them back.

**Benefits:**

- Targeted marketing efforts tailored to specific customer behaviors.
- Improved customer retention and engagement.
- Increased ROI on marketing campaigns by focusing on segments with higher potential.
- By applying RFM analysis to the retail data, "TrendyStyles" gains a - granular understanding of its customer segments, allowing them to optimize their marketing strategies and enhance overall customer satisfaction and loyalty.


## 🧵Links

📊 Kaggle Dataset

https://www.kaggle.com/datasets/mehmettahiraslan/customer-shopping-dataset

