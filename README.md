# Automated E-Commerce Order Processing and Exception Handling

An automated order orchestration pipeline built in Zapier that ingests batch orders on a schedule, validates stock and payment status, and automatically routes each order down a fulfillment or exception path.

## Overview

This automation replaces a manual spreadsheet driven order review process. Every hour, the workflow pulls in a batch of incoming orders, parses the payload with a Python code step, loops through every line item, and uses Zapier Paths, Tables, and Filters to decide whether an order should be confirmed or flagged for support.

It eliminates manual triage, cuts confirmation email delays, and gives the support team a clean, structured exception queue.

Tech stack: Zapier (Schedule, Code, Looping, Paths, Filter, Tables, Gmail)

## Business Problem

The operations team was manually reviewing every incoming order to check stock, payment status, and order value. 

This caused several issues:
- Delayed confirmations for customers
- Missed or untracked out-of-stock items
- Lack of an audit trail for inventory updates
- Overloaded support inboxes

## Workflow Structure

1. Schedule Trigger: Runs hourly to ingest batch orders.
2. Code by Zapier: Parses raw order payloads into a clean array using Python.
3. Looping by Zapier: Iterates through each line item individually.
4. Paths by Zapier: Splits orders based on rules.

Path A - High-Value and In-Stock Orders:
- Searches inventory records in Zapier Tables.
- Filters and verifies payment status is Paid.
- Sends an order confirmation email via Gmail.
- Updates inventory balance and creates an audit log entry.

Path B - Out of Stock and Exception Orders:
- Searches the pending exceptions table.
- Filters for priority customer flags.
- Sends an alert email to the support team.
- Inserts a new open exception record into Zapier Tables.

## Key Outcomes

- Cuts order confirmation times down from hours to minutes.
- Automatically logs 100 percent of exceptions into a structured database.
- Routes VIP customer exceptions directly to support.
- Maintains an accurate audit trail for every inventory adjustment.

## Repository Contents

- README.md: Project documentation
- workflow.json: Exported Zapier workflow structure
- project-thumbnail.png: Zapier canvas layout preview
