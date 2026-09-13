# Car Pricing & Performance Analysis

**What drives the price of a car — and where does the market behave differently than expected?**

I analyzed 11,914 vehicles (Kaggle's *Car Features and MSRP* dataset, spanning model years 1990–2017) to answer a question that matters to anyone setting or evaluating car prices: which vehicle features actually justify a premium, and where does the market have segments that need to be priced differently?

---

## Business Problem

A manufacturer, dealership, or pricing team rarely has the luxury of setting prices by gut feel. They need to know: does a bigger engine reliably mean a higher price? Does transmission type affect fuel economy in a way that should factor into positioning? And critically — are there segments of the market (like electric vehicles or ultra-luxury cars) that break the normal pricing logic and need to be treated separately?

This analysis was built to answer exactly that, using real specification and pricing data across 47 brands.

## What I Did

- Profiled the dataset (11,914 rows, 16 features) and checked for missing data before drawing any conclusions
- Compared pricing and mileage across engine types, cylinder counts, and transmission types
- Identified the most common brands and vehicle styles in the market
- Measured the shape of six key features (Engine HP, Cylinders, MPG, Popularity, MSRP) using skewness, kurtosis, and IQR — not just to check a box, but to figure out *whether the outliers were real or noise*
- Visualized relationships with histograms, a correlation heatmap, and a scatter plot of horsepower vs. price

## Key Findings

**Engine size is one of the strongest, most reliable price drivers.** Average MSRP climbs steadily from ~$24K for 4-cylinder cars to ~$61K for 8-cylinder, and past $280K for 12-cylinder vehicles. This isn't noise — it's a consistent enough pattern that engine tier could reasonably anchor a pricing tier.

**Electric vehicles don't play by the same rules as gas cars.** Cars with "Direct Drive" transmission (a proxy for EVs in this data) post mileage figures over 100 MPG-equivalent — more than triple typical gas car mileage — and their pricing sits on its own curve entirely. Comparing them directly to combustion vehicles on price-per-mpg would be misleading.

**The outliers are the story, not noise to discard.** Every core feature I tested was right-skewed, with 5–8% of cars flagged as statistical outliers via the IQR method. When I dug into who those outliers actually were, they weren't data errors — they were genuine supercars (Bugatti, Ferrari, Lamborghini) and EVs sitting at the extreme end of a real market segment. Removing them from a pricing model would erase a legitimate part of the picture, not clean it up.

**"Popularity" measures buzz, not sales.** Ferrari ranks in the top 5 most "popular" brands in this dataset, alongside Ford and BMW — a brand that sells a tiny fraction of the volume. That tells me this metric reflects recognition or online interest, not units sold, which matters if anyone downstream tries to use it as a demand signal.

**Horsepower is the single strongest visual and statistical correlate of price** — confirmed by both the correlation heatmap and the HP-vs-MSRP scatter plot. If a business needed one variable to quickly ballpark a price, this is it.

## Recommendations

- Use engine size/performance tier as a primary axis for pricing segmentation — it's consistent and defensible across the dataset
- Model or report on EVs separately from gas vehicles; blending them distorts both mileage and price comparisons
- Don't strip outliers from this data before modeling — flag and study them, since they represent a real luxury/performance segment
- Treat "Popularity" as a brand-awareness metric, not a demand or sales proxy, in any downstream use

## What's Next

I'm building on this analysis with a price-prediction model (Linear Regression and Random Forest) trained on these same features, to see how much of MSRP can be explained by measurable specs alone — coming soon in this repo.

## Tools Used
Python · Pandas · Matplotlib · Seaborn · Jupyter Notebook

## Data Source
[Car Features and MSRP — Kaggle](https://www.kaggle.com/datasets/CooperUnion/cardataset)

