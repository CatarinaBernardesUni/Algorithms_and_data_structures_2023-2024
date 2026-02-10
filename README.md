# Algorithms_and_data_structures_2023-2024
**Computation II – Algorithms & Data Structures (Group Project)**  
Spring Semester 2023/2024

## Project Overview
This project analyzes a sales dataset from a hypothetical Students’ Union (SU) using core concepts from **algorithms and data structures**. The goal is to extract meaningful customer insights, perform sorting and searching operations, and evaluate customer value using **RFM analysis** (Recency, Frequency, Monetary Value).

Each group works with a **unique dataset**, and all analysis is implemented in **Python**, following strict library and implementation constraints.

---

## Dataset Description
The dataset is provided as a **pickle (`.pkl`) file** and contains a list of dictionaries. Each dictionary represents a single purchase with the following fields:

- **Name**: Student name (string)
- **Date**: Purchase date in `DD-MM-YYYY` format (string)
- **Item**: Purchased item name (string)
- **Unit Price**: Price per item in euros (float)
- **Quantity**: Number of units purchased (int)

The dataset may contain inconsistencies or errors. These must be handled programmatically (no manual editing or hard-coded fixes).

---

## Technologies & Libraries
Only the following libraries are used, as required:

- Python built-in libraries
- `pickle`
- `numpy`
- `matplotlib`
- `timeit`
- `scipy.stats.spearmanr`

---

## Information Extraction
For each student, the following metrics are computed:

### Recency
- Number of days since the student’s **most recent purchase**
- Assuming **March 1st, 2024** as the current reference date

### Frequency
- Total number of purchases made by the student

### Monetary Value
- Total amount spent by the student across all purchases

### Visualizations
- Histograms for **recency**, **frequency**, and **monetary value** are generated using `matplotlib`.

---

## Sorting & RFM Analysis

### First RFM Score (RFM)
1. **Recency**
   - Students are sorted by most recent purchase.
   - Divided into 3 equal groups and scored: 3 (most recent) → 1 (least recent)

2. **Frequency**
   - Sorted by number of purchases (descending)
   - Scored from 3 to 1

3. **Monetary Value**
   - Sorted by total spending (descending)
   - Scored from 3 to 1

Each student receives a combined **RFM score (e.g., 333, 211, 111)**.  
Students are then sorted by their RFM scores to identify the most “valuable” customers.

---

### Second RFM Score (RFM’)
A hierarchical scoring approach:
1. Bucket students by **recency**
2. Within each recency bucket, rank by **frequency**
3. Within each frequency bucket, rank by **monetary value**

Each student again receives an RFM’ score.

### Correlation Analysis
- **Spearman Rank Correlation** (`scipy.stats.spearmanr`) is used to measure the correlation between **RFM** and **RFM’** rankings.

---

## Searching

### Linear Search
- Used to find the RFM scores of group members (or alternative names if missing).

### Binary Search
1. Students are sorted alphabetically.
2. Binary search is applied to find specific students.
3. Execution time is measured using `timeit`.

A performance comparison between **linear search** and **binary search** is provided.

---
