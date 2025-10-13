# Code Templating with Jinja2

[Jinja2](https://jinja.palletsprojects.com/) is a **powerful templating engine for Python**. It allows you to build dynamic text files—such as **SQL**, **HTML**, **YAML**, **Python**, and **config scripts**—by injecting variables, logic, and control structures into templates.

Originally built for HTML generation (e.g., Flask web apps), Jinja2 is also widely used for:
- **SQL templating**
- **Code generation**
- **CI/CD configuration files**
- **Infrastructure as code (e.g., Terraform, Ansible)**

---

## Installation

```bash
uv pip install Jinja2
```

---

## Why Use Jinja for SQL?

Writing SQL in real-world projects often involves:

* Repeating similar query structures with different tables/columns
* Dynamically injecting filters or parameters
* Managing environment-specific differences (dev vs prod)

Jinja2 helps by allowing you to:

* Reuse templates
* Inject variables
* Use conditional logic and loops

---

## Basic SQL Templating with Jinja2

### Step 1: Create a SQL Template

```sql
-- query_template.sql
SELECT
    {{ columns | join(", ") }}
FROM
    {{ table_name }}
WHERE
    date >= '{{ start_date }}'
    {% if country %}
    AND country = '{{ country }}'
    {% endif %}
```

### Step 2: Render the Template in Python

```python
# render_sql_template.py
from jinja2 import Template

# Load the sql script as a template
template = Template(open("query_template.sql").read())

# Define variables to inject into the template
params = {
    "columns": ["id", "name", "created_at"],
    "table_name": "users",
    "start_date": "2023-01-01",
    "country": "Canada"
}

# Render the final SQL string
rendered_query = template.render(params)

# Save to file
with open("output.sql", "w") as f:
    f.write(rendered_query)

print(rendered_query)
```

### Output SQL

```sql
SELECT
    id, name, created_at
FROM
    users
WHERE
    date >= '2023-01-01'
    AND country = 'Canada'
```

## Jinja2 Features You Can Use in SQL Templates

| Feature           | Example                                                   |
|------------------|------------------------------------------------------------|
| **Variables**     | `{{ table_name }}`                                        |
| **Loops**         | `{% for col in columns %}{{ col }}, {% endfor %}`         |
| **Conditionals**  | `{% if include_filter %} ... {% endif %}`                 |
| **Filters**       | `{{ columns \| join(', ') }}`                             |
| **Includes**      | `{% include 'common_filters.sql' %}`                      |

### 1. Filters (`{{ columns | join(', ') }}`)

A **filter** modifies the value of a variable. Think of it like a **function** applied to a variable in a template.

#### Example:

```sql
{{ columns | join(', ') }}
```

This takes a list like:

```python
columns = ["id", "name", "created_at"]
```

And transforms it into:

```sql
id, name, created_at
```

#### Common Filters in Jinja2:

| Filter     | What It Does                            |
|------------|------------------------------------------|
| `join(', ')` | Joins a list into a string             |
| `upper`     | Converts text to uppercase              |
| `lower`     | Converts text to lowercase              |
| `length`    | Gets the length of a list or string     |


### 2. Includes (`{% include 'common_filters.sql' %}`)

`{% include %}` inserts the content of another template file into the current one.

Useful for reusing shared SQL snippets like filters or CTEs.

#### Example:

**main_query.sql**
```sql
SELECT *
FROM sales
WHERE 1 = 1
{% include 'common_filters.sql' %}
```

**common_filters.sql**
```sql
AND status = 'active'
AND created_at >= '2023-01-01'
```

#### Output after rendering:

```sql
SELECT *
FROM sales
WHERE 1 = 1
AND status = 'active'
AND created_at >= '2023-01-01'
```

### 3. Macros (`{% macro %}`)

A macro is like a **function** inside a Jinja template. Define reusable blocks of code with parameters.

#### Example:

**utils.sql**
```sql
{% macro country_filter(column, country) %}
    {% if country %}
        AND {{ column }} = '{{ country }}'
    {% endif %}
{% endmacro %}
```

**main_query.sql**
```jinja2
{% import 'utils.sql' as utils %}

SELECT * FROM customers
WHERE 1 = 1
{{ utils.country_filter('country', country) }}
```

If rendered with `country="Canada"`, the final query becomes:

```sql
SELECT * FROM customers
WHERE 1 = 1
AND country = 'Canada'
```


## Use Cases Beyond SQL

Jinja2 can also be used to template many other types of files:

### HTML

```html
<h1>Hello {{ user_name }}</h1>
```

### Python Scripts

```python
# script_template.py
def run():
    print("Running {{ task_name }} at {{ runtime }}")
```

### YAML / Config Files

```yaml
# config_template.yaml
env: {{ environment }}
debug: {% if environment == 'dev' %}true{% else %}false{% endif %}
```

### Shell Scripts

```bash
#!/bin/bash
echo "Deploying to {{ region }}"
```

- Write modular templates with `{% include %}` or `{% macro %}` for reuse.

## ✅ Summary

| Feature                  | Benefits                                        |
|--------------------------|-------------------------------------------------|
| Dynamic SQL              | Inject tables, columns, filters dynamically     |
| Logic in templates       | Use conditionals and loops                      |
| Reusable templates       | DRY code for similar scripts or environments    |
| Multi-file support       | Compose SQL from building blocks with includes  |
| Not limited to SQL       | Also use with HTML, YAML, configs, code         |

## Example Use Cases

- Generating similar queries for 50 tables with a loop
- Templating Snowflake or BigQuery SQL scripts by environment
- Creating Python or shell scripts dynamically in CI/CD pipelines
- Rendering config files for testing or deployment

## Further Resources

- Jinja2 Docs: https://jinja.palletsprojects.com/
- dbt (a SQL-based data tool built on Jinja): https://docs.getdbt.com/
