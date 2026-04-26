# 🔎 project_sql — Data Analyst Job Market Analysis

This folder contains four SQL queries that progressively explore the remote Data Analyst job market, from identifying the best-paying roles to pinpointing the most valuable skills.

---

## Query 1 — Top 10 Paying Remote Data Analyst Jobs
**File:** `1_top_data_analyst`

Finds the ten highest-paying remote (`Anywhere`) Data Analyst job postings that have a listed salary.

**Key columns returned:** `job_id`, `company`, `job_title_short`, `job_location`, `job_schedule_type`, `salary_year_avg`

**Approach:** Joins `job_postings_fact` with `company_dim`, filters for `job_title_short = 'Data Analyst'` and `job_location = 'Anywhere'`, excludes null salaries, and orders by `salary_year_avg DESC`.

---

## Query 2 — Skills Behind the Top 10 Paying Jobs
**File:** `2_top_data_skills`

Builds on Query 1 using a CTE to identify what skills the top 10 highest-paying remote DA jobs actually require.

**Key columns returned:** everything from the CTE + `skills`

**Approach:** Wraps the top-10 job logic in a CTE (`top_jobs`), then joins through `skills_job_dim` and `skills_dim` to surface the associated skill names. Results remain ordered by salary so the skill-to-salary relationship is clear.

---

## Query 3 — Most In-Demand Skills for Remote DA Roles
**File:** `3_top_skills`

Counts how frequently each skill appears across *all* remote Data Analyst postings with a listed salary, returning the top 5 most demanded skills.

**Key columns returned:** `skills`, `demand_count`

**Approach:** Joins all four tables, groups by skill name, and orders by count descending with `LIMIT 5`. This highlights the skills most likely to appear in job requirements — useful for prioritizing what to learn.

---

## Query 4 — Highest-Paying Skills (With Meaningful Demand)
**File:** `4_top_paying_skills`

Identifies which skills command the highest average salary among remote DA roles, filtered to only include skills that appear in more than 100 job postings (ensuring statistical relevance).

**Key columns returned:** `skills`, `avg_salary`, `demand_count`

**Approach:** Uses a CTE (`jbs`) to compute the average salary and demand count per skill across all qualifying postings, then filters the outer query to `demand_count > 100`. This surfaces skills that are both well-compensated *and* widely valued — the sweet spot for career development.

---

## How These Queries Connect

```
Query 1  ──►  Which jobs pay the most?
Query 2  ──►  What skills do those top jobs require?
Query 3  ──►  Which skills appear most often across all DA jobs?
Query 4  ──►  Which skills offer the best salary, with real demand?
```

Together they paint a complete picture: what the market pays, what it wants, and where skill investment yields the greatest return.
