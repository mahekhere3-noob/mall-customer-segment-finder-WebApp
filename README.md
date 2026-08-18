# Mall Customer Segment Finder Web App🛍️

A **K-Means clustering** model that groups mall customers into behavioral segments based on income and spending score — no labels, no "correct answer," just patterns the model finds on its own. Built with `pandas` and `scikit-learn`, with an interactive **Streamlit web interface**.

---

## 📊 Problem Statement

Can a model group shoppers into meaningful customer segments, just from income and spending behavior?

This project uses K-Means to cluster 100 mall customers based on their annual income and a 1-100 spending score, then lets a new customer's profile be classified into one of the discovered segments.

---

## 📁 Dataset

- **100** customers
- **Features:** Age, Annual Income (k$), Spending Score (1-100)
- **No target column** — this is unsupervised learning

---

## ⚙️ Approach

1. Load customer data into a pandas DataFrame
2. Standardize income and spending score with `StandardScaler` (they're on very different scales, and K-Means is distance-based)
3. Fit `KMeans` with 5 clusters
4. Label each cluster based on its income/spending pattern (e.g. high income + low spending → "Cautious High Earners")
5. For a new customer, scale their profile the same way and predict which segment they land in
6. Show a scatter plot comparing them to all 5 segments and a list of similar customers

---

## 🧠 Tech Stack

**Model:**
- Python 3
- pandas
- scikit-learn (`KMeans`, `StandardScaler`)
- Matplotlib

**Web Interface:**
- Streamlit

---

## 🚀 How to Run

```bash
git clone <your-repo-url>
cd mall-customer-segment-finder
pip install streamlit pandas scikit-learn matplotlib
streamlit run app.py
```

Enter an income and spending score, click "Find My Segment," and see which of the 5 customer groups you land in, plotted against everyone else.

---

## 📈 Result

The model finds **5 natural customer segments**:
- **Premium Customers** — high income, high spending
- **Budget-Conscious Big Spenders** — low income, high spending
- **Cautious High Earners** — high income, low spending
- **Budget Shoppers** — low income, low spending
- **Average Customers** — mid income, mid spending

A test profile (₹60k income, spending score 55) correctly lands in "Average Customers."

---

## 🔍 A Note on Unsupervised Learning

Like the Movie Taste Cluster Finder in this same series, there's no accuracy score here — no "right answer" to check the model against. It just finds structure in the data, and it's on us to interpret and name what that structure represents.

---

## 🔍 Limitations & Next Steps

- Trained on a small, synthetically generated dataset (100 customers), not real mall transaction data.
- The number of clusters (5) was chosen based on a prior Elbow Method analysis, not re-derived dynamically in this app.
- Segment labels are rule-based off income/spending thresholds and may not always match intuition perfectly.

**Planned improvements:**
- Bring in more features (age, visit frequency) and see if segments hold up or shift
- Re-run the Elbow Method live in the app instead of assuming K=5
- Add actual marketing action suggestions per segment

---

## 📝 Note

This project was built as a learning exercise in unsupervised clustering using scikit-learn.
