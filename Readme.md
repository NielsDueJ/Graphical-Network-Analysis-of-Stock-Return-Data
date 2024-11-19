# Unsupervised Learning: 
## Application of Graphical Network Analysis on Stock Returns Data

**Last Update:** July 24th, 2020

### Overview
This Jupyter Notebook demonstrates the application of **Graphical Network Analysis** on stock returns data using machine learning techniques. It combines Sparse Covariance Estimation, Clustering, and Manifold Learning to analyze and visualize the relationships between stocks based on their conditional dependencies.

### Key Features:
1. **Sparse Covariance Estimation**: Utilizes the Graphical Lasso method to estimate the precision matrix and infer conditional correlations.
2. **Clustering**: Implements Affinity Propagation to group stocks into clusters without requiring the number of clusters to be predefined.
3. **Manifold Learning**: Uses Multidimensional Scaling (MDS) to create a 2D embedding for visualizing the network.

The notebook processes historical stock data, calculates key financial metrics such as Sharpe Ratios and Maximum Drawdown, and generates insightful visualizations for understanding stock relationships across sectors.

---

### Instructions

#### **Before You Start**
- The notebook is designed for **illustration purposes**. Run the code blocks sequentially from start to finish.
- **Do not modify the code**, unless explicitly marked with **"CAN BE CHANGED"**. 
- Test the notebook with existing values in the **"CAN BE CHANGED"** sections before making adjustments.

#### **Setup**
1. Import the necessary Python packages and custom functions from `Graphical_Analysis_functions.py`.
2. Load and clean stock return data (from CRSP) and T-Bill data (from FRED) for analysis.

---

### Workflow

#### **1. Data Preparation**
- **Dataset Overview**: Stock return data includes 22 firms across four sectors: Bank, Health, Energy, and Tech.
- **Preprocessing Steps**:
  - Convert daily stock returns to weekly returns using the `resample` function.
  - Adjust T-Bill return data to weekly returns.
  - Save cleaned data for analysis.

#### **2. Summary Statistics**
- Key metrics include:
  - Total Return
  - Average Return
  - Annualized Average Return
  - Annualized Standard Deviation
  - Sharpe Ratio (using 3-Month T-Bill as the risk-free rate)
  - Maximum Drawdown
- Users can customize the time period and focus on specific firms or sectors.

#### **3. Graphical Network Analysis**
The algorithm uses three unsupervised learning techniques:
1. **Sparse Inverse Covariance Estimation**:
   - Identifies conditional correlations and constructs the graphical network.
2. **Affinity Propagation**:
   - Groups stocks into clusters based on similar behaviors.
3. **Manifold Learning**:
   - Visualizes the network in 2D using Multidimensional Scaling (MDS).

#### **4. Visualization**
- **Graphical Network Plot**:
  - Each node represents a stock, color-coded by its cluster.
  - Edges between nodes indicate conditional correlations, with edge strength defined by the precision matrix.
- **Zoom Functions**:
  - Focus on specific sectors or firms using `graphicalAnalysis_plot_ZOOM_bySector` and `graphicalAnalysis_plot_ZOOM_byFirm`.

---

### Customization Options
1. **Time Period**:
   - Specify `start_date` and `end_date` for analysis.
2. **Sectors**:
   - Use `Sectors_chosen` to analyze specific sectors (e.g., `['Bank', 'Tech']`).
3. **Firms**:
   - Exclude specific firms with `drop_firm` (e.g., `['FRC', 'RY']`).
4. **Output Settings**:
   - Enable or disable summary statistics and individual stock performance plots with `display_SumStat` and `display_IndRet`.

---

### Example Configurations

#### **Full Dataset Analysis**
```python
start_date = '2020-01-01'
end_date   = '2020-06-28'
Sectors_chosen = ['Bank', 'Health', 'Energy', 'Tech']
drop_firm = []
display_SumStat = True
display_IndRet = True
