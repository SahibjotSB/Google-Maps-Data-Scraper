
---

# Google Maps Business Scraper

## Description
This script scrapes business details from Google Maps using Playwright. It extracts information such as business name, address, website, phone number, review count, review average, and coordinates. The data is saved in both Excel and CSV formats for further analysis.

---

## Features
- Scrapes business information from Google Maps.
- Handles duplicate entries by tracking unique URLs and names.
- Outputs data as sorted lists based on review average.
- Supports custom search queries and batch processing through an input file.
- Saves results in `output/` directory as `.xlsx` and `.csv`.

---

## Requirements

### Software
- Python 3.8 or higher
- Google Chrome or Chromium browser

### Python Libraries
Install required libraries using:
```
pip install playwright pandas
```

### Setting up Playwright
Run the following command to ensure browsers are set up:
```
playwright install
```

---

## Usage

### Running the Script
Run the script using the following command:
```
python script_name.py [-s SEARCH_QUERY] [-t TOTAL_RESULTS]
```

### Arguments
- `-s`, `--search`: A single search query (e.g., "restaurants in Toronto").
- `-t`, `--total`: Maximum number of results to scrape (default: 1,000,000).

### Batch Processing
To process multiple queries:
1. Create a file named `input.txt` in the script directory.
2. Add one search query per line.
3. Run the script without `-s`:
   ```
   python script_name.py
   ```

### Output Files
Scraped data is saved in the `output/` directory as:
- Excel: `google_maps_data_<query>.xlsx`
- CSV: `google_maps_data_<query>.csv`

---

## Example Commands

### Single Query
```
python script_name.py -s "cafes in New York" -t 50
```

### Batch Query
With `input.txt` containing:
```
cafes in New York
gyms in Los Angeles
restaurants in Toronto
```
Run:
```
python script_name.py
```

---

## Notes
1. **Coordinates Extraction**: The script extracts latitude and longitude directly from the Google Maps URL.
2. **Sorting**: Businesses are sorted by review average in descending order.
3. **Timeouts**: The script includes deliberate waits to accommodate Google Maps' loading times.

---

## Troubleshooting

1. **Playwright Setup Issues**:
   If you encounter errors during Playwright setup, ensure that `playwright install` is successfully executed.
   
2. **Duplicate Results**:
   The script skips duplicate business URLs and names.

3. **Google Maps Layout Changes**:
   If scraping fails, Google Maps' HTML structure might have changed. Update the XPath locators in the script.

---

## License
This script is for educational and personal use only. Ensure compliance with Google's terms of service when using this tool.

--- 
