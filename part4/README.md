Part 4 – LLM-Powered Intelligent System

The objective of this project is to develop an LLM-powered feature that evaluates insurance records using a structured business scoring rubric. The solution uses the Google Gemini API, validates structured JSON outputs using JSON Schema, implements a PII guardrail, and demonstrates deterministic and non-deterministic outputs through temperature comparison.

Dataset
Dataset Name: Medical Insurance Cost Dataset
Input File: cleaned_data.csv

LLM API
Provider: Google Gemini API
Model: gemini-2.0-flash (or replace with the model you actually used)

The API key is stored securely using an environment variable.
No API keys are hardcoded.

A reusable function named `call_llm()` was implemented.

1) It accepts a system prompt
2) It accepts a user prompt
3) It supports configurable temperature
4) It limits output tokens
5) It returns the model response

System Prompt
You are an insurance risk assessment assistant.Evaluate the insurance record and return ONLY valid JSON.

Required fields:
1) risk_tier
2) flag_for_review
3) primary_signal
4) confidence
5) recommended_action

Example
Input: {"age":45,"bmi":31,"smoker":"yes"}

Output
{
"risk_tier":"high",
"flag_for_review":true,
"primary_signal":"smoker",
"confidence":"high",
"recommended_action":"manual review"
}

User Prompt Template
Score the following insurance record.

Record:
{record_json}
Return ONLY valid JSON.

Why Temperature = 0?

Temperature was set to be 0 because the structured JSON generation requires deterministic and consistent outputs. A lower temperature always selects the highest-probability tokens, reducing randomness and ensuring reliable formatting.

JSON Schema Validation
A JSON schema containing five required scalar fields was defined.
Required fields:
1) risk_tier
2) flag_for_review
3) primary_signal
4) confidence
5) recommended_action

Every LLM response was:

1. stripped of whitespace
2. parsed using `json.loads()`
3. validated using `jsonschema.validate()`
Invalid responses were replaced using a fallback dictionary containing null values.

PII Guardrail
Before every API request, a regular expression checks for personally identifiable information.
Blocked examples:
1) Email addresses
2) Phone numbers

Example:
Input: Customer email is abc@gmail.com
Output: Input blocked: PII detected.

Clean inputs successfully proceed to the LLM.

Files Included
1) part4.ipynb
2) cleaned_data.csv
3) README.md
4) requirements.txt
