# Excel/CSV Splitter with Pandas

This Jupyter/Colab notebook provides a Python script to split a large Excel or CSV file into two separate CSV files using pandas. By default, the first CSV contains the first 83,300 rows, and the second contains the remaining rows. The notebook is especially suited for Google Colab and will provide download links for the generated files.

## Features

- Upload an Excel or CSV file
- Split the file into two CSVs at a specified row (default: 83,300)
- Download links for both CSV files (in Colab)

## How It Works

1. **Upload** your Excel or CSV file (e.g., `83kLIST.csv`) to the Colab environment.
2. The script loads the file into a pandas DataFrame.
3. The DataFrame is split:
    - `first_part.csv`: First 83,300 rows (or specified count)
    - `second_part.csv`: Remaining rows
4. Both CSV files are saved, and download links are provided (Colab).

## Usage

1. Open this notebook in Google Colab or your local Jupyter environment.
2. Upload your file.
3. Update `excel_file_path` and row count as needed.
4. Run all cells.
5. Download the resulting CSV files using the provided links.

## Example

Suppose your input file `83kLIST.csv` looks like:

| email                    |
|--------------------------|
| prlrh@uhhg.org           |
| employment@sdcnt.com     |
| sales@colonialgc.com     |
| Craig@portageprinting.com|
| pgashbaugh@aol.com       |

- **first_part.csv**: Rows 0–83,299
- **second_part.csv**: Rows 83,300–end

## Sample Code

```python
import pandas as pd
from google.colab import files

excel_file_path = '/83kLIST.csv'  # Path to your file
split_row = 83300                 # Row at which to split

# Load the data
df = pd.read_csv(excel_file_path)

# Split the DataFrame
df_first_part = df.iloc[:split_row]
df_second_part = df.iloc[split_row:]

# Save to CSV files
df_first_part.to_csv('first_part.csv', index=False)
df_second_part.to_csv('second_part.csv', index=False)

# Provide download links (Colab)
files.download('first_part.csv')
files.download('second_part.csv')
