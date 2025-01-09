# mssqldba

#-- Dynamic Management Views for Azure SQL Database and SQL Server

#-- Monitor resource use
SELECT * FROM sys.dm_db_resource_stats;				
-- Azure SQL Database service tier usage statistics
													
-- For Azure SQL Managed Instance, use sys.server_resource_stats

#-- Monitor connections
SELECT * FROM sys.dm_exec_connections;				-- details about current instance or database connections


#-- Index management
-- counts of existing index operations

SELECT * FROM sys.dm_db_index_usage_stats;			

-- utilization of existing indexes
SELECT * FROM sys.dm_db_index_operational_stats 
						(NULL, NULL, NULL, NULL);	
-- last time statistics were updated for a specific index

SELECT * FROM sys.dm_db_stats_properties 
						(1893581784, 1);	
-- index fragmentation
SELECT * FROM sys.dm_db_index_physical_stats
					(NULL, NULL, NULL, NULL, NULL);	
-- details for new and potentially useful indexes 
SELECT * FROM sys.dm_db_missing_index_details;		


#-- Query Plans
-- explore the plan cache
SELECT * FROM sys.dm_exec_cached_plans;				

-- view estimated execution plans from the plan cache
SELECT * FROM sys.dm_exec_query_plan
	(0x0500FF7F99F756F020E70773B501000001000000000000000000000000000000000000000000000000000000);

-- get the last actual execution plan for a query
SELECT * FROM sys.dm_exec_query_plan_stats
	(0x0500FF7F99F756F020E70773B501000001000000000000000000000000000000000000000000000000000000);
													
													

#-- Wait Statistics
-- wait stats across the server
SELECT * FROM sys.dm_os_wait_stats;					

-- waits for a given session, but not across sessions
SELECT * FROM sys.dm_exec_session_wait_stats;		


 
# https://docs.microsoft.com/en-us/azure/azure-sql/database/monitoring-with-dmvs
 
