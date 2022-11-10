
# The problem: 

## I have 2 csv files and I need to check for lines in common

---

Steps:

1. First step was to sanitize files, I've replaced all `"` characteres and fixed the value from the last column removing floating point from column 

2. I've sorted the files just for better visualization based on the first column
    ```sh
    sort --field-separator=';' -k1 old_solution_rows.csv > old_solution_rows_sorted.csv
    ```

3. I've used the `comm` to make the results:

    > Show lines that only exist in file b: (i.e. what was added to b)
    ```sh
    comm -23 a b
    ```
    ```sh
    comm -13 new_solution_rows_sorted.csv old_solution_rows_sorted.csv > new_solution_missing_rows.csv
    ``` 

    > Show lines that only exist in file a: (i.e. what was deleted from a)
    ```sh
    comm -13 a b
    ```
    ```sh
    comm -23 new_solution_rows_sorted.csv old_solution_rows_sorted.csv > new_solution_extra_rows.csv
    ```


