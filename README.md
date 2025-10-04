🕵️‍♂️ Outlier Detection & Removal using the IQR Method
A robust, distribution-agnostic approach to clean skewed data using Interquartile Range (IQR)
✅ Works great for non-normal, right-skewed datasets like income!

🛠️ Tech Stack
🐍 Python • 🐼 Pandas • 📓 Jupyter • 📈 Matplotlib • 🎨 Seaborn

📌 Overview
This project demonstrates a statistical, non-parametric method to detect and handle outliers in real-world datasets using the Interquartile Range (IQR) technique. Unlike methods based on mean and standard deviation, IQR relies on quartiles and is highly resistant to skewness — making it especially well-suited for financial or income-type data.

The included Jupyter Notebook guides you through a complete workflow:

📊 Visualizing the original data distribution using histograms and box plots
📐 Computing the first quartile (Q₁), third quartile (Q₃), and the IQR
🚧 Establishing outlier boundaries using the standard 1.5 × IQR rule
🧹 Applying two widely used outlier treatment strategies:
&nbsp;&nbsp;&nbsp;&nbsp;• Trimming: Removing records that fall outside the valid range
&nbsp;&nbsp;&nbsp;&nbsp;• Capping (Winsorization): Replacing extreme values with the nearest boundary limits
🔍 Comparing the data distribution before and after treatment to assess impact

📥 Installation
All required libraries can be installed via pip:

pip install pandas numpy seaborn matplotlib

💡 Tip: It’s recommended to use a virtual environment to keep dependencies isolated and avoid conflicts.

📁 Dataset
The analysis uses a dataset named Outlier.csv, with a focus on the income column — a numerical feature known for high skewness.

Skewness: Approximately 1.027
Interpretation: Strong positive (right) skew, typical of real-world income data
💰 Such distributions often contain extreme high-end values, making them ideal candidates for IQR-based outlier detection.

📐 IQR Method Explained
The Interquartile Range (IQR) measures the spread of the middle 50% of the data, calculated as the difference between the 75th percentile (Q₃) and the 25th percentile (Q₁).

Outliers are identified as any values falling below the lower fence or above the upper fence, defined as:

Upper Limit = Q₃ + 1.5 × IQR
Lower Limit = Q₁ − 1.5 × IQR
🔢 Calculated Boundaries for income
Using the dataset, the following thresholds were derived:

Q₁ (25th percentile): 32,752.5
Q₃ (75th percentile): 115,406.5
IQR: 82,654.0
Upper Limit: 239,387.5
Lower Limit: −91,228.5
⚠️ Since income cannot be negative in this context, only values exceeding the upper limit are considered outliers.

🧹 Outlier Handling Techniques

✂️ Trimming (Removal)
This approach removes all records where income lies beyond the statistical boundaries. In this dataset, 77 outlier records were identified and excluded.

❌ Pros: Simple and straightforward
❌ Cons: Reduces overall sample size, which may impact downstream analysis or model performance

🧢 Capping (Winsorization)
Instead of deletion, extreme values are replaced with the nearest boundary value — preserving the total number of observations while limiting the influence of outliers.

✅ Best practice for machine learning and statistical modeling, as it maintains data integrity without discarding records.

📈 Visualization Results
The notebook presents a side-by-side comparison of data distributions:

📦 Before treatment: Box plots show numerous high-end outliers; histograms reveal strong right skew
📏 After treatment: Outliers are either removed or pulled back to the boundary, resulting in a cleaner, more symmetric distribution

✅ The result is a refined dataset that supports more stable, accurate, and reliable modeling outcomes.

🚀 Ready to Run?
• Clone this repository
• Install the required dependencies
• Open Outlier_Detection_IQR.ipynb in Jupyter
• Execute the notebook to explore the full analysis

📬 Feedback & Contributions
Found an issue? Have a suggestion for improvement?
👉 Open an issue or submit a pull request — all contributions are welcome! 🤝
