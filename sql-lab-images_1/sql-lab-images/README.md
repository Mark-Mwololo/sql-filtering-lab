# Apply Filters to SQL Queries

## Project Description

This project places me in the role of a security professional at a large organization tasked with investigating security issues to help keep the system secure. Using the organization's `employees` and `log_in_attempts` tables, I applied SQL filtering commands — `SELECT`, `FROM`, `WHERE`, `LIKE`, `AND`, `OR`, and `NOT` — to retrieve private records and logs from different datasets. Each query was designed to isolate specific, relevant information in order to investigate potential security incidents and support routine department-wide system updates.

## Project Queries

Commands used: `SELECT`, `FROM`, `WHERE`, `LIKE`, `AND`, `OR`, `NOT`

### 1. Retrieve after-hours failed login attempts
**Scenario:** A potential security incident occurred after business hours. Query the `log_in_attempts` table to review all failed login attempts that occurred after 18:00.

```sql
SELECT * FROM log_in_attempts WHERE login_time > '18:00' AND success = 0;
```

![After hours failed login attempts](sql-lab-images/01_after_hours_failed_logins.png)

### 2. Retrieve login attempts on specific dates
**Scenario:** A suspicious event occurred on 2022-05-09. Review all login attempts that occurred on that day and the day before.

```sql
SELECT * FROM log_in_attempts WHERE login_date = '2022-05-08' OR login_date = '2022-05-09';
```

![Login attempts on specific dates](sql-lab-images/02_specific_date_logins.png)

### 3. Retrieve login attempts outside of Mexico
**Scenario:** Suspicious login activity was determined not to have originated in Mexico. Identify all login attempts that occurred outside of Mexico (the `country` column contains both `MEX` and `MEXICO`).

```sql
SELECT * FROM log_in_attempts WHERE NOT country LIKE 'MEX%';
```

![Login attempts outside of Mexico](sql-lab-images/03_outside_mexico_logins.png)

### 4. Retrieve employees in Marketing
**Scenario:** Security updates need to be performed on Marketing department machines located in the East building.

```sql
SELECT * FROM employees WHERE department = 'Marketing' AND office LIKE 'East%';
```

![Marketing employees in East building](sql-lab-images/04_marketing_east_office.png)

### 5. Retrieve employees in Finance or Sales
**Scenario:** A security update needs to be performed on machines for employees in the Sales and Finance departments.

```sql
SELECT * FROM employees WHERE department = 'Finance' OR department = 'Sales';
```

![Finance or Sales employees](sql-lab-images/05_finance_or_sales.png)

### 6. Retrieve all employees not in IT
**Scenario:** Employees in the Information Technology department already received a security update; all other departments still need it.

```sql
SELECT * FROM employees WHERE NOT department = 'Information Technology';
```

![Employees not in IT department](sql-lab-images/06_not_it_department.png)

## Summary

In this project, I practiced using SQL to filter and retrieve specific records from both login activity logs and employee data in order to support a security investigation and routine department updates. This kind of targeted querying is a core skill for a SOC analyst, where the ability to quickly isolate relevant login attempts, flag suspicious patterns, and pull precise employee or system records can directly impact how fast a threat is identified and contained. Being comfortable writing efficient, accurate SQL filters means less time sifting through irrelevant data and more time focused on actual analysis and response. This project reflects the kind of hands-on database querying I'd bring to a security operations role, where speed and precision in data retrieval are essential to keeping an organization's systems secure.

## Repository Structure

```
├── README.md
└── sql-lab-images/
    ├── 01_after_hours_failed_logins.png
    ├── 02_specific_date_logins.png
    ├── 03_outside_mexico_logins.png
    ├── 04_marketing_east_office.png
    ├── 05_finance_or_sales.png
    └── 06_not_it_department.png
```
