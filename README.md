# International Students and Mental Health — SQL Data Analysis

### Overview
This project investigates whether studying in a different country affects a student's mental health.  
It uses survey data from a Japanese international university collected in 2018 to explore how the **length of stay** impacts depression, social connectedness, and acculturative stress among international students.

The dataset was analyzed using **PostgreSQL** within DataCamp Workspace to reproduce insights similar to published academic findings on mental health and adaptation challenges among international students.

---

### Dataset
**File:** `students.csv`

| Field Name     | Description |
|----------------|-------------|
| `inter_dom`    | Type of student (international or domestic) |
| `japanese_cate`| Japanese language proficiency |
| `english_cate` | English language proficiency |
| `academic`     | Academic level (undergraduate or graduate) |
| `age`          | Current age of student |
| `stay`         | Length of stay in years |
| `todep`        | Total depression score (PHQ-9 test) |
| `tosc`         | Total social connectedness score (SCS test) |
| `toas`         | Total acculturative stress score (ASISS test) |

---

### Project Instructions
Explore and analyze the `students` data to determine how the **length of stay (`stay`)** impacts the **average mental health diagnostic scores** of international students in the study.

The final query should:
1. Return a table with **nine rows** and **five columns**.
2. Alias the columns as:  
   - `stay`  
   - `count_int`  
   - `average_phq`  
   - `average_scs`  
   - `average_as`
3. Compute the averages of:
   - `todep` (PHQ-9 test)  
   - `tosc` (SCS test)  
   - `toas` (ASISS test)  
   rounded to two decimal places.
4. Include `count_int` as the number of international students per length of stay.
5. Sort the results by `stay` in descending order.
6. Ensure the final DataFrame name is **`df`**.

---

### SQL Query
```sql
SELECT stay, 
       COUNT(*) AS count_int, 
       ROUND(AVG(todep), 2) AS average_phq, 
       ROUND(AVG(tosc), 2) AS average_scs,
       ROUND(AVG(toas), 2) AS average_as
FROM students
WHERE inter_dom = 'Inter'
GROUP BY stay
ORDER BY stay DESC;
