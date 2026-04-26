# 📊 SQL Job Postings Analysis

A SQL-based data analysis project exploring the data analyst job market — covering top-paying roles, in-demand skills, and the highest-compensating skill sets for remote Data Analyst positions.

## 🗂️ Repository Structure

```
├── sql.fls/
│   ├── 1_create_database.sql    # Database creation
│   ├── 2_create_tables.sql      # Table schemas and indexes
│   └── 3_modify_tables.sql      # Data loading instructions
│
├── project_sql/
│   ├── 1_top_data_analyst       # Top 10 highest-paying remote DA jobs
│   ├── 2_top_data_skills        # Skills required by those top-paying jobs
│   ├── 3_top_skills             # Most in-demand skills across remote DA roles
│   └── 4_top_paying_skills      # Highest-paying skills (with 100+ job demand)
│
└── README.md
```

## 🗄️ Database Schema

The project uses a PostgreSQL database (`sql_course`) with four tables:

| Table | Description |
|---|---|
| `job_postings_fact` | Core job listings with salary, location, and schedule info |
| `company_dim` | Company names and metadata |
| `skills_dim` | Skill names and categories |
| `skills_job_dim` | Junction table linking jobs to required skills |

## 🚀 Getting Started

### 1. Create the Database

Run `sql.fls/1_create_database.sql` in pgAdmin or psql to create the `sql_course` database.

### 2. Create Tables

Run `sql.fls/2_create_tables.sql` to set up all four tables with proper primary keys, foreign keys, and indexes.

### 3. Load Data

Follow the instructions in `sql.fls/3_modify_tables.sql`. Due to permission considerations, it's recommended to use the `\copy` command via the PSQL Tool in pgAdmin:

```sql
\copy company_dim FROM '/path/to/csv/company_dim.csv' WITH (FORMAT csv, HEADER true, DELIMITER ',', ENCODING 'UTF8');
\copy skills_dim FROM '/path/to/csv/skills_dim.csv' WITH (FORMAT csv, HEADER true, DELIMITER ',', ENCODING 'UTF8');
\copy job_postings_fact FROM '/path/to/csv/job_postings_fact.csv' WITH (FORMAT csv, HEADER true, DELIMITER ',', ENCODING 'UTF8');
\copy skills_job_dim FROM '/path/to/csv/skills_job_dim.csv' WITH (FORMAT csv, HEADER true, DELIMITER ',', ENCODING 'UTF8');
```

### 4. Run the Analysis

Execute the queries in `project_sql/` in order to explore the job market insights.

## 🔍 Analysis Overview

See the [`project_sql/` README](project_sql/README.md) for a detailed breakdown of each query and its findings.

## 🛠️ Tools Used

- **PostgreSQL** — Database engine
- **pgAdmin** — GUI for database management
- **VS Code** with SQL extensions — Query authoring
