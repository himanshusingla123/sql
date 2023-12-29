In SQL, both RANK() and DENSE_RANK() are window functions used for ranking rows within a result set based on the values in one or more columns. However, there is a key difference between them:

1. **RANK():**
   - Assigns a unique rank to each distinct row within the result set.
   - If two or more rows have the same values, they receive the same rank, and the next rank is skipped.
   - Subsequent ranks are adjusted to account for the skipped ranks.

   Example:
   ```sql
   SELECT
       column1,
       column2,
       RANK() OVER (ORDER BY column3) AS Rank
   FROM
       your_table;
   ```

2. **DENSE_RANK():**
   - Similar to RANK(), it assigns a unique rank to each distinct row.
   - If two or more rows have the same values, they also receive the same rank, but the next rank is not skipped.
   - Subsequent ranks are not adjusted and continue without gaps.

   Example:
   ```sql
   SELECT
       column1,
       column2,
       DENSE_RANK() OVER (ORDER BY column3) AS DenseRank
   FROM
       your_table;
   ```

In summary, the main difference is in how they handle tied ranks. RANK() may have gaps in the ranking sequence when there are ties, while DENSE_RANK() does not have gaps and assigns consecutive ranks to tied values.

To calculate the row number in SQL, you can use the `ROW_NUMBER()` window function. This function assigns a unique sequential integer to each row within a partition of the result set. Here's a basic example:

```sql
SELECT
    column1,
    column2,
    ROW_NUMBER() OVER (ORDER BY column3) AS RowNumber
FROM
    your_table;
```

In this example:

- `column1`, `column2`, and `column3` are the columns from your table.
- `ROW_NUMBER() OVER (ORDER BY column3)` is the expression that calculates the row number. You can adjust the `ORDER BY` clause to specify the column or columns based on which you want to order the rows.

This query will give you a result set with an additional column, `RowNumber`, which contains the calculated row numbers.

Keep in mind that the `ROW_NUMBER()` function is sensitive to the `ORDER BY` clause, so changing the order will result in different row numbers. If you want to partition the result set based on certain columns, you can use the `PARTITION BY` clause. For example:

```sql
SELECT
    column1,
    column2,
    ROW_NUMBER() OVER (PARTITION BY partition_column ORDER BY column3) AS RowNumber
FROM
    your_table;
```

Replace `partition_column` with the column by which you want to partition the result set.
