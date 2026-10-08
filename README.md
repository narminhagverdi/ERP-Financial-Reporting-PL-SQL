# ERP Financial Reporting --- Oracle PL/SQL

A practical Oracle SQL/PL/SQL project that simulates an ERP financial
reporting environment.

## Project Overview

This project models core financial processes using Oracle Database
objects and PL/SQL:

-   General Ledger (GL)
-   Accounts Payable (AP)
-   Accounts Receivable (AR)
-   Financial reporting and aggregation
-   Journal-entry balance validation
-   Vendor and customer exposure reporting
-   Error logging
-   Scheduled reporting/validation jobs
-   Query performance analysis with `EXPLAIN PLAN`

## Database Objects

### Tables

-   `GL_JE_HEADERS` --- journal entry headers
-   `GL_JE_LINES` --- journal entry lines
-   `AP_VENDORS` --- vendor master data
-   `AP_INVOICES_ALL` --- accounts payable invoices
-   `AR_CUSTOMERS` --- customer master data
-   `AR_CASH_RECEIPTS` --- customer cash receipts
-   `ERROR_LOG` --- PL/SQL error logging

The tables include primary keys, foreign keys, unique constraints, check
constraints and default values.

### Indexes

The project includes indexes for frequently used join/filter columns,
including:

-   Journal header/line relationships
-   Vendor and customer relationships
-   Period and account filtering
-   Payment/receipt status
-   Composite account/header access

### Views

-   `VW_JOURNAL_ENTRY_DETAIL`
-   `VW_TRIAL_BALANCE`
-   `VW_LEDGER_SUMMARY`
-   `VW_AP_VENDOR_EXPOSURE`
-   `VW_AR_CUSTOMER_EXPOSURE`

The reporting views use joins, aggregation, `CASE`, `NVL`, and analytic
functions such as `RANK`, `DENSE_RANK`, and cumulative `SUM`.

### Materialized Views

-   `MV_TRIAL_BALANCE`
-   `MV_AP_VENDOR_EXPOSURE`

These are configured for complete refresh on demand and are supported by
indexes.

### PL/SQL Package

`PKG_GL_REPORTS` provides reusable financial logic:

-   `F_IS_JE_BALANCED` --- checks whether journal debit equals credit
-   `P_VALIDATE_ALL_JOURNALS` --- validates all journal entries
-   `P_CREATE_JOURNAL_ENTRY` --- creates a debit/credit journal entry
-   `F_GET_ACCOUNT_BALANCE` --- calculates an account balance for a
    period

The package also demonstrates exception handling and writes errors to
`ERROR_LOG`.

### Triggers

-   `TRG_GLJL_VALIDATE_BALANCE` --- validates journal balance after
    statement processing
-   `TRG_ARCR_UPDATE_BALANCE` --- updates customer balance after a
    confirmed receipt
-   `TRG_APINV_AUDIT_PAID` --- records when an invoice changes to `PAID`

### Scheduler Jobs

The project includes Oracle `DBMS_SCHEDULER` jobs for:

-   Nightly materialized-view refresh
-   Daily journal-balance validation

### Performance Analysis

The project demonstrates `EXPLAIN PLAN` and `DBMS_XPLAN.DISPLAY` for
comparing query execution plans.

## Technologies

-   Oracle Database
-   SQL
-   PL/SQL
-   Oracle Views
-   Materialized Views
-   Indexes
-   Analytic Functions
-   PL/SQL Packages
-   Triggers
-   `DBMS_SCHEDULER`
-   `EXPLAIN PLAN`
-   `DBMS_XPLAN`

## How to Run

1.  Open Oracle SQL Developer or another Oracle-compatible SQL client.
2.  Connect to an Oracle schema where you have permission to create the
    required objects.
3.  Open `ERP_Financial_Reporting.sql`.
4.  Run the script in the required order.
5.  Review the created tables, views, package, triggers, materialized
    views and scheduler jobs.
6.  Use the included reporting queries to inspect the results.

> Note: Some objects such as scheduler jobs and materialized views may
> require additional Oracle privileges.

## Main Reporting Examples

The project includes examples for:

-   Journal-entry detail reporting
-   Trial balance reporting
-   Cumulative ledger balances
-   Vendor outstanding exposure
-   Customer balance ranking
-   Invoice percentage-of-total analysis
-   Journal debit/credit validation

## Project Goal

The goal of this project is to demonstrate practical Oracle SQL and
PL/SQL skills in an ERP-style financial reporting scenario, with a focus
on database design, reporting, reusable PL/SQL logic, data validation,
automation and query performance.

## Author

**Narmin Hagverdi**

Oracle SQL / PL/SQL learning project focused on ERP Financial Reporting.
