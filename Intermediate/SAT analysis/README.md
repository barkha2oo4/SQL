# 🏫 NYC Public School SAT Performance Analysis (SQL + SQLite in Colab)

This project explores SAT performance across NYC public high schools using SQL (SQLite) in a Colab environment. The analysis includes borough-wise performance, top schools, and data completeness profiling — mimicking real-world data auditing and reporting scenarios.

---

## 📊 Objectives

- Identify top 5 high-performing schools by total SAT score.
- Compare SAT performance across NYC boroughs.
- Find the best-performing school per borough.
- Audit data completeness (missing SAT score fields).
- Generate actionable recommendations for educational improvement and data integrity.

---

## 🧰 Tech Stack

- **SQL**: Core analysis and data aggregation (SQLite syntax)
- **Python**: Used with SQLite3 and Pandas in **Google Colab**
- **SQLite**: Lightweight relational database engine
- **Pandas**: For querying and displaying SQL results

---

## 🧱 Database Schema

Two tables were created:

### `schools`

| Column Name | Type     | Description              |
|-------------|----------|--------------------------|
| school_id   | TEXT     | Unique school identifier |
| name        | TEXT     | Name of the school       |
| borough     | TEXT     | NYC Borough              |

### `sat_scores`

| Column Name     | Type | Description                |
|-----------------|------|----------------------------|
| school_id       | TEXT | Foreign key to `schools`   |
| reading_score   | INT  | SAT Reading score          |
| math_score      | INT  | SAT Math score             |
| writing_score   | INT  | SAT Writing score          |

---

## 📌 Key SQL Steps

### ✅ Step 1–3: Schema & Setup
- Created schema using SQLite
- Inserted 20 synthetic school + SAT records (with intentional NULLs for data quality analysis)

### ✅ Step 4–7: Core Analysis
- Top 5 Schools by total SAT score
- Borough-wise average SAT score analysis
- Best-performing school in each borough

### ✅ Step 8–9: Data Completeness
- Missing score counts by field
- Incomplete schools and affected boroughs
- Proportion of complete vs incomplete records

### ✅ Step 10: Insights & Recommendations
- Data storytelling for educational improvements
- Data quality compliance monitoring

---

## 🧠 Insights

- **Manhattan** leads SAT performance with highest average total scores.
- **Hunter College HS** is the top overall performer.
- 15% of SAT score records are **incomplete** — a red flag for decision-making.
- **Equal number of missing fields** across reading, math, and writing.

---

## 📌 Recommendations

- Strengthen SAT score reporting policies in Bronx, Queens, and Staten Island.
- Use Manhattan’s schools as benchmarks for curriculum and strategy.
- Encourage periodic data audits and completeness checks.
- Tag records with missing SAT fields to avoid skewing aggregate stats.

---

## 📁 Project Files

| File                    | Description                            |
|-------------------------|----------------------------------------|
| `notebook.ipynb`        | Colab notebook with all steps & output |
| `README.md`             | Project summary & portfolio write-up   |
| `school_sat.db` (opt.)  | SQLite database file (if exporting)    |

---

## 📈 Sample Query

```sql
SELECT name, borough,
       reading_score + math_score + writing_score AS total_score
FROM schools
JOIN sat_scores USING(school_id)
WHERE reading_score IS NOT NULL AND math_score IS NOT NULL AND writing_score IS NOT NULL
ORDER BY total_score DESC
LIMIT 5;
