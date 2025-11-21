📊 Detailed Comparison
Feature	| Savepoint	| Checkpoint
|-|-|-|
Purpose	| To roll back part of a transaction	| To speed up crash recovery
Scope	| Within a single transaction	| Entire database system
Who Controls	| Application Programmer (user)	| DBMS (system)
Syntax	| SAVEPOINT point_name; ROLLBACK TO point_name;	| Automatic or admin-triggered
Persistence	| Temporary - exists only during transaction |	Permanent - written to disk
