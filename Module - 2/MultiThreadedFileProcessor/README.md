# Multi-Threaded CSV File Processor

A beginner-level Java project that reads multiple CSV files at the same time using threads, and produces a combined sales report.

---

## What This Project Does

- Reads 3 CSV sales files **at the same time** (using multiple threads)
- Uses a **Builder Pattern** to set up configuration
- Combines all data and prints a **Sales Report**
- Saves the report to `report.txt`

---

## Requirements

You only need **ONE thing** installed:

### ✅ Java JDK 8 or higher

> If you already have Java installed, you can skip the install step below.

### How to Check if Java is Already Installed

1. Press `Windows + R`
2. Type `cmd` and press **Enter**
3. In the black window, type:

```
java -version
```

If you see something like `java version "17.0.x"` → **Java is already installed. Skip to Step 2.**

If you see `'java' is not recognized...` → **You need to install Java first.**

---

## Step 1 — Install Java (Only if Not Installed)

1. Go to this website:
   👉 https://www.oracle.com/java/technologies/downloads/

2. Download **JDK 17** (or any version 8 and above) for **Windows x64**

3. Run the downloaded `.exe` installer and click **Next → Next → Finish**

4. After installing, open `cmd` again and type `java -version` to confirm it works.

---

## Step 2 — Download / Copy This Project

Copy the entire `MultiThreadedFileProcessor` folder to your computer.

Make sure the folder looks like this:

```
MultiThreadedFileProcessor/
├── src/
│   ├── Main.java
│   ├── config/
│   │   └── ProcessorConfig.java
│   ├── model/
│   │   └── SalesRecord.java
│   ├── processor/
│   │   └── CsvFileProcessor.java
│   └── report/
│       └── ReportAggregator.java
├── data/
│   ├── sales_january.csv
│   ├── sales_february.csv
│   └── sales_march.csv
├── run.bat
└── README.md
```

---

## Step 3 — Run the Project

### Easiest Method — Double Click

1. Open the `MultiThreadedFileProcessor` folder
2. **Double-click** the file called `run.bat`
3. A black window will open, compile the code, and run it automatically

That's it! ✅

---

### Alternative Method — Using Command Prompt

1. Open the `MultiThreadedFileProcessor` folder
2. Click on the **address bar** at the top of the folder window
3. Type `cmd` and press **Enter** (this opens Command Prompt inside the folder)
4. Type this command and press **Enter**:

```
javac -d out src\Main.java src\model\SalesRecord.java src\config\ProcessorConfig.java src\processor\CsvFileProcessor.java src\report\ReportAggregator.java
```

5. Then type this and press **Enter**:

```
java -cp out Main
```

---

## Expected Output

When the program runs, you will see something like this:

```
============================================
  Multi-Threaded CSV File Processor
============================================

Configuration: ProcessorConfig{threads=3, inputFolder='data/', ...}

Found 3 CSV file(s) to process:

  -> sales_february.csv
  -> sales_january.csv
  -> sales_march.csv

Processing files concurrently...

[Thread: pool-1-thread-1] Processing: data\sales_february.csv
[Thread: pool-1-thread-2] Processing: data\sales_january.csv
[Thread: pool-1-thread-3] Processing: data\sales_march.csv
[Thread: pool-1-thread-2] Done! Parsed 8 records from: data\sales_january.csv
[Thread: pool-1-thread-3] Done! Parsed 9 records from: data\sales_march.csv
[Thread: pool-1-thread-1] Done! Parsed 8 records from: data\sales_february.csv

All threads finished. Thread pool shut down.

=======================================================
       SALES AGGREGATED REPORT
=======================================================

  Total Records Processed : 25
  Total Quantity Sold     : 915 units
  Total Revenue           : $57,650.85
  ...

Report saved to: report.txt
```

The full report is also saved in a file called **`report.txt`** inside the project folder.

---

## Troubleshooting

| Problem | Fix |
|---|---|
| `'java' is not recognized` | Java is not installed. Go to Step 1 above. |
| `'javac' is not recognized` | You installed JRE instead of JDK. Re-install **JDK** from the link in Step 1. |
| `No CSV files found` | Make sure the `data/` folder is inside `MultiThreadedFileProcessor/` and has `.csv` files. |
| Black window closes too fast | Right-click `run.bat` and click **"Run as administrator"**, or use the Command Prompt method instead. |

---

## Project Files Explained (Simple)

| File | Purpose |
|---|---|
| `Main.java` | Starting point — creates threads and runs everything |
| `ProcessorConfig.java` | Settings (threads, folder, etc.) using Builder Pattern |
| `SalesRecord.java` | Represents one row of data from a CSV file |
| `CsvFileProcessor.java` | One thread reads one CSV file using this |
| `ReportAggregator.java` | Combines all data and creates the final report |
| `data/*.csv` | Sample sales data files |
| `run.bat` | One-click script to compile and run on Windows |

---

## Adding Your Own CSV Files

You can add more `.csv` files to the `data/` folder.

Each file must follow this format (first line is the header):

```
product,category,quantity,price
Laptop,Electronics,5,999.99
T-Shirt,Clothing,20,19.99
```

The program will automatically detect and process all `.csv` files in the `data/` folder.

---

*Built with Java — No external libraries needed.*
