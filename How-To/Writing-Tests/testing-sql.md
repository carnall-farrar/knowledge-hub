
# Guide to Testing SQL Code in Data Projects

Testing SQL logic is just as important as testing pyThon code. Bad SQL leads to:
- Incorrect metrics and insights
- Poor model inputs
- Costly business decisions

Writing tests for SQL helps ensure:
- Data integrity
- Query correctness
- Reproducibility
- Trust in analytics and models

---

## 🔍 What Should You Test in SQL?

### 1. Join Coverage

**Problem:** SQL joins can silently drop records if keys don’t match or duplicate data if joins aren’t properly scoped.

**Test Strategy:**
- Check the number of rows before and after joins.
- Validate the presence of NULLs in joined columns.
- Log unexpected one-to-many or many-to-many joins.

**Example SQL Check (Post-Join Audit):**
```sql
-- Check unmatched records in a LEFT JOIN
SELECT COUNT(*) AS unmatched_orders
FROM orders o
LEFT JOIN customers c ON o.customer_id = c.customer_id
WHERE c.customer_id IS NULL;
```

**Expected Outcome:**
- `unmatched_orders = 0` if every order has a valid customer.

---

### 2. Check for Duplicates

**Problem:** Aggregations, joins, or inserts can unintentionally introduce duplicate rows or primary keys.

**Test Strategy:**
- Check for duplicate values in business or surrogate keys.
- Check row count vs expected row uniqueness.

**Example SQL Check:**
```sql
-- Detect duplicate user IDs
SELECT user_id, COUNT(*) AS occurrences
FROM users
GROUP BY user_id
HAVING COUNT(*) > 1;
```

**Expected Outcome:**
- This query should return **zero rows**.

---

### 3. Data Expectations & Known Output Checks

**Problem:** SQL often feeds into metrics or dashboards. Even if syntax is correct, **semantic errors** can yield incorrect data (e.g., revenue off by millions).

**Test Strategy:**
- Define **expected ranges, counts, or value sets** based on known data behavior.
- Use reference values or business rules for comparison.
- Add assertions or manual flags to trigger alerts if thresholds are exceeded.

**Examples:**

```sql
-- Check if recent user signups are within expected range
SELECT COUNT(*) AS recent_signups
FROM users
WHERE signup_date >= CURRENT_DATE - INTERVAL '7 days';
```

**Expected Range:**
- Between 900 and 1100 users (based on business expectations).

**Flag deviations in test scripts:**
```sql
WITH signups AS (
  SELECT COUNT(*) AS recent_signups
  FROM users
  WHERE signup_date >= CURRENT_DATE - INTERVAL '7 days'
)
SELECT CASE
         WHEN recent_signups < 900 OR recent_signups > 1100 THEN 'FAIL'
         ELSE 'PASS'
       END AS signup_check
FROM signups;
```

<!-- ---

## 🧰 Tools for Testing SQL

| Tool / Method             | Description                                           |
|---------------------------|-------------------------------------------------------|
| **dbt tests**             | Built-in tests for uniqueness, not-null, relationships |
| **Great Expectations**    | Framework for testing data quality with validations    |
| **pytest + SQLAlchemy**   | Write Python unit tests that execute SQL              |
| **Airflow DAG asserts**   | Add validation checks as tasks in your DAGs           |
| **Custom SQL scripts**    | Run your own test queries & assertions                |

---

## 🧪 Example Test with dbt

```yaml
# models/users.sql
select * from raw_users

# models/users.yml
version: 2

models:
  - name: users
    tests:
      - unique:
          column_name: user_id
      - not_null:
          column_name: email
```

Run with:
```bash
dbt test
```

---

## 🧪 Example Test with Great Expectations (GE)

```python
import great_expectations as ge
df = ge.read_csv("output/users.csv")

df.expect_column_values_to_be_unique("user_id")
df.expect_column_values_to_not_be_null("email")
df.expect_column_mean_to_be_between("signup_days", min_value=5, max_value=10)
```

---

## 📁 Suggested Testing Structure

```
project/
├── sql/
│   ├── transform/
│   ├── test_queries/
│   │   ├── check_joins.sql
│   │   ├── check_duplicates.sql
│   │   └── check_metrics.sql
├── expectations/
│   └── signups_expectation.json
├── tests/
│   └── test_data_validity.py  # for Python + SQL integration tests
```

---

## 🧠 Final Tips

- ✅ Test **before** loading to dashboards or models
- ✅ Test both **structure (joins, keys)** and **content (ranges, business rules)**
- ✅ Use **automation** (e.g., `dbt test`, cron jobs, Airflow) to run tests regularly
- ✅ Document known expectations and edge cases

---

## 🧪 Bonus: Questions to Ask in SQL Code Reviews

- Are **joins well-defined** and non-ambiguous?
- Are **primary/foreign keys** preserved?
- Is data **deduplicated** correctly?
- Are **known totals or counts** matching business expectations?
- Is there a test for **NULL values** in critical columns?

---

## 📚 Resources

- [dbt Testing Docs](https://docs.getdbt.com/docs/build/tests)
- [Great Expectations](https://docs.greatexpectations.io/)
- [SQL Testing with Pytest](https://docs.sqlalchemy.org/en/20/changelog.html#testing) -->
