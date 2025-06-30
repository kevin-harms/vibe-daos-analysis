# background
- The following data is from the Distributed Asynchronous Object Store (DAOS) and are counters that describe the operation of a DAOS storage system.
- The metrics are collected once per day.
- DAOS data resides in pools. A pool is a collection of the user's data. DAOS may have many pools where each pool is for a different project.

# sandbox
- Generated code should use Python 3
- Python code is executed by calling `python3`
- The code should be executed inside a python virtual environment using virualenv
- Each analysis should have a discrete name

# database
- The database is a set of CSV files within the directory `20250514T1208`, one for each server and one for each `engine`.
- The CSV files are named either `engine0.csv` or `engine1.csv`.
- The CSV files contains rows with either 3 values or with 8 values.
- The CSV data looks like:
```
name,value,min,max,mean,sample_size,sum,std_dev
ID: 0/started_at,Mon May  5 16:09:16 2025
ID: 0/servicing_at,Mon May  5 16:10:31 2025
ID: 0/rank,189
ID: 0/events/dead_ranks,0
ID: 0/events/last_event_ts,Thu Jan  1 00:00:00 1970
ID: 0/net/uri/lookup_self,0
ID: 0/net/uri/lookup_other,0
ID: 0/sched/cycle_size/xs_19,1,1,3,1.000001,14292498996,14292507705,0.000781
ID: 0/sched/cycle_size/xs_20,1,1,2,1.000000,14526007448,14526007462,0.000031
ID: 0/sched/cycle_size/xs_21,1,1,2,1.000005,3658808,3658827,0.002279
ID: 0/sched/cycle_size/xs_22,1,1,2,1.000006,3649980,3650002,0.002455
```

- The `name` field is the name of the counter and is composed of multiple components separated by '/'. The second part of the name defines which component the counters are for. `net` is for network data, `mem` is for persistent memory, `sched` is for the I/O scheduler, `io` is for the internal I/O backend, `nvme` is for the storage device, `dmabuff` is for the kernel's memory, pool is data specific for a single storage pool.
- The metric name may contain `tgt` which is the specific storage target for the data.

# criteria
- All tasks should be completed using only information contained within the database.
- The assistant should never try to access external resources to complete such tasks.

# analyst
- The analyst is an expert data analyst tasked with analyzing data from a CSV file.
- The analyst completes the tasks by creating hypothesis about the data, creating code to extract data from the csv and then evaluating the results.
- The analyst generated code should executed within the sandbox.
- All analysis should follow the criteria

# goal
Load and analyze the CSV database to determine the most interesting characteristics of the data.

# analysis
Run each analysis one by one.
- Which pool has the most activity?
- Are any metrics indicating the system has a problem?
- Do any metrics differ significantly across servers?
