### Source

The dataset that these queries pulled from is the London Crime dataset made publically available by https://data.london.gov.uk/ and hosted by the Google BigQuery platform.

### Query 1

This first Query will select the total number of crimes across the 4 categories for Time Period #1 (2009-2012).

```sql
SELECT 
  major_category,
  SUM(value) AS total_crimes
FROM
 `bigquery-public-data.london_crime.crime_by_lsoa`
WHERE
  year >= 2009 AND year <= 2012
  AND (major_category = 'Burglary' 
  OR major_category = 'Criminal Damage'
  OR major_category = 'Drugs'
  OR major_category = 'Violence Against the Person')
GROUP BY
  major_category
```

### Query 2

And this second Query will grab the same information for Time Period #2 (2013-2016).

```sql
SELECT 
  major_category,
  SUM(value) AS total_crimes
FROM
 `bigquery-public-data.london_crime.crime_by_lsoa`
WHERE
  year >= 2013 AND year <= 2016
  AND (major_category = 'Burglary' 
  OR major_category = 'Criminal Damage'
  OR major_category = 'Drugs'
  OR major_category = 'Violence Against the Person')
GROUP BY
  major_category
```

These two pieces of information can be used to visualize the difference in these crime categories between 2009-2012 and 2013-2016.

Next, I investigate how these crime types are broken down by month in the two time periods.

---

### Query 3

This third query breaks down crime by month for Time Period #1 (2009-2012).

```sql
SELECT 
  major_category,
  month,
  SUM(value) AS total_crimes
FROM
 `bigquery-public-data.london_crime.crime_by_lsoa`
WHERE
  year >= 2009 AND year <= 2012
  AND (major_category = 'Burglary' 
  OR major_category = 'Criminal Damage'
  OR major_category = 'Drugs'
  OR major_category = 'Violence Against the Person')
GROUP BY
  major_category,
  month
ORDER BY
  month
```

### Query 4

This fourth query grabs the same information for Time Period #2 (2013-2016).

```sql
SELECT 
  major_category,
  month,
  SUM(value) AS total_crimes
FROM
 `bigquery-public-data.london_crime.crime_by_lsoa`
WHERE
  year >= 2013 AND year <= 2016
  AND (major_category = 'Burglary' 
  OR major_category = 'Criminal Damage'
  OR major_category = 'Drugs'
  OR major_category = 'Violence Against the Person')
GROUP BY
  major_category,
  month
ORDER BY
  month
```

Now for the last two Queries I want to know how the crime totals for these categories change across the boroughs of London.

---

### Query 5

This fifth query displays crime totals by category and borough for Time Period #1 (2009-2012).

```sql
SELECT 
  major_category,
  borough,
  SUM(value) AS total_crimes
FROM
 `bigquery-public-data.london_crime.crime_by_lsoa`
WHERE
  year >= 2009 AND year <= 2012
  AND (major_category = 'Burglary' 
  OR major_category = 'Criminal Damage'
  OR major_category = 'Drugs'
  OR major_category = 'Violence Against the Person')
GROUP BY
  major_category,
  borough
ORDER BY
  borough
```

### Query 6

This sixth query grabs the same information for Time Period #2 (2013-2016).

```sql
SELECT 
  major_category,
  borough,
  SUM(value) AS total_crimes
FROM
 `bigquery-public-data.london_crime.crime_by_lsoa`
WHERE
  year >= 2013 AND year <= 2016
  AND (major_category = 'Burglary' 
  OR major_category = 'Criminal Damage'
  OR major_category = 'Drugs'
  OR major_category = 'Violence Against the Person')
GROUP BY
  major_category,
  borough
ORDER BY
  borough
```

---

The results of these 6 Queries are saved in their own CSV files that I will use to create visualizations.
