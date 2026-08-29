# Matplotlib Learning Project

A hands-on Python learning repository focused on **data visualization with Matplotlib**, **CSV analysis with Pandas**, and supporting examples of **concurrency** (asyncio, threading, and multiprocessing).

This project is structured as a progressive learning portfolio: foundational charting practice, then applied analysis on a synthetic Netflix-style dataset, plus standalone scripts that demonstrate concurrent execution patterns in Python.

---

## Project Overview

| Area | What this repo demonstrates |
|------|-----------------------------|
| Visualization fundamentals | Line, bar, pie, histogram, scatter, and subplot charts in Jupyter |
| Applied data analysis | Loading, cleaning, and plotting a CSV dataset with Pandas + Matplotlib |
| Python concurrency | Practical scripts for `asyncio`, `threading`, and `multiprocessing` |

The visualization work lives in two notebooks:

- **`phase.ipynb`** — Matplotlib basics using small, hard-coded sample datasets
- **`project.ipynb`** — End-to-end charts from `netflix_dummy_data.csv`

The concurrency examples are separate runnable Python modules and are not wired into the notebooks.

---

## Key Learning Areas

- Core Matplotlib plotting APIs (`pyplot` and object-oriented `subplots`)
- Chart customization (titles, labels, legends, colors, markers, linestyles, grids, axis limits)
- Common chart types for categorical and numeric data
- Multi-panel layouts with `plt.subplot` and `plt.subplots`
- Reading CSV data with Pandas (`pd.read_csv`)
- Basic data cleaning (`dropna`, `str.strip`, `str.replace`, type conversion, categorical mapping)
- Aggregation and counting (`value_counts`) before visualization
- Concurrent programming patterns: async I/O-style waiting, threads, and process pools

---

## Technologies & Libraries

| Technology | Role in this project |
|------------|----------------------|
| **Python 3.13** | Runtime used by the notebooks (kernel metadata) |
| **Matplotlib** | All chart creation and styling |
| **Pandas** | CSV loading, cleaning, aggregation, and plotting helpers |
| **Jupyter Notebook** | Interactive exploration in `phase.ipynb` and `project.ipynb` |
| **asyncio** | Concurrent coroutine example (`async_example.py`) |
| **threading / concurrent.futures** | Threading vs sequential timing comparison (`thread_example.py`) |
| **multiprocessing** | Process pool, processes, and queue communication (`processing_example.py`) |

Standard library modules also used: `time`, `os`.

---

## Project Structure

```text
Matplotlib-Learning-Project/
├── phase.ipynb                 # Matplotlib fundamentals (sample data)
├── project.ipynb               # Netflix CSV analysis & visualizations
├── netflix_dummy_data.csv      # Synthetic subscription / viewing dataset
├── async_example.py            # asyncio.gather concurrency demo
├── thread_example.py           # threading & ThreadPoolExecutor demo
├── processing_example.py       # multiprocessing Pool / Process / Queue demo
└── README.md
```

---

## Files / Notebooks Overview

### Notebooks

| File | Purpose |
|------|---------|
| [`phase.ipynb`](phase.ipynb) | Step-by-step Matplotlib practice: line plots, bakery sales styling, bar chart, pie chart, histogram, scatter comparison, and subplots (both `subplot` and `fig, ax` styles). Uses hard-coded lists only—no CSV. |
| [`project.ipynb`](project.ipynb) | Applied analysis on `netflix_dummy_data.csv`: subscription counts, rating distribution, watch-hour histogram (with light cleaning), device vs subscription scatter, and side-by-side horizontal bar charts for country and subscription type. |

### Data

| File | Purpose |
|------|---------|
| [`netflix_dummy_data.csv`](netflix_dummy_data.csv) | Synthetic dataset with **300 rows** and **10 columns**. Date range: **2024-01-01** to **2024-10-26**. |

**Columns:** `Date`, `User_ID`, `Subscription_Type`, `Country`, `Watch_Hours`, `Genre`, `Device_Type`, `Monthly_Fee`, `Rating_Given`, `Renewed`

**Notable categorical values present in the file:**

- Subscription types: Basic, Standard, Premium  
- Countries: Australia, India, Canada, USA, UK  
- Genres: Drama, Romance, Thriller, Action, Sci-Fi, Comedy  
- Devices: Tablet, Laptop, Mobile, TV  
- Monthly fees: 199, 499, 649  
- Ratings: 1–5  
- Renewed: Yes / No  

### Python scripts

| File | Purpose |
|------|---------|
| [`async_example.py`](async_example.py) | Three async functions with different sleep times, run together via `asyncio.gather`, with total elapsed time printed. |
| [`thread_example.py`](thread_example.py) | Compares sequential execution, manual `threading.Thread` usage, and `ThreadPoolExecutor.map` for the same sleep-based tasks. |
| [`processing_example.py`](processing_example.py) | Three multiprocessing demos: `Pool.map` over 10,000 numbers, multiple `Process` workers printing PIDs, and `Queue`-based result collection. Includes `freeze_support()` for Windows. |

---

## Visualizations & Data Analysis

### `phase.ipynb` — Matplotlib fundamentals

| Chart | What it shows |
|-------|----------------|
| Line plot | Simple numeric series with markers |
| Styled line plot | Bakery sales by weekday (color, dashed line, markers, legend, grid, axis limits) |
| Bar chart | Product sales comparison (A–D) |
| Pie chart | Regional revenue share (North / South / East / West) |
| Histogram | Student score distribution (custom bins) |
| Scatter plot | Study hours vs productivity for two groups |
| Subplots | Prime-number series as stacked line + bar (`plt.subplot`) and side-by-side OO axes (`plt.subplots`) |

### `project.ipynb` — Netflix dummy data

| Chart | Data handling involved |
|-------|------------------------|
| Vertical bar chart | `Subscription_Type` counts after `dropna()` |
| Pie chart | `Rating_Given` value counts (sorted by rating) |
| Histogram | Country string clean-up (`strip`, replace `"USA"` → `"United States"`), `Watch_Hours` cast to `int`, then 10-bin histogram |
| Scatter plot | Maps `Device_Type` and `Subscription_Type` to numeric codes, then plots device vs subscription |
| Dual horizontal bar charts | `Country` and `Subscription_Type` value counts in a 1×2 subplot layout |

All notebook plots use Matplotlib’s interactive `plt.show()` flow (figures are generated in-session; this repo does not ship exported image assets).

---

## Python Concepts Demonstrated

- Importing and using third-party libraries (`matplotlib.pyplot`, `pandas`)
- Lists, dictionaries, and basic numeric / string data
- Functions and script entry points (`if __name__ == "__main__"`)
- Timing with `time.perf_counter()` / `time.time()`
- Pandas Series / DataFrame operations: `copy`, column selection, `map`, `astype`, aggregations
- Async coroutines (`async` / `await`, `asyncio.run`, `asyncio.gather`)
- Thread creation, joining, and thread pools
- Multiprocessing pools, processes, and inter-process queues

---

## Getting Started / Installation

### Prerequisites

- Python 3.10+ recommended (notebooks were run with **Python 3.13.5**)
- pip

### Setup

```bash
git clone https://github.com/SadiqCodex/Matplotlib-Learning-Project.git
cd Matplotlib-Learning-Project

python -m venv venv

# Windows
venv\Scripts\activate

# macOS / Linux
# source venv/bin/activate

pip install matplotlib pandas jupyter
```

There is no `requirements.txt` in the repository yet; the packages above match the imports used in the notebooks.

---

## Usage

### Run the notebooks

```bash
jupyter notebook
```

Then open:

1. **`phase.ipynb`** — work through Matplotlib chart types cell by cell  
2. **`project.ipynb`** — run cells in order (they read `netflix_dummy_data.csv` from the project root)

Keep the working directory at the repository root so `pd.read_csv("netflix_dummy_data.csv")` resolves correctly.

### Run the concurrency examples

```bash
python async_example.py
python thread_example.py
python processing_example.py
```

On Windows, prefer running `processing_example.py` as a script (not by pasting into an interactive session) because of multiprocessing’s process-spawn model; the file already calls `multiprocessing.freeze_support()`.

---

## Learning Outcomes

After working through this repository, you will have practiced:

1. Building and styling common Matplotlib charts from scratch  
2. Combining Pandas cleaning/aggregation with Matplotlib (and Pandas plot helpers)  
3. Exploring a multi-column CSV dataset through targeted visualizations  
4. Comparing sequential vs concurrent execution using asyncio, threads, and processes  

---

## Future Improvements

Ideas aligned with the current scope of the repo:

- Add a `requirements.txt` (or `pyproject.toml`) with pinned versions of Matplotlib, Pandas, and Jupyter  
- Extend `project.ipynb` with time-series plots over the `Date` column, genre breakdowns, or renewal analysis (`Renewed`)  
- Export selected figures to an `outputs/` folder for portfolio screenshots  
- Add brief markdown narrative cells in both notebooks explaining each chart’s intent  
- Unify concurrency demos with short commentary on when to choose asyncio vs threads vs processes  

---

## Author

**Sadik Mohammad** ([SadiqCodex](https://github.com/SadiqCodex))

Repository: [Matplotlib-Learning-Project](https://github.com/SadiqCodex/Matplotlib-Learning-Project)

---

*This repository is a personal learning / portfolio project documenting practical experience with Python visualization, CSV-based analysis, and concurrency fundamentals.*
