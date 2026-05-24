# databricks-acme-motors-assistant

## Acme Motors Dealership Assistant

This repository contains a Databricks learning portfolio project focused on building a safe business assistant for a fictional car dealership company: **Acme Motors**.

## Scope

The goal of this project is to demonstrate how a manager could ask sales questions in natural language without allowing the AI model to invent numbers or generate unsafe SQL.

Example question:

```text
How many F150 trucks did I sell this month?
````

Instead of letting the AI answer directly, the system follows this flow:

```text
User question
↓
Databricks Foundation Model selects an approved function
↓
Python validates the function and arguments
↓
Python / Spark SQL queries Delta Tables
↓
The final answer is generated from real table results
```

## Main Idea

The LLM does not calculate sales numbers.

The LLM does not generate SQL.

The LLM only routes the question to one of the approved business functions.

```text
The LLM routes.
Python executes.
Delta Tables are the source of truth.
```

## Use Case

A dealership manager wants to ask questions like:

```text
How many F150 trucks did I sell this month?
What are my top-selling vehicle models?
Which sales representative sold the most?
How much revenue did we generate by state?
```

The assistant converts those questions into structured function calls, for example:

```json
{
  "function_name": "get_product_sales_summary",
  "arguments": {
    "product_model": "F150",
    "date_range": "this_month"
  }
}
```

Then Python executes the matching safe function against the `auto_sales_transactions` Delta Table.

## What this repo demonstrates

* Databricks notebooks
* PySpark DataFrames
* Delta Tables
* SQL over business data
* Databricks Foundation Model usage with `ai_query`
* Function-calling style workflow
* Safe query execution
* Python validation and OOP with a `FunctionRegistry`
* Audit logging for traceability

## Project Notebooks

```text
01_create_auto_sales_delta_table
02_manual_business_queries
03_function_catalog
04_python_function_registry
05_foundation_model_router
06_end_to_end_assistant
```

## Portfolio Purpose

This project was built to learn and demonstrate the basics of using Databricks for a GenAI-style business workflow.

It is a focused portfolio project showing how to combine Databricks, Delta Tables, Foundation Models, Python functions, and safe SQL execution.

```
