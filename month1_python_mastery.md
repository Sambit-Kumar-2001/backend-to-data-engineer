# Month 1: The "Daily Commit" Challenge (Python for DE)
**Goal:** 30 Days of Code. 30 Commits. Zero "Tutorial Hell".
**Audience:** Senior Backend Dev (C#/.NET/Node) transitioning to Data.

---

## 📅 Week 1: The "Delta" (Syntax & High-Level Structures)
**Theme**: "Stop writing C# in Python."

*   **Day 1: List Comprehensions (The "LINQ" of Python)**
    *   **Theory**: Loops are for side effects. Comprehensions are for transformations (Map/Filter).
    *   **Problem**: Generate a list of 10,000 random integers. Filter only the primes. Square them.
    *   **Target**: One line of code for the logic.
*   **Day 2: Dictionary Comprehensions (HashMaps on Steroids)**
    *   **Theory**: Rapidly building lookup tables without `.Add()`.
    *   **Problem**: Take a list of strings `['apple', 'banana', 'cherry']`. Create a dict `{ 'apple': 5, 'banana': 6... }` mapping word to length.
*   **Day 3: The `set` Data Structure (O(1) Lookups)**
    *   **Theory**: Database join logic in memory. `Intersection` and `Difference`.
    *   **Problem**: Find specific items that exist in `list_a` but NOT in `list_b` (1M items each). Benchmark `list` vs `set` speed.
*   **Day 4: Functions as First-Class Citizens**
    *   **Theory**: Passing functions as arguments (Callbacks/Delegates).
    *   **Problem**: Write a `pipeline(data, *funcs)` function that applies a dynamic list of cleaning functions to a string.
*   **Day 5: `*args` and `**kwargs` (Dynamic Arguments)**
    *   **Theory**: Handling variable inputs (like `...params` in JS/C#).
    *   **Problem**: Write a flexible logging wrapper that accepts any function signature.
*   **Day 6: Type Hinting (`typing` module)**
    *   **Theory**: Python is dynamic, but DE pipelines need strict contracts (Pydantic style).
    *   **Problem**: Refactor Day 1-5 code to use strictly typed functions (`def func(x: list[int]) -> int:`).
*   **Day 7: Weekly Capstone - The CLI Tool**
    *   **Problem**: Build a CLI tool using `argparse` that takes a file path and a "mode" (count/clean) and runs your Day 4 pipeline on it.

---

## 📅 Week 2: Memory & Performance (The "DE" Mindset)
**Theme**: "How to process 100GB on a laptop."

*   **Day 8: Generators (`yield`) - Part 1**
    *   **Theory**: Lazy evaluation. `IEnumerable<T>` in C#.
    *   **Problem**: Write a function that yields Fibonacci numbers infinitely. Stop it after 1000 items.
*   **Day 9: Generators (Streaming Files) - Part 2**
    *   **Theory**: Reading files line-by-line vs `readlines()`.
    *   **Problem**: Create a dummy 1GB text file (script it). Write a generator to stream it and count the word "error". Monitor your RAM usage.
*   **Day 10: Decorators (`@wrapper`)**
    *   **Theory**: Aspect-Oriented Programming (Middleware).
    *   **Problem**: Write a `@timer` decorator that prints how long any function takes to run.
*   **Day 11: Context Managers (`with` statement)**
    *   **Theory**: `using` statement in C#. Auto-cleanup of resources.
    *   **Problem**: Write a custom class `DatabaseConnection` that connects on `__enter__` and closes on `__exit__`.
*   **Day 12: The `itertools` Module**
    *   **Theory**: High-performance functional tools (`chain`, `groupby`).
    *   **Problem**: Flatten a list of lists `[[1,2], [3,4]]` into `[1,2,3,4]` using `itertools.chain`.
*   **Day 13: `multiprocessing` vs `threading`**
    *   **Theory**: The GIL (Global Interpreter Lock). CPU vs IO bound.
    *   **Problem**: Write a CPU-heavy script (calculating massive factorials). Run it on 1 core vs 4 cores. Measure the speedup.
*   **Day 14: Weekly Capstone - The Log Parser**
    *   **Problem**: Stream a massive log file (Generator), parse specific fields (Regex), and write "Critical" errors to a separate file (Context Manager).

---

## 📅 Week 3: Data Manipulation (Pandas/Polars)
**Theme**: "Excel on Code."

*   **Day 15: Series & DataFrames**
    *   **Theory**: Columnar data storage. Indexing.
    *   **Problem**: Load a CSV. Select specific columns. logical filtering (`df[df['age'] > 30]`).
*   **Day 16: GroupBy & Aggregations**
    *   **Theory**: SQL `GROUP BY` logic. Split-Apply-Combine.
    *   **Problem**: Load sales data. Calculate "Total Revenue" and "Average Order Value" per "Region".
*   **Day 17: Merging & Joining**
    *   **Theory**: SQL `JOIN` logic (Left, Inner, Cross).
    *   **Problem**: Join `Users` table with `Orders` table. Find users with 0 orders.
*   **Day 18: Vectorization (The Secret Sauce)**
    *   **Theory**: Why `df['a'] + df['b']` is 100x faster than a loop. SIMD instructions.
    *   **Problem**: Implement a math formula on a column using a Loop vs Vectorization. Time it.
*   **Day 19: Handling Missing Data**
    *   **Theory**: Null handling strategies (Imputation, Drop).
    *   **Problem**: Inject `NaN` into your data. Fill them with the "Mean of the column".
*   **Day 20: String Operations in Pandas**
    *   **Theory**: `df.str.contains()`, `df.str.split()`.
    *   **Problem**: Parse a column of messy emails (" John@Gmail.com ") -> ("john@gmail.com").
*   **Day 21: Weekly Capstone - The ETL Script**
    *   **Problem**: Read a messy CSV, Clean it (Schema validation), Enrich it (Join with lookup), and Save as "Clean_Data.csv".

---

## 📅 Week 4: The Real World (Files, APIs, Formats)
**Theme**: "Connecting to the outside world."

*   **Day 22: JSON & APIs (`requests`)**
    *   **Problem**: Fetch data from `jsonplaceholder.typicode.com`. Flatten nested JSON into a list of dicts.
*   **Day 23: Working with Parquet**
    *   **Theory**: Row-based (CSV) vs Column-based (Parquet) storage.
    *   **Problem**: Convert your Day 21 CSV to Parquet. Compare file size and read speed.
*   **Day 24: Interacting with S3 (MinIO)**
    *   **Theory**: Object Storage.
    *   **Problem**: Write a script to upload a file to a specific MinIO bucket using `boto3`.
*   **Day 25: Interacting with SQL (SQLAlchemy)**
    *   **Theory**: Engine, Connection, Session.
    *   **Problem**: Dump your DataFrame into a Postgres table (`to_sql`).
*   **Day 26: Environment Variables (`python-dotenv`)**
    *   **Theory**: Security. Never commit keys.
    *   **Problem**: Refactor Day 24/25 to load credentials from `.env`.
*   **Day 27: Exception Handling for Pipelines**
    *   **Theory**: Catching specific errors.
    *   **Problem**: Wrap your ETL script in `try/except` blocks. Log errors to a file, but don't crash the pipeline for one bad row.
*   **Day 28: Logging (`logging` module)**
    *   **Theory**: Print debugging vs Structured Logging.
    *   **Problem**: Replace all `print()` statements with `logger.info()` and `logger.error()`.
*   **Day 29: Unit Testing (`pytest`)**
    *   **Theory**: Testing data transformations.
    *   **Problem**: Write a test for your "Clean Email" function from Day 20.
*   **Day 30: FINAL CAPSTONE - The "Mini-Pipeline"**
    *   **Problem**: 
        1. Fetch JSON data from an API.
        2. Convert to DataFrame (Pandas/Polars).
        3. Clean/Transform.
        4. Save as Parquet to MinIO.
        5. Log everything.
    *   **Goal**: Post this repo link to LinkedIn.
