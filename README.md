Natural Language to SQL Table Selection
This project explores the feasibility of using GPT-3.5-Turbo to determine which tables are necessary to create an SQL query based on natural language prompts.

Installation
To run the project, ensure you have installed the required dependencies:

bash
Copy code
pip install openai==1.1.1
Usage
Define Tables: Define tables and their content definitions using a pandas DataFrame.

Prepare Prompts: Create prompts by specifying tables and user questions.

Model Invocation: Utilize the return_OAI function to call the GPT-3.5-Turbo model with the prompts.

Analyze Results: Review the JSON output containing the necessary tables for the SQL query.

Example
python
Copy code
# Define Tables
data = {'table': ['employees', 'salary', 'studies'],
        'definition': ['Employee information, name...',
                       'Salary details for each year',
                       'Educational studies, institution, type, level']}
df = pd.DataFrame(data)

# Prepare Prompts
prompt_question_tables = """
Given the following tables and their content definitions,
###Tables
{tables}

Tell me which tables would be necessary to query with SQL to address the user's question below.
Return the table names in a JSON format.
###User Question:
{question}
"""
pqt1 = prompt_question_tables.format(tables=text_tables, question="Return the name of the highest-paid employee")

# Model Invocation
result1 = return_OAI(pqt1)

# Analyze Results
print(result1)
# Output: {"tables": ["employees", "salary"]}
Conclusion
This project demonstrates GPT-3.5-Turbo's capability in determining tables essential for SQL queries. Further refinement and testing may be required for complex systems.

This README provides a comprehensive overview of the project, including installation instructions, usage guidelines, an example, and a conclusion.
