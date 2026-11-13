# Python Video Post-Production Workflow and Reporting Tool

## Overview

Developed a Python-based video post-production workflow tool that processes Xytech work-order data and Baselight export information, matches video files and frame ranges, and generates organized reports. The application uses MongoDB to store source records and provides command-line functionality to process matching data, convert frame numbers into timecodes, generate video clips and thumbnails, and export results.

The project was designed to simplify the process of organizing post-production work orders and matching video files to the corresponding locations and frame ranges.

## Technologies Used

- **Python** – Application logic, data processing, and command-line functionality.
- **MongoDB** – Database storage for Xytech and Baselight export records.
- **PyMongo** – Python integration with MongoDB.
- **FFmpeg** – Video processing, clip extraction, and thumbnail generation.
- **FFprobe** – Retrieving video information, including duration.
- **Pandas** – Organizing and processing matched data.
- **XlsxWriter** – Generating Excel reports.
- **CSV** – Importing source data and exporting reports.
- **Frame.io Client** – Optional integration for uploading processed media to Frame.io.
- **Argparse** – Command-line argument parsing and execution.

## Key Features

### 1. Source Data Import

- Reads Xytech work-order information from `Xytech.txt`.
- Reads Baselight export information from `Baselight_export.txt`.
- Stores source records in MongoDB collections.
- Supports separate command-line options for importing each source.
- Provides options to print stored Xytech and Baselight records.

### 2. Baselight and Xytech Data Matching

- Matches Baselight file paths and frame information with corresponding Xytech work-order locations.
- Organizes matching records by their associated work-order information.
- Groups consecutive frames into frame ranges.
- Produces structured matched data for reporting and video processing.

### 3. Frame and Timecode Processing

- Converts frame numbers into timecodes using a 24 FPS frame rate.
- Processes frame ranges associated with matched video files.
- Supports command-line options for displaying and processing frame information.

### 4. Video Processing

- Uses FFprobe to retrieve video duration information.
- Uses FFmpeg to generate video thumbnails.
- Extracts video clips based on the matched frame ranges.
- Supports processing matched records from the database.

### 5. Report Generation and Export

- Exports matched information into CSV format.
- Generates an Excel report named `matched_data.xlsx`.
- Supports additional CSV exports, including `matched_data.csv`, `file_contents.csv`, and `videoFile.csv`.
- Organizes matched work-order, file, and frame information into report outputs.

### 6. Frame.io Integration

- Includes an optional Frame.io integration.
- Supports uploading media to Frame.io through the Frame.io client.
- Requires a valid Frame.io access token and asset ID to be configured before use.

## Database Structure

**Database:** `Project3database`

| Collection | Description |
|---|---|
| `Baselight_export` | Stores Baselight export records and associated file/frame information. |
| `Xytech` | Stores Xytech work-order and location information. |

## Example Usage

Import Baselight export data:

```bash
python comp467P3.py --insertBE
```

Import Xytech work-order data:

```bash
python comp467P3.py --insertX
```

Print Baselight export records:

```bash
python comp467P3.py --printBE
```

Print Xytech records:

```bash
python comp467P3.py --printX
```

Process and match the source data:

```bash
python comp467P3.py --process
```

Process matched data stored in MongoDB:

```bash
python comp467P3.py --processDB
```

Convert and process timecode information:

```bash
python comp467P3.py --timecode
```

Display frame information:

```bash
python comp467P3.py --frames
```

Export matched data to CSV:

```bash
python comp467P3.py --export
```

Export matched data to Excel:

```bash
python comp467P3.py --output
```

Export additional file information:

```bash
python comp467P3.py --exportEX
```

Export video file information:

```bash
python comp467P3.py --exportCSV
```

Run the optional Frame.io upload functionality:

```bash
python comp467P3.py --frameio
```

## Project Objective

The objective of this project was to develop a Python-based workflow for organizing and processing video post-production data. By integrating Xytech work orders, Baselight export information, MongoDB, and FFmpeg, the application matches source records to video files, processes frame ranges, and generates reports that help organize post-production tasks.

## What This Project Demonstrates

- **Database management:** Storing and retrieving Xytech and Baselight records using MongoDB.
- **Python scripting:** Building a command-line application with multiple processing workflows.
- **Data matching:** Connecting work-order locations with exported video file and frame information.
- **Video processing:** Using FFmpeg and FFprobe to inspect videos, generate thumbnails, and extract clips.
- **Timecode processing:** Converting frame numbers into timecodes at 24 FPS.
- **Data reporting:** Exporting processed information into CSV and Excel files.
- **External integration:** Implementing optional media upload functionality through Frame.io.

## Dependencies

Create a `requirements.txt` file with the Python packages used by the project:

```text
pymongo
pandas
xlsxwriter
frameioclient
```

Install dependencies with:

```bash
pip install -r requirements.txt
```

FFmpeg and FFprobe must also be installed and accessible from the command line for the video-processing features.
