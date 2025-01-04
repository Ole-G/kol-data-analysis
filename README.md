# KOL Data Analysis Automation Script

## Overview
This Google Apps Script automates the processing and analysis of Key Opinion Leader (KOL) data from multiple CSV files. The script provides a user-friendly interface through a custom menu in Google Sheets, enabling users to trigger the data analysis process with a single click. It processes CSV files from a designated Google Drive folder, applies filtering based on a reference database, and maintains a master KOL tracking sheet.

## Features
- Automated processing of multiple CSV files from a specified Google Drive folder
- Data filtering and cleaning using a reference database
- Smart column management with selective column retention
- Master KOL tracking sheet maintenance
- Real-time progress notifications via toast messages
- Latest data update reporting with date verification

## Prerequisites
- Access to Google Sheets
- Access to Google Drive
- A designated folder containing your CSV files
- A Google Sheet with the following structure:
  - "DB" sheet (containing reference data in column F)
  - "KOL data" sheet (for processed data storage)

## Setup
1. Replace the placeholder text [INSERT YOUR ID HERE] with your Google Drive folder ID
2. Ensure your Google Spreadsheet has the required sheets:
   - "DB" sheet with reference data in column F
   - "KOL data" sheet for the final processed data

## Usage
1. After installation, a custom menu "Аналітика" will appear in your Google Sheet
2. Select "Зібрати дані" to initiate the data analysis process
3. Progress updates will appear as toast notifications
4. Upon completion, you'll receive an alert with the latest data date

## Process Flow
1. Creates a temporary worksheet "Проміжні дані"
2. Imports data from all CSV files in the specified folder
3. Removes unnecessary columns, retaining only columns 1, 2, 3, 5, 7, 11, 12, and 13
4. Filters data based on matches in the "DB" sheet's column F
5. Transfers filtered data to the "KOL data" sheet
6. Removes the temporary worksheet
7. Identifies and displays the latest date from column G

## Error Handling
The script includes comprehensive error checking for:
- Missing or nonexistent sheets
- Empty data sources
- Date format validation
- Missing reference data

## Functions

### `onOpen()`
Establishes the custom menu interface in Google Sheets, creating an "Аналітика" menu with a "Зібрати дані" option.

### `analyzeKOLData()`
The main processing function that coordinates the entire analysis workflow, managing temporary sheets, data import, processing, and cleanup operations.

### `deleteUnnecessaryColumns(sheet)`
Manages column retention by preserving only specified columns (1, 2, 3, 5, 7, 11, 12, 13) and removing all others.

### `filterRowsBasedOnDB(allDataSheet, dbSheet)`
Implements data filtering by comparing imported data against the reference database in the "DB" sheet.

### `copyDataToKOLData(allDataSheet, kolDataSheet)`
Handles the transfer of processed data from the temporary worksheet to the final "KOL data" sheet.

## Notifications and User Interface
- All user interface elements are presented in Ukrainian
- Progress notifications provide real-time updates in Ukrainian
- The script uses a temporary sheet named "Проміжні дані" for processing
- All operations are automated to minimize user intervention

## Customization
To adapt the script for your specific needs, you can modify:
- The Google Drive folder ID placeholder
- The column retention list in deleteUnnecessaryColumns
- Sheet names if different naming conventions are preferred
- Notification messages if different language is needed

## Performance Considerations
The script maintains efficient performance through:
- Sequential file processing
- Batch operations for data reading and writing
- Temporary worksheet usage for processing
- Optimized column deletion sequencing

## Security Notes
- The script has been sanitized to remove sensitive information
- The folder ID is configurable through a placeholder
- No hardcoded sensitive data is included in the code

## Best Practices for Implementation
- Always backup your data before running the script
- Ensure your CSV files are properly formatted
- Maintain consistent data structure in your "DB" sheet
- Regularly verify the folder ID configuration
- Monitor process completion notifications
