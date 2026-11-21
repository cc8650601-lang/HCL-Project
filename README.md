# Sample Superstore — Exploratory Data Analysis

## Student information

| Field | Details |
|---|---|
| Student name | Chirag Chauhan |
| Admission number | 2026B01010323 |
| Project | Exploratory Data Analysis (EDA) of Sample Superstore |
| Tools | Python, Jupyter Notebook, Pandas, NumPy, Matplotlib, Seaborn |

## Project overview

This project explores the Sample Superstore retail dataset. It inspects and cleans the data, calculates sales and profit metrics, compares performance across time and business segments, identifies potential outliers, and saves cleaned data and summary tables. The analysis is descriptive: observed correlations and discount patterns do not establish cause and effect.

## Project files

```text
stock market analysis/
├── data/
│   └── Sample - Superstore.csv
├── outputs/                       # Analysis results are saved here
├── Superstore_EDA.ipynb           # Notebook to run interactively in Jupyter
├── analyze.py                     # Reusable Python analysis source code
├── clean_superstore.py            # Separate CSV cleaning utility
├── requirements.txt               # Python package requirements
└── README.md
```

## Dataset source and attribution

The project uses the **Sample - Superstore** dataset, a fictional retail sales dataset distributed by Tableau for learning and visualization. Tableau describes it as containing product, sales, and profit information for a fictitious company. The official Tableau sample-data page is:

- [Tableau Public Sample Data](https://public.tableau.com/app/learn/sample-data)
- [Tableau help: Connect to a sample data source](https://help.tableau.com/current/guides/get-started-tutorial/en-us/get-started-tutorial-connect.htm)

The CSV currently included in this project is named `data/Sample - Superstore.csv`. The project copy does not contain download or version metadata, so its exact download date and intermediate download location cannot be verified from the file alone. For a formal submission, cite Tableau as the dataset publisher and retain the original download details if they are available to you.

## Objectives

1. Inspect the dataset structure, data types, missing values, duplicate rows, and numeric summaries.
2. Prepare date and numeric columns for analysis and remove exact duplicate records.
3. Create useful fields for order year, order month, shipping duration, and profit margin.
4. Calculate sales, profit, margin, order, customer, and shipping KPIs.
5. Compare results by category, region, sub-category, segment, and month.
6. Visualize sales trends, profit performance, discounts, and numeric correlations.
7. Flag unusual Sales and Profit values with the interquartile range (IQR) rule.

## Data cleaning and preparation

The analysis code performs the following preparation:

- Reads the CSV using `latin1` encoding.
- Parses `Order Date` and `Ship Date` as dates. Unparseable values become missing dates (`NaT`).
- Converts `Sales`, `Quantity`, `Discount`, and `Profit` to numeric values.
- Counts and removes exact duplicate rows.
- Adds `Order Year`, `Order Month`, `Shipping Days`, and row-level `Profit Margin` fields.
- Reports missing values and flags IQR outliers for review.

Missing values are not automatically filled, and outlier rows are not deleted. Negative profit values are retained because they represent losses in the data. These choices preserve the observations for analysis rather than silently changing them.

## Requirements

Python 3.9 or newer is recommended. Install the libraries from a terminal in the project folder:

```bash
python -m pip install -r requirements.txt
```

To use Jupyter Notebook if it is not already installed:

```bash
python -m pip install notebook
```

The required analysis packages are Pandas, NumPy, Matplotlib, and Seaborn. Their official documentation is linked below.

## Run in Jupyter Notebook

1. Open `Superstore_EDA.ipynb` in Jupyter Notebook or JupyterLab.
2. Confirm that `data/Sample - Superstore.csv` is present.
3. Run the notebook cells from top to bottom.
4. Review the tables and charts displayed inline. Exported CSV files are written to `outputs/`.

The notebook imports reusable functions from `analyze.py`. Keep both files in the project folder. If Jupyter reports a missing package, install the requirements above in the same Python environment used by the notebook kernel, then restart the kernel.

## Run the Python source from a terminal

From the project folder, run:

```bash
python analyze.py
```

To specify a different input CSV or output directory:

```bash
python analyze.py --input "path/to/Sample - Superstore.csv" --output outputs
```

The CSV should contain the standard Superstore fields used by the analysis, including order and ship dates, sales, profit, order and customer IDs, category, sub-category, and region.

## Outputs

Running the analysis creates or updates these files in `outputs/`:

- `cleaned_data.csv` — prepared rows, including derived fields.
- `kpis.csv` and `kpis.json` — key performance indicators.
- `category_summary.csv`, `region_summary.csv`, `subcategory_summary.csv`, `segment_summary.csv`, and `monthly_summary.csv` — grouped performance tables.
- `outliers.csv` — rows flagged as potential Sales or Profit outliers by the IQR method.
- `insights.txt` — a short summary of selected findings.
- `monthly_sales.png`, `category_and_region.png`, `subcategory_profit.png`, `discount_vs_profit.png`, and `correlation_heatmap.png` — saved chart images when running `analyze.py`.

The notebook displays its charts inline and saves the cleaned dataset and summary tables as CSV files. Running the terminal script also saves chart images and the text insight report.

## Analysis questions

- How do sales change over time?
- Which categories and regions have the highest sales or profit?
- Which sub-categories have the highest and lowest profit?
- How are discounts associated with order-line profit?
- Which records are flagged as potential Sales or Profit outliers?
- What are the total sales, total profit, overall profit margin, unique orders, and unique customers?

## Source code and learning references

The project code is written in Python for this analysis. The initial EDA outline was supplied in the project prompt and then organized into the notebook and reusable `analyze.py` workflow. No external article or third-party code repository is claimed as the source of the analysis code.

- [Pandas documentation](https://pandas.pydata.org/docs/)
- [NumPy documentation](https://numpy.org/doc/)
- [Matplotlib documentation](https://matplotlib.org/stable/)
- [Seaborn documentation](https://seaborn.pydata.org/)
- Dataset publisher: Tableau, linked in the [Dataset source and attribution](#dataset-source-and-attribution) section.

## Limitations

- The dataset represents a fictional sample business and should not be treated as real company performance.
- Results depend on the specific CSV version supplied with the project.
- Correlation and discount-versus-profit patterns are descriptive and do not prove causation.
- IQR outlier flags indicate unusual values for review; they do not, by themselves, mean the data is erroneous.
