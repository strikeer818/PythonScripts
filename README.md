# Python QA Testing and Database Reporting Tool

## Overview

Developed a Python-based QA reporting tool that imports, stores, analyzes, and exports software testing results using MongoDB. The application processes CSV test reports and provides command-line functionality to retrieve specific testing information, identify recurring bugs, track blocker issues, and generate organized reports.

The project was designed to simplify QA data management and make it easier to analyze test results across weekly reports and database records.

## Technologies Used

- **Python** – Application logic, data processing, and command-line functionality.
- **MongoDB** – Database storage and querying of QA test results.
- **PyMongo** – Python integration with MongoDB.
- **Pandas** – Data manipulation, filtering, and duplicate removal.
- **CSV** – Importing and exporting QA testing reports.
- **Argparse** – Command-line argument parsing and execution.

## Key Features

### 1. CSV Data Import

- Imports weekly QA reports and database dump files from CSV.
- Stores testing records in MongoDB collections.
- Supports verbose output to display imported records.
- Tracks the total number of records processed.

### 2. QA Test Result Filtering

Provides command-line queries to retrieve specific testing information:

- **Test Owner:** Retrieves all test cases assigned to a specific QA tester.
- **Repeatable Bugs:** Identifies bugs marked as repeatable.
- **Blocker Bugs:** Filters test cases identified as blocker issues.
- **Build Date:** Retrieves test reports associated with a specific software build date.
- Supports queries across both weekly reports and database dump collections.

### 3. Data Cleaning and Deduplication

- Uses Pandas to organize retrieved database records.
- Removes duplicate test cases based on test case descriptions, expected results, actual results, and test ownership.
- Excludes MongoDB internal document IDs from query results.

### 4. Test Case Reporting

- Retrieves the first test case, middle test case, and final test case stored in the database.
- Provides a quick overview of test records and database contents.

### 5. CSV Report Export

- Exports filtered QA test results into a structured CSV file.
- Supports exporting results based on test owner, repeatable bugs, blocker issues, and build dates.
- Generates a `report.csv` file containing relevant test information.

## Database Structure

**Database:** `Project2database`

| Collection | Description |
|---|---|
| `QA_WeeklyReports` | Stores weekly QA testing reports. |
| `DB_Dump` | Stores the complete QA testing database dump. |

Each test record contains information such as:

- Test Number
- Build Number
- Category
- Test Case
- Expected Result
- Actual Result
- Repeatable Status
- Blocker Status
- Test Owner

## Example Usage

Import weekly reports into MongoDB:

```bash
python comp467P2.py --QA_WeeklyReport weekly_report.csv --insert
```

Import database dump:

```bash
python comp467P2.py --DB_Dump DB_Dump.csv --insert
```

Find all test cases assigned to a specific tester:

```bash
python comp467P2.py --nameWR "Andrew Gabriel"
```

Find repeatable bugs:

```bash
python comp467P2.py --repeatWR
```

Find blocker issues:

```bash
python comp467P2.py --blockerDU
```

Retrieve reports from a specific build date:

```bash
python comp467P2.py --dateWR
```

Display the first, middle, and last test cases:

```bash
python comp467P2.py --report
```

Export filtered results to CSV:

```bash
python comp467P2.py --nameWR "Andrew Gabriel" --export
```

Display additional record counts:

```bash
python comp467P2.py --repeatWR -v
```

## Project Objective

The objective of this project was to develop a command-line QA reporting system that improves how software testing data is stored, retrieved, filtered, and analyzed. By integrating Python, MongoDB, and Pandas, the application provides an organized approach to managing QA test results and generating reports for software testing analysis.

## What This Project Demonstrates

- **Database management:** Working with MongoDB collections and querying structured testing records.
- **Python scripting:** Building an application with data-processing logic.
- **Test analysis:** Identifying repeatable defects and blocker issues.
- **Data validation:** Filtering and removing duplicate testing records.
- **Automation:** Using command-line arguments to execute different reporting operations.
- **Data reporting:** Generating CSV reports from database queries.

## Dependencies

Create a `requirements.txt` file with:

```text
pandas
pymongo
```

Install dependencies with:

```bash
pip install -r requirements.txt
```
