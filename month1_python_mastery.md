# Month 1: The "Daily Commit" Challenge (Python for DE)
**Goal:** 30 Days of Code. 30 Commits. Zero "Tutorial Hell".
**Audience:** Senior Backend Dev (C#/.NET/Node) transitioning to Data.

---

## 📅 Week 1: The "Delta" (Syntax & High-Level Structures)
**Theme**: "Stop writing C# in Python."

*   **Day 1: List Comprehensions (The "LINQ" of Python)**
    *   **Resource**: [Real Python: List Comprehensions](https://realpython.com/list-comprehension-python/)
    *   **Video**: [Corey Schafer: List Comprehensions](https://www.youtube.com/watch?v=3dt4OGnU5OM)
    *   **Theory**: Loops are for side effects. Comprehensions are for transformations (Map/Filter).
    *   **Problem**: Generate a list of 10,000 random integers. Filter only the primes. Square them.
    *   **Target**: One line of code for the logic.
*   **Day 2: Dictionary Comprehensions (HashMaps on Steroids)**
    *   **Resource**: [PEP 274 – Dict Comprehensions](https://peps.python.org/pep-0274/)
    *   **Video**: [mCoding: Dictionary Comprehensions](https://www.youtube.com/watch?v=p15p-xaxfk0)
    *   **Theory**: Rapidly building lookup tables without `.Add()`.
    *   **Problem**: Take a list of strings `['apple', 'banana', 'cherry']`. Create a dict `{ 'apple': 5, 'banana': 6... }` mapping word to length.
*   **Day 3: The `set` Data Structure (O(1) Lookups)**
    *   **Resource**: [Real Python: Sets in Python](https://realpython.com/python-sets/)
    *   **Video**: [Tech With Tim: Python Sets](https://www.youtube.com/watch?v=r3R3h5ly_8g)
    *   **Theory**: Database join logic in memory. `Intersection` and `Difference`.
    *   **Problem**: Find specific items that exist in `list_a` but NOT in `list_b` (1M items each). Benchmark `list` vs `set` speed.
*   **Day 4: Functions as First-Class Citizens**
    *   **Resource**: [Dan Bader: Functional Programming](https://dbader.org/blog/python-first-class-functions)
    *   **Video**: [ArjanCodes: Functional Programming](https://www.youtube.com/watch?v=rCXpQ0954Wc)
    *   **Theory**: Passing functions as arguments (Callbacks/Delegates).
    *   **Problem**: Write a `pipeline(data, *funcs)` function that applies a dynamic list of cleaning functions to a string.
*   **Day 5: `*args` and `**kwargs` (Dynamic Arguments)**
    *   **Resource**: [Real Python: Args and Kwargs](https://realpython.com/python-kwargs-and-args/)
    *   **Video**: [Corey Schafer: Args & Kwargs](https://www.youtube.com/watch?v=4jBJhCaNrWU)
    *   **Theory**: Handling variable inputs (like `...params` in JS/C#).
    *   **Problem**: Write a flexible logging wrapper that accepts any function signature.
*   **Day 6: Type Hinting (`typing` module)**
    *   **Resource**: [Mypy Cheat Sheet](https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html)
    *   **Video**: [ArjanCodes: Type Hinting](https://www.youtube.com/watch?v=QORvB-_mbZ0)
    *   **Theory**: Python is dynamic, but DE pipelines need strict contracts (Pydantic style).
    *   **Problem**: Refactor Day 1-5 code to use strictly typed functions (`def func(x: list[int]) -> int:`).
*   **Day 7: Weekly Capstone - The CLI Tool**
    *   **Resource**: [Argparse Tutorial](https://docs.python.org/3/howto/argparse.html)
    *   **Video**: [Tech With Tim: Argparse](https://www.youtube.com/watch?v=cdblJqEUDNo)
    *   **Problem**: Build a CLI tool using `argparse` that takes a file path and a "mode" (count/clean) and runs your Day 4 pipeline on it.

---

## 📅 Week 2: Memory & Performance (The "DE" Mindset)
**Theme**: "How to process 100GB on a laptop."

*   **Day 8: Generators (`yield`) - Part 1**
    *   **Resource**: [Real Python: Generators](https://realpython.com/introduction-to-python-generators/)
    *   **Video**: [Corey Schafer: Generators](https://www.youtube.com/watch?v=bD05uGo_sVI)
    *   **Theory**: Lazy evaluation. `IEnumerable<T>` in C#.
    *   **Problem**: Write a function that yields Fibonacci numbers infinitely. Stop it after 1000 items.
*   **Day 9: Generators (Streaming Files) - Part 2**
    *   **Resource**: [Python Tricks: Streaming Data](https://syslog.rip/2023/10/08/python-streaming/)
    *   **Video**: [ArjanCodes: Streaming Large Data](https://www.youtube.com/watch?v=4fF55qVI_1M)
    *   **Theory**: Reading files line-by-line vs `readlines()`.
    *   **Problem**: Create a dummy 1GB text file (script it). Write a generator to stream it and count the word "error". Monitor your RAM usage.
*   **Day 10: Decorators (`@wrapper`)**
    *   **Resource**: [Corey Schafer: Decorators](https://www.youtube.com/watch?v=FsAPt_9Bf3U)
    *   **Video**: [Corey Schafer: Decorators](https://www.youtube.com/watch?v=FsAPt_9Bf3U)
    *   **Theory**: Aspect-Oriented Programming (Middleware).
    *   **Problem**: Write a `@timer` decorator that prints how long any function takes to run.
*   **Day 11: Context Managers (`with` statement)**
    *   **Resource**: [Python Docs: Context Managers](https://docs.python.org/3/transform/context_managers.html)
    *   **Video**: [Corey Schafer: Context Managers](https://www.youtube.com/watch?v=-aKFIBZDfe0)
    *   **Theory**: `using` statement in C#. Auto-cleanup of resources.
    *   **Problem**: Write a custom class `DatabaseConnection` that connects on `__enter__` and closes on `__exit__`.
*   **Day 12: The `itertools` Module**
    *   **Resource**: [Itertools in Python](https://realpython.com/python-itertools/)
    *   **Video**: [Real Python: Itertools](https://www.youtube.com/watch?v=Qu3dThVPjqc)
    *   **Theory**: High-performance functional tools (`chain`, `groupby`).
    *   **Problem**: Flatten a list of lists `[[1,2], [3,4]]` into `[1,2,3,4]` using `itertools.chain`.
*   **Day 13: `multiprocessing` vs `threading`**
    *   **Resource**: [SuperFastPython: Multiprocessing](https://superfastpython.com/multiprocessing-in-python/)
    *   **Video**: [Corey Schafer: Multiprocessing](https://www.youtube.com/watch?v=fKl2JW_qrso)
    *   **Theory**: The GIL (Global Interpreter Lock). CPU vs IO bound.
    *   **Problem**: Write a CPU-heavy script (calculating massive factorials). Run it on 1 core vs 4 cores. Measure the speedup.
*   **Day 14: Weekly Capstone - The Log Parser**
    *   **Resource**: [Regex101](https://regex101.com/)
    *   **Video**: [Corey Schafer: Regex](https://www.youtube.com/watch?v=K8L6KVGG-7o)
    *   **Problem**: Stream a massive log file (Generator), parse specific fields (Regex), and write "Critical" errors to a separate file (Context Manager).

---

## 📅 Week 3: Data Manipulation (Pandas/Polars)
**Theme**: "Excel on Code."

*   **Day 15: Series & DataFrames**
    *   **Resource**: [Pandas Visual Guide](https://jalammar.github.io/gentle-visual-intro-to-pandas/)
    *   **Video**: [Keith Galli: Pandas Tutorial](https://www.youtube.com/watch?v=vmEHCJofslg)
    *   **Theory**: Columnar data storage. Indexing.
    *   **Problem**: Load a CSV. Select specific columns. logical filtering (`df[df['age'] > 30]`).
*   **Day 16: GroupBy & Aggregations**
    *   **Resource**: [Real Python: Pandas GroupBy](https://realpython.com/pandas-groupby/)
    *   **Video**: [Data School: GroupBy](https://www.youtube.com/watch?v=qy0fDqoMJx8)
    *   **Theory**: SQL `GROUP BY` logic. Split-Apply-Combine.
    *   **Problem**: Load sales data. Calculate "Total Revenue" and "Average Order Value" per "Region".
*   **Day 17: Merging & Joining**
    *   **Resource**: [Pandas Merging Guide](https://pandas.pydata.org/pandas-docs/stable/user_guide/merging.html)
    *   **Video**: [Corey Schafer: Pandas Merging](https://www.youtube.com/watch?v=jycKLq540Hk)
    *   **Theory**: SQL `JOIN` logic (Left, Inner, Cross).
    *   **Problem**: Join `Users` table with `Orders` table. Find users with 0 orders.
*   **Day 18: Vectorization (The Secret Sauce)**
    *   **Resource**: [Benefit of Vectorization](https://engineering.upside.com/a-beginners-guide-to-optimizing-pandas-code-for-speed-c09ef2c6a4d6)
    *   **Video**: [PyData: Vectorization](https://www.youtube.com/watch?v=nxWginnBklU)
    *   **Theory**: Why `df['a'] + df['b']` is 100x faster than a loop. SIMD instructions.
    *   **Problem**: Implement a math formula on a column using a Loop vs Vectorization. Time it.
*   **Day 19: Handling Missing Data**
    *   **Resource**: [Handling Missing Data](https://pandas.pydata.org/docs/user_guide/missing_data.html)
    *   **Video**: [Data School: Missing Data](https://www.youtube.com/watch?v=fCMrO_VzeL8)
    *   **Theory**: Null handling strategies (Imputation, Drop).
    *   **Problem**: Inject `NaN` into your data. Fill them with the "Mean of the column".
*   **Day 20: String Operations in Pandas**
    *   **Resource**: [Pandas Text Data](https://pandas.pydata.org/docs/user_guide/text.html)
    *   **Video**: [Keith Galli: Pandas String Ops](https://www.youtube.com/watch?v=b2q5W3X-O_Y)
    *   **Theory**: `df.str.contains()`, `df.str.split()`.
    *   **Problem**: Parse a column of messy emails (" John@Gmail.com ") -> ("john@gmail.com").
*   **Day 21: Weekly Capstone - The ETL Script**
    *   **Resource**: [Polars User Guide](https://pola-rs.github.io/polars-book/user-guide/)
    *   **Video**: [Ritchie Vink: Polars Introduction](https://www.youtube.com/watch?v=t1kQLkQd26A)
    *   **Problem**: Read a messy CSV, Clean it (Schema validation), Enrich it (Join with lookup), and Save as "Clean_Data.csv".

---

## 📅 Week 4: The Real World (Files, APIs, Formats)
**Theme**: "Connecting to the outside world."

*   **Day 22: JSON & APIs (`requests`)**
    *   **Resource**: [Real Python: Python Requests](https://realpython.com/python-requests/)
    *   **Video**: [Corey Schafer: Requests Module](https://www.youtube.com/watch?v=tb8gHvYlCFs)
    *   **Problem**: Fetch data from `jsonplaceholder.typicode.com`. Flatten nested JSON into a list of dicts.
*   **Day 23: Working with Parquet**
    *   **Resource**: [Apache Parquet Docs](https://parquet.apache.org/documentation/latest/)
    *   **Video**: [Databricks: What is Parquet?](https://www.youtube.com/watch?v=_Bm0T_4QGQA)
    *   **Theory**: Row-based (CSV) vs Column-based (Parquet) storage.
    *   **Problem**: Convert your Day 21 CSV to Parquet. Compare file size and read speed.
*   **Day 24: Interacting with S3 (MinIO)**
    *   **Resource**: [Boto3 Documentation](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/quickstart.html)
    *   **Video**: [Be A Better Dev: Upload to S3](https://www.youtube.com/watch?v=q6e02D81tEw)
    *   **Theory**: Object Storage.
    *   **Problem**: Write a script to upload a file to a specific MinIO bucket using `boto3`.
*   **Day 25: Interacting with SQL (SQLAlchemy)**
    *   **Resource**: [SQLAlchemy Tutorial](https://docs.sqlalchemy.org/en/14/tutorial/)
    *   **Video**: [Corey Schafer: SQLAlchemy](https://www.youtube.com/watch?v=akYYbGYz7UE)
    *   **Theory**: Engine, Connection, Session.
    *   **Problem**: Dump your DataFrame into a Postgres table (`to_sql`).
*   **Day 26: Environment Variables (`python-dotenv`)**
    *   **Resource**: [12 Factor App: Config](https://12factor.net/config)
    *   **Video**: [NetworkChuck: Environment Variables](https://www.youtube.com/watch?v=5iWhQWVXosU)
    *   **Theory**: Security. Never commit keys.
    *   **Problem**: Refactor Day 24/25 to load credentials from `.env`.
*   **Day 27: Exception Handling for Pipelines**
    *   **Resource**: [Python: Errors and Exceptions](https://docs.python.org/3/tutorial/errors.html)
    *   **Video**: [Corey Schafer: Try/Except](https://www.youtube.com/watch?v=NIWwJbo-9_8)
    *   **Theory**: Catching specific errors.
    *   **Problem**: Wrap your ETL script in `try/except` blocks. Log errors to a file, but don't crash the pipeline for one bad row.
*   **Day 28: Logging (`logging` module)**
    *   **Resource**: [Python Logging Guide](https://realpython.com/python-logging/)
    *   **Video**: [Corey Schafer: Logging](https://www.youtube.com/watch?v=-ARI4Cz-awo)
    *   **Theory**: Print debugging vs Structured Logging.
    *   **Problem**: Replace all `print()` statements with `logger.info()` and `logger.error()`.
*   **Day 29: Unit Testing (`pytest`)**
    *   **Resource**: [Pytest: Getting Started](https://docs.pytest.org/en/7.1.x/getting-started.html)
    *   **Video**: [ArjanCodes: PyTest Guide](https://www.youtube.com/watch?v=cHYq1MRV2IA)
    *   **Theory**: Testing data transformations.
    *   **Problem**: Write a test for your "Clean Email" function from Day 20.
*   **Day 30: FINAL CAPSTONE - The "Mini-Pipeline"**
    *   **Resource**: [Structuring Python Projects](https://docs.python-guide.org/writing/structure/)
    *   **Video**: [ArjanCodes: Project Structure](https://www.youtube.com/watch?v=trG_x4279_I)
    *   **Problem**: 
        1. Fetch JSON data from an API.
        2. Convert to DataFrame (Pandas/Polars).
        3. Clean/Transform.
        4. Save as Parquet to MinIO.
        5. Log everything.
    *   **Goal**: Post this repo link to LinkedIn.
