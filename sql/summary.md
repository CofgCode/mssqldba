#Cached Query Plans  
## sys.dm_exec_cached_plans
Returns a row for each query plan that is cached by SQL Server for faster query execution. You can use
this dynamic management view to find cached query plans, cached query text, the amount of memory
taken by cached plans, and the reuse count of the cached plans.

## sys.dm_exec_sql_text
Returns the text of the SQL batch that is identified by the specified sql_handle.

## sys.dm_exec_query_plan_stats
Returns the equivalent of the last known actual execution plan for a previously cached query plan.
Queries with CPU times
##  sys.dm_exec_query_stats
Returns aggregate performance statistics for cached query plans in SQL Server. The view contains one
row per query statement within the cached plan, and the lifetime of the rows are tied to the plan itself.
When a plan is removed from the cache, the corresponding rows are eliminated from this view.

## sys.dm_exec_procedure_stats
Returns aggregate performance statistics for cached stored procedures. The view returns one row for
each cached stored procedure plan, and the lifetime of the row is as long as the stored procedure
remains cached. When a stored procedure is removed from the cache, the corresponding row is
eliminated from this view.
Find still running sessions (right now)

## sys.dm_exec_requests
Returns information about each request that is executing in SQL Server.
Current active sessions right now

## sys.dm_exec_connections
Returns information about the connections established to this instance of SQL Server and the details of
each connection. Returns server wide connection information for SQL Server. Returns current database
connection information for SQL Database.
Data and log I/O usage

## sys.dm_db_resource_stats (Azure SQL Database)
Returns CPU, I/O, and memory consumption for an Azure SQL Database database or an Azure SQL
Managed Instance. One row exists for every 15 seconds, even if there is no activity. Historical data is
maintained for approximately one hour.sys.resource_stats (all databases – must be in "master" database in Azure SQL Database
when executing it).
Returns CPU usage and storage data for an Azure SQL Database. The data is collected and aggregated
within five-minute intervals. For each user database, there is one row for every five-minute reporting
window in which there is a change in resource consumption. The data returned includes CPU usage,
storage size change, and database SKU modification. Idle databases with no changes may not have rows
for every five-minute interval. Historical data is retained for approximately 14 days.

## sys.server_resource_stats (Managed Instance)
Returns CPU usage, IO, and storage data for Azure SQL Managed Instance. The data is collected and
aggregated within five-minute intervals. There is one row for every 15 seconds reporting. The data
returned includes CPU usage, storage size, IO utilization, and SKU. Historical data is retained for
approximately 14 days.

## sys.elastic_pool_resource_stats (elastic pool databases)
Returns resource usage statistics for all the elastic pools in a SQL Database server. For each elastic pool,
there is one row for each 15 second reporting window (four rows per minute). This includes CPU, IO,
Log, storage consumption and concurrent request/session utilization by all databases in the pool. This
data is retained for 14 days.

## sys.resource_usage
Provides hourly summary of resource usage data for user databases in the current server. Historical data
is retained for 90 days.
For each user database, there is one row for every hour in continuous fashion. Even if the database was
idle during that hour, there is one row, and the usage_in_seconds value for that database will be 0.
Storage usage and SKU information is rolled up for the hour appropriately.

## sys.dm_user_db_resource_governance
Returns actual configuration and capacity settings used by resource governance mechanisms in the
current database or elastic pool.

## sys.dm_os_job_object
Returns a single row describing the configuration of the job object that manages the SQL Server process,
as well as certain resource consumption statistics at the job object level.
A job object is a Windows construct that implements CPU, memory, and IO resource governance at the
operating system level.

##  sys.dm_io_virtual_file_stats(null, null) –database_id and file_id
Returns I/O statistics for data and log files.

##  sys.dm_os_performance_counters
Returns a row per performance counter maintained by the server.

## Find long running transactions

## sys.dm_tran_active_transactions
Returns information about transactions for the instance of SQL Server.

## Indexes

## sys.dm_db_missing_index_details
Returns detailed information about missing indexes, excluding spatial indexes.
In Azure SQL Database, DMVs cannot expose information that would impact database containment or
expose information about other databases the user has access to.

## sys.dm_db_missing_index_group_stats
Returns summary information about groups of missing indexes, excluding spatial indexes.
In Azure SQL Database, DMVs cannot expose information that would impact database containment or
expose information about other databases the user has access to.

## sys.dm_db_missing_index_groups
This DMV returns information about indexes that are missing in a specific index group, except for spatial
indexes.
In Azure SQL Database, DMVs cannot expose information that would impact database containment or
expose information about other databases the user has access to.

## sys.dm_db_missing_index_group_stats_query
Returns information about queries that needed a missing index from groups of missing indexes,
excluding spatial indexes. More than one query may be returned per missing index group. One missing
index group may have several queries that needed the same index.
In Azure SQL Database, DMVs cannot expose information that would impact database containment or
expose information about other databases the user has access to.

## sys.dm_db_index_physical_stats
Returns size and fragmentation information for the data and indexes of the specified table or view in
SQL Server.
For an index, one row is returned for each level of the B-tree in each partition.
For a heap, one row is returned for the IN_ROW_DATA allocation unit of each partition.

## Tempdb Database

## sys.dm_db_session_space_usage
Returns the number of pages allocated and deallocated by each session for the database.
Internal objects are only in tempdb.sys.dm_db_task_space_usage
Returns page allocation and deallocation activity by task for the database.
Internal objects are only in tempdb.

## Wait stats

## sys.dm_os_wait_stats
Returns information about all the waits encountered by threads that executed.
You can use this aggregated view to diagnose performance issues with SQL Server and also with specific
queries and batches.
sys.dm_exec_session_wait_stats provides similar information by session.

## sys.dm_db_wait_stats
Returns information about all the waits encountered by threads that executed during operation. You
can use this aggregated view to diagnose performance issues with Azure SQL Database and also with
specific queries and batches.
Specific types of wait times during query execution can indicate bottlenecks or stall points within the
query. Similarly, high wait times, or wait counts server wide can indicate bottlenecks or hot spots in
interaction query interactions within the server instance.
For example, lock waits indicate data contention by queries; page IO latch waits indicate slow IO
response times; page latch update waits indicate incorrect file layout.

## sys.dm_os_waiting_tasks
Returns information about the wait queue of tasks that are waiting on some resource.

#Resource governance

## sys.dm_resource_governor_resource_pools
Returns information about the current resource pool state, the current configuration of resource pools,
and resource pool statistics.

## sys.dm_resource_governor_workload_groups
Returns workload group statistics and the current in-memory configuration of the workload
group
