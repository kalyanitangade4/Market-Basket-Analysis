# 🛒 Market Basket Analysis
A data analysis project that mines grocery purchase records to uncover which products customers tend to buy together, and turns those patterns into concrete recommendations a merchandising or marketing team can act on.

## 📌 Problem Statement
Retailers want to answer a concrete question: if a customer buys product X, what else are they likely to buy? Rather than guessing at product placement and bundle deals, this project uses association rule mining to answer that statistically — identifying which item pairings occur together far more often than chance would predict.

## 🗂️ Dataset
The analysis uses the widely-used Groceries dataset (Kaggle), containing item-level purchase records with fields such as:
| Category | Example | 
| --- | --- |
| Fields | Customer |
| Member_number | Transaction Date |
| Product item | Description |
| Derived | TransactionID (reconstructed from Member_number + Date)|

~38,765 purchase records, 3,898 unique customers, 167 unique products, spanning Jan 2014 – Dec 2015.

## 🎯 Objectives
- Quantify which products are purchased most frequently and how purchase volume behaves over time.
- Reconstruct customer transactions and mine frequent itemsets using the Apriori algorithm.
- Generate association rules (Support, Confidence, Lift) to surface meaningful product pairings.
- Translate statistical patterns into plain-language, actionable merchandising recommendations.

## 🔍 Methodology
1. **Collect the data** – Load item-level purchase records (customer, date, product).
2. **Clean the data** – Parse dates, remove exact duplicate rows, and reconstruct transactions by grouping items bought by the same customer on the same date.
3. **Explore the data** – Look at top-selling products, basket size distribution, and purchase trends by month and day of week.
4. **Encode transactions** – Convert transactions into a one-hot basket matrix.
5. **Mine frequent itemsets** – Apply the Apriori algorithm with a low support threshold tuned to this dataset's small average basket size (~2.5 items).
6. **Generate association rules** – Filter on lift ≥ 1.0, then rank by lift and confidence to find the strongest product pairings.
7. **Summarize findings** – Turn the rules into simple, clear takeaways (e.g., "milk + yogurt buyers are 2x more likely to also buy sausage").
8. **Give recommendations** – Suggest practical merchandising and promotion actions based on what the data shows.

## 📊 Key Findings
- Sausage, yogurt, and whole milk form the strongest purchasing cluster. Customers buying whole milk + yogurt are over 2x as likely (lift 2.18) to also buy sausage compared to chance — and the reverse direction holds too.
- Citrus fruit ↔ specialty chocolate is a notable cross-category pairing (lift 1.65), suggesting a "treat" purchase pattern.
Tropical fruit ↔ flour (lift 1.62) hints at home-baking behavior.
- Best-selling items are not the most "associated" items. Staples like whole milk and vegetables show lift ≈ 1 with nearly everything — they're bought out of routine, not because of what else is in the basket.
- No strong weekly seasonality — purchase volume is steady across days of the week and months, simplifying inventory planning.
- Suggested next step: feed the mined rules into a "customers who bought this also bought…" recommendation feature, prioritizing the sausage/yogurt/milk and flour/tropical-fruit pairings for in-store placement tests first, since that's where the data shows the strongest signal.

## 📈 Visualizations Produced
Most purchased items (bar chart)
Monthly purchase volume trend (line chart)
Basket size distribution (histogram)
Purchases by day of week (bar chart)
Support vs. Confidence, sized/colored by Lift (bubble scatter)
Network graph of top item associations by lift
Lift heatmap among top 15 products

## 🛠️ Tools & Technologies
- **Language:** Python 3.x
- **Data Handling:** Pandas, NumPy
- **Association Rule Mining:** mlxtend (Apriori, association_rules)
- **Visualization:** Matplotlib, NetworkX
- **Environment:** Jupyter Notebook

## 💡 Business Recommendations
- **Cross-merchandising:** place sausage near the dairy aisle (milk/yogurt), and tropical fruit near baking supplies.
- **Bundle promotions:** a "breakfast bundle" (milk + yogurt + sausage) or "baking bundle" (flour + tropical fruit).
- **Recommendation engine seed rules:** the mined rules can directly seed a "customers who bought this also bought…" feature.
- **Don't over-promote staples together:** bundling milk with vegetables adds little incremental lift since customers buy both anyway.

## ✅ Conclusion
This analysis shows that co-purchase behavior isn't random — it concentrates around specific mid-frequency product clusters (sausage/yogurt/milk, fruit/flour) rather than around best-sellers. These are concrete, addressable levers for shelf placement and bundling, which is what makes the findings useful for a merchandising strategy rather than just a descriptive report.

## 👨‍💻 Author
Kalyani Tangade B.Tech IT Graduate | Aspiring Data Analyst Mumbai, India kalyanitangade4@gmail.com
