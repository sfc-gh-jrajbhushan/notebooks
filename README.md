# Dynamic Tables Demo — Feature Engineering for Valuations

A Snowflake notebook demonstrating how Dynamic Tables, Workspace Notebooks, and Git Integration solve common pain points in model feature engineering workflows.

## What's in this demo

| Section | What it shows |
|---------|--------------|
| Pipeline setup | 3 raw source tables (credit bureau, transactions, demographics) with synthetic data |
| Feature Store (DT) | Joins across sources, derives risk tiers, income bands, spend features. 1-minute target lag. |
| Acquisition Summary (DT) | Portfolio-level metrics by segment. Downstream lag — auto-refreshes when feature store updates. |
| Live refresh | Insert new applicants into source tables, watch both DTs update automatically |
| Dependency management | `pip --dry-run` for automatic version resolution + `INSTALLED_PACKAGES` blast-radius query |
| Git integration | DDL for connecting a private GitHub repo (CREATE SECRET, API INTEGRATION, GIT REPOSITORY) |
| Artifactory integration | DDL for connecting a private PyPI repo with PrivateLink support |

## Prerequisites

- Snowflake account with SYSADMIN (or equivalent) to create databases
- Warehouse `DASH_S` (or edit the notebook to use a different warehouse)

## How to run

1. Upload `ian_dt_demo.ipynb` to a Snowflake Workspace, or push to a git repo and pull from Snowflake
2. Open the notebook in Snowflake Notebooks (Container Runtime)
3. Run cells sequentially — the setup cells create all objects in `DEMO_IAN.VALUATIONS`
4. For the live refresh section, wait ~1 minute after the insert for the DT to refresh

## Cleanup

The last cell contains commented-out DROP statements. Uncomment and run to remove all demo objects.

## Files

- `ian_dt_demo.ipynb` — The demo notebook
- `README.md` — This file
