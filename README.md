# EPS Extraction from SEC EDGAR Filings

## Overview
This project involves parsing and extracting Earnings Per Share (EPS) data from a set of SEC EDGAR filings in HTML format, specifically focusing on quarterly EPS data for companies. This task simulates a real-world scenario where the extracted financial data is required to be structured for further analysis or reporting.

The primary goal of this project is to develop a robust parser that can navigate the complexities of SEC filings, handle varied formats, and output EPS data reliably. This parser should not only work for the provided sample files but also generalize well to unseen filing formats.

## Project Description
Given a set of EDGAR filings (such as 8-K reports), the objective is to:
1. Parse each HTML file to locate and extract the quarterly EPS figure.
2. Prioritize specific types of EPS data, following defined rules:
   - **Basic EPS** is preferred over diluted EPS if both are present.
   - **GAAP EPS** is preferred over non-GAAP EPS if both are present.
   - **Net/total EPS** should be output if multiple EPS values are available.
3. Output a negative EPS value if it is represented in brackets (e.g., `(4.5)` should be output as `-4.5`).
4. Where EPS data is not available but "loss per share" information is present, output the loss per share as a negative EPS value.

The output is saved in a CSV format with two columns: `filename` (name of the filing) and `EPS` (extracted EPS value).

## File Structure
- `filings/`: Folder containing the HTML files for each EDGAR filing.
- `output/`: Directory where the generated CSV output will be saved.
- `parser.py`: Python script implementing the EPS extraction logic.
- `requirements.txt`: List of required libraries for running the script.

## Installation and Setup
1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd eps-extraction-project
   ```

2. **Install required packages**:
   It is recommended to use a virtual environment:
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   pip install -r requirements.txt
   ```

## Usage
To execute the parser and generate the output CSV file, run the following command:

```bash
python parser.py --input_folder filings/ --output_file output/eps_data.csv
```

### Output Format
The parser will generate a CSV file (`eps_data.csv`) with the following format:
```csv
filename,EPS
0001564590-20-019726.html,0.08
0000066570-20-000013.html,1.12
0000008947-20-000044.html,-0.41
0001564590-20-019431.html,1.08
0001564590-20-019396.html,-3.15
```

## Key Extraction Rules
1. **EPS Type Priority**:
   - Basic EPS is preferred over diluted EPS.
   - GAAP EPS is prioritized over non-GAAP EPS.
   - When multiple EPS values are present, output the net or total EPS value.
   
2. **Negative EPS**:
   - EPS values enclosed in brackets should be interpreted as negative (e.g., `(4.5)` is `-4.5`).

3. **Loss Per Share**:
   - If EPS is absent, but "loss per share" data is available, output it as a negative EPS value.

## Project Submission
To submit the project, include the following:
- The `parser.py` script.
- The output CSV file containing EPS data for all 50 provided filings.
- A brief description of your approach and any assumptions made during development.

## Assessment Criteria
The parser will be evaluated based on:
1. **Accuracy**: Correctly extracting and prioritizing EPS data per the outlined rules.
2. **Adaptability**: Handling variations in filing formats and generalizing to unseen formats.
3. **Efficiency**: Processing multiple files in a performant manner.

## License
This project is proprietary to Trexquant Investment LP. Redistribution of this project or its contents is strictly prohibited without prior written consent from Trexquant.
