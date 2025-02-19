---
description: "Configuration Functions (Transact-SQL)"
title: "Configuration Functions (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "07/24/2017"
ms.prod: sql
ms.prod_service: "database-engine, sql-database"
ms.reviewer: ""
ms.technology: t-sql
ms.topic: reference
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "functions [SQL Server], configuration"
  - "configuration options [SQL Server], functions"
  - "current configuration information"
  - "configuration functions [SQL Server]"
ms.assetid: 066f15e7-3406-437e-93c4-3f247c529169
author: markingmyname
ms.author: maghan
---
# Configuration Functions (Transact-SQL)
[!INCLUDE [SQL Server Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/sql-asdb-asdbmi.md)]

These scalar functions return information about current configuration option settings:
  
- [@@DATEFIRST](../../t-sql/functions/datefirst-transact-sql.md)
- [@@DBTS](../../t-sql/functions/dbts-transact-sql.md)
- [@@LANGID](../../t-sql/functions/langid-transact-sql.md)
- [@@LANGUAGE](../../t-sql/functions/language-transact-sql.md)
- [@@LOCK_TIMEOUT](../../t-sql/functions/lock-timeout-transact-sql.md)
- [@@MAX_CONNECTIONS](../../t-sql/functions/max-connections-transact-sql.md)
- [@@MAX_PRECISION](../../t-sql/functions/max-precision-transact-sql.md)
- [@@NESTLEVEL](../../t-sql/functions/nestlevel-transact-sql.md)
- [@@OPTIONS](../../t-sql/functions/options-transact-sql.md)
- [@@REMSERVER](../../t-sql/functions/remserver-transact-sql.md)
- [@@SERVERNAME](../../t-sql/functions/servername-transact-sql.md)
- [@@SERVICENAME](../../t-sql/functions/servicename-transact-sql.md)
- [@@SPID](../../t-sql/functions/spid-transact-sql.md)
- [@@TEXTSIZE](../../t-sql/functions/textsize-transact-sql.md)
- [@@VERSION](../../t-sql/functions/version-transact-sql-configuration-functions.md)

All configuration functions operate in a nondeterministic way. In other words, these functions do not always return the same results every time they are called, even with the same set of input values. See [Deterministic and Nondeterministic Functions](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md) for more information about function determinism.
  
## See also

[Functions &#40;Transact-SQL&#41;](../../t-sql/functions/functions.md)
