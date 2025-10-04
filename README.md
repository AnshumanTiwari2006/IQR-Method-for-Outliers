🕵️‍♂️ Outlier Detection & Removal using the IQR Method
A robust, distribution-agnostic approach to clean skewed data using Interquartile Range (IQR)
✅ Works great for non-normal, right-skewed datasets like income!

🛠️ Tech Stack
<span>🐍 Python</span> • <span>🐼 Pandas</span> • <span>📓 Jupyter</span> • <span>📈 Matplotlib</span> • <span>🎨 Seaborn</span>

📌 Overview
This project demonstrates a statistical, non-parametric method to detect and handle outliers in real-world datasets using the Interquartile Range (IQR) technique. Unlike mean- and standard deviation-based methods, IQR is resistant to skewness — making it ideal for financial or income-type data.

The included Jupyter Notebook walks you through:

📊 Visualizing data with histograms & box plots
📐 Calculating Q₁, Q₃, and IQR
🚧 Defining outlier boundaries using the 1.5 × IQR rule
🧹 Applying two handling strategies:
Trimming: Remove outlier records
Capping (Winsorization): Replace outliers with boundary values
🔍 Comparing before vs. after distributions
📥 Installation
Install the required Python libraries using pip:

pip install pandas numpy seaborn matplotlib

💡 Tip: Use a virtual environment to avoid dependency conflicts!

📁 Dataset
File: Outlier.csv
Target Column: income (numerical, right-skewed)
Skewness: ≈ 1.027 → confirms positive (right) skew
💰 Income data often contains extreme high values — perfect for IQR-based cleaning!

📐 IQR Method Explained
The Interquartile Range (IQR) is the spread between the 25th and 75th percentiles:

IQR = Q₃ − Q₁

Outliers are defined as values outside these statistical fences:

Upper Limit = Q₃ + 1.5 × IQR
Lower Limit = Q₁ − 1.5 × IQR
🔢 Calculated Boundaries for income
For the income column, we computed the following statistical thresholds using the IQR method:

Q₁ (25th percentile): 32,752.5
Q₃ (75th percentile): 115,406.5
IQR (Interquartile Range): 82,654.0
Upper Limit (Q₃ + 1.5 × IQR): 239,387.5
Lower Limit (Q₁ − 1.5 × IQR): −91,228.5
⚠️ Since income values cannot be negative in this context, only data points above 239,387.5 are treated as outliers.
⚠️ Since income can't be negative, only upper outliers exist in this dataset!

🧹 Outlier Handling Techniques
1. ✂️ Trimming (Removal)
Remove rows where income exceeds the upper limit.

Outliers detected: 77 rows
We create a new DataFrame by keeping only rows where income is within the calculated limits:
df_changed = df[(df['income'] < upper_limit) & (df['income'] > lower_limit)]

❌ Pros: Simple
❌ Cons: Reduces sample size — may lose valuable data

2. 🧢 Capping (Winsorization)
Replace extreme values with boundary limits — preserves dataset size!

We assign a new column in the DataFrame using nested np.where logic:
df_new['income'] = np.where(
&nbsp;&nbsp;&nbsp;&nbsp;df['income'] > upper_limit,
&nbsp;&nbsp;&nbsp;&nbsp;upper_limit,
&nbsp;&nbsp;&nbsp;&nbsp;np.where(
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;df['income'] < lower_limit,
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;lower_limit,
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;df['income']
&nbsp;&nbsp;&nbsp;&nbsp;)
)

✅ Best practice for ML pipelines — avoids data loss while taming extremes!

📈 Visualization Results
The notebook includes a 2×2 comparison grid:

📦 Before: Box plot with long upper whiskers & outlier dots
📏 After: Clean box plot — outliers removed or capped
📊 Before: Right-skewed histogram
📉 After: More symmetric, model-friendly distribution
✅ Result: Cleaner data → more stable models and reliable insights!

🚀 Ready to Run?
Clone this repo
Install dependencies
Open Outlier_Detection_IQR.ipynb in Jupyter
Run cells and explore!
📬 Feedback & Contributions
Found a bug? Have an idea?
👉 Open an issue or submit a PR! All contributions welcome! 🤝
