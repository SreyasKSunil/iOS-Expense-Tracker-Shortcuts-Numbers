# iOS-Expense-Tracker-Shortcuts-Numbers
This project is an automated personal finance tracker built using  Apple Shortcuts for logging expenses  and Apple Numbers as a database and dashboard.
Apple Expense Tracker

Automation using Apple Shortcuts + Apple Numbers

Overview

This project is an automated personal finance tracker built using:

Apple Shortcuts for logging expenses

Apple Numbers as a database and a dashboard


Features:

One tap expense logging

Automated month and year detection

Dynamic dashboard

Pie chart per category

Monthly comparison chart

Clean raw database structure

Architecture:

Apple Shortcut → Numbers Table → Dashboard → Charts

File Structure

Expense_Tracker.shortcut

Expense_Tracker_2026.numbers

screenshots folder

How It Works
1. Data Logging

Shortcut collects:

Date

Paid At

Category

Payment Method

Amount

It writes data directly into the Raw_Data sheet.

No manual entry required.

2. Database Structure (Raw_Data Sheet)

Columns:

A. Date
B. Paid At
C. Category
D. Payment Method
E. Amount
F. Month
G. Year

Formulas:

In F2:

MONTH(A2)


In G2:

YEAR(A2)


Amount column formatted as Currency of your choice.

This sheet acts as the database. No totals here.

3. Dashboard Sheet

Control cells:

B1 = Selected Month
B2 = Selected Year

Changing these values updates:

Monthly total

Category summary

Charts

4. Monthly Total Formula
SUMIFS(Raw_Data::Amount;
Raw_Data::Month; B1;
Raw_Data::Year; B2)


Displays total spending for selected month.

5. Category Summary

Categories listed manually.

Formula:

SUMIFS(Raw_Data::Amount;
Raw_Data::Category; A2;
Raw_Data::Month; Dashboard::B1;
Raw_Data::Year; Dashboard::B2)


This powers the pie chart.

6. Monthly Comparison

Month list 1 to 12.

Formula:

SUMIFS(Raw_Data::Amount;
Raw_Data::Month; A2;
Raw_Data::Year; Dashboard::B2)


Used for column chart.

Shortcut Setup Guide
Step 1. Download the Shortcut Files

Clone the repository:

git clone https://github.com/SreyasKSunil/iOS-Expense-Tracker-Shortcuts-Numbers.git


Open the Numbers file.

Save it inside iCloud/iPhone.

Step 2. Install Shortcut

Open Expense_Tracker.shortcut.

Open the Shortcut file and make sure the 'Add to Number' section is correctly assigned to the table, sheet, and file.

Allow required permissions.

Ensure it writes to the correct Numbers file.

Step 3. Optional

Add Shortcut to Home Screen.

Add Siri phrase:
Log expense

Customization

You can:

Add more categories

Add income tracking

Add savings rate formula

Add yearly dashboard

Why This Design

Clean separation between data and dashboard

No duplicate files per month

Scalable structure

Works offline

No subscription tools

Future Improvements

Income tracking

Budget vs actual comparison

Auto recurring expenses

iPhone widget display
