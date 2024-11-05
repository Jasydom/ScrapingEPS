# EPS Extraction Project - README

## Overview

This project is designed to extract **Earnings Per Share (EPS)** data from a set of financial HTML files using **web scraping** and **regular expressions (regex)**. The goal is to develop a reliable method for identifying EPS data in financial reports.

## Methodology

### 1. Initial Approach

At the beginning of the project, I explored different approaches:
- I initially consulted **ChatGPT**, which recommended using **regex** as a possible solution.
- I researched various **Natural Language Processing (NLP)** tools such as **Named Entity Recognition (NER)** with **SpaCy** and **Hugging Face**, but they were not suitable for this task.
- I also looked into scraping financial data from **Yahoo Finance**, but it was not directly relevant to my project.

### 2. Web Scraping Approach

I chose to use **BeautifulSoup** for scraping the HTML data and **regex** for identifying and extracting the EPS information. My steps were as follows:
- **HTML Parsing**: I converted each HTML file into a BeautifulSoup object.
- **Table Extraction**: I focused on extracting financial data from the tables in the HTML files.
- **Regex Application**: I applied regex to identify and extract the EPS values.

The extracted values were then converted from strings to floats and saved into a CSV file for further analysis.

### 3. Development Process

#### Step 1: Build Initial Regex Patterns
I started by building regex patterns based on a sample output file (`output_example.csv`). These initial patterns were expanded to cover the remaining 50 HTML files.

#### Step 2: Data Extraction Using Regex
- I added more regex patterns to handle variations in how EPS was represented in the data.
- The **order of regex patterns** was important for ensuring accurate matches.
- The extracted EPS values were stored in CSV files.

### Results

I generated two main output files:
1. **output_eps_data.csv**: This version contains more regex patterns and has fewer errors.
2. **output_eps_data_v3.csv**: This version contains fewer regex patterns (reduced from 31 to 5), but it has more errors as the simplified regex approach did not capture all variations.

### Challenges and Limitations

- **Multiple Regex Patterns**: I relied on a large number of regex patterns, which I reduced in version 3, but this introduced more errors.
- **Unsuccessful EPS Extraction**: I was unable to extract EPS values from the following files:
   - `0000046080-20-000050.html`
   - `0001104659-20-053563.html`
- **Exploring Alternative Methods**: I may explore other approaches to better understand HTML structures and possibly train a model using **Hugging Face** for more accurate extraction.

### Future Work

- **Optimize Regex Patterns**: I plan to further reduce the number of regex patterns while maintaining accuracy.
- **Explore ML Solutions**: I may experiment with training a model to extract EPS values more effectively.
- **Improve Accuracy in Version 3**: Although version 3 reduced the number of regex patterns, I need more time to address the errors it introduced.

---

## Project Structure

### Code Structure:
1. **Library Imports**: Import necessary libraries such as `BeautifulSoup`, `re`, and `pandas`.
2. **Function Definitions**: Functions are defined for HTML parsing, table extraction, and EPS extraction using regex.
3. **Testing Code on Sample Articles (5 Articles)**: Code is first tested on a small sample to ensure the extraction process works correctly.
4. **Processing All 50 Articles**: The code is then extended to handle the full set of 50 HTML files.
5. **Generalizing Regex Patterns**: In version 3, the regex patterns were generalized to reduce the total number of patterns.

---

## Files

- **output_eps_data.csv**: Contains more regex patterns and fewer errors.
- **output_eps_data_v3.csv**: Contains fewer regex patterns but more extraction errors.


## Conclusion

This project demonstrates how **web scraping** and **regular expressions** can be used to extract financial data from HTML reports. While regex-based extraction works well in many cases, there are limitations, particularly when dealing with diverse HTML structures. Future efforts will focus on refining the regex patterns and exploring alternative methods for more robust extraction.
