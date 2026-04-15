## GymBot: AI-Powered Fitness Tracking & SQL Assistant

A Python-based AI application that simulates, stores, and analyzes fitness data using an SQLite database, Google Gemini (GenAI) for natural language querying, and a LangGraph-powered chatbot (GymBot) for interactive logging and insights.

---

## Overview

This project combines LLMs + structured databases to create an intelligent fitness assistant.

It:

Generates and stores 60 days of fitness data

Allows users to query data using natural language

Provides an interactive chatbot to log daily fitness activity

Computes calorie burn and trends dynamically using SQL

---

## Project Structure
GymBot/
├── main_notebook.ipynb        # End-to-end implementation (data + querying + chatbot)
├── health.db                 # SQLite database (generated)
├── README.md                 # Project documentation

---

## Getting Started
Prerequisites
Python 3.9+
Google API Key (Gemini)
1. Install Dependencies
pip install google-genai==1.7.0
pip install langgraph==0.3.21 langchain-google-genai==2.1.2 langgraph-prebuilt==0.1.7
2. Set Up API Key
import os
os.environ["GOOGLE_API_KEY"] = "your_api_key_here"
3. Run the Project
Open the notebook or script
Run all cells to:
Generate database
Enable querying
Launch GymBot

---


## Features & Usage
# 1. Natural Language → SQL Queries

Ask questions like:

chat.send_message("What day did the person burn the most calories?")

The model:

Inspects tables
Generates SQL queries
Executes them
Returns structured answers

# 2. Fitness Data Stored

The system tracks:

Steps (brisk, slow, running)
Calories consumed
Workout duration
Activity levels
Weight trends

# 3. Calorie Burn Logic

Total calories burned per day:

(brisk_steps × 0.04) +
(slow_steps × 0.02) +
(run_steps × 0.06) +
(light_minutes × 2) +
(moderate_minutes × 4) +
(workout_minutes × 10)

# 4. GymBot (Interactive Chat Assistant)

Start a conversation to:

Log daily fitness data
Store it in the database
Get diet & workout advice
Example Interaction
User: Log
Bot: Please provide:
date, steps, weight, activity, calories...

User:
2024-05-27, 1700, 2100, 1208, 68, 277, 198, 60, 1450

# 5. Database Utilities
Check Data
check_daily_info("2024-05-27")
Delete Data
delete_daily_info("2024-05-27")

# 6. Search Grounding
Uses Gemini with Google Search
Retrieves real-world info (e.g., gym timings)

# 7. Visualization Support

Includes example code for:

Plotting calorie burn across exercises
Using Seaborn + Matplotlib

---


# Model & System Details
LLM
Model: Gemini 2.0 Flash
Tool-calling enabled for:
SQL execution
Schema inspection
Chatbot Framework
LangGraph
State-based workflow
Tool routing
Multi-step reasoning
Database
SQLite (health.db)
Tables:
step_analysis_daily
activity_daily
workout_daily
calories_consumed_daily
calorie_burn_rates_per_step
calorie_burn_rates_per_minute

---

# Notes
Built for the Kaggle Google GenAI Hackathon - learn agentic AI in 5 days series

