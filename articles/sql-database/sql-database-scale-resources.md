---
title: Azure SQL Database Scale Resources | Microsoft Docs
description: This article explains how to scale your database by adding or removing allocated resources.
services: sql-database
author: jovanpop-msft
ms.reviewer: carlrab
ms.service: sql-database
ms.topic: conceptual
ms.date: 07/16/2018
ms.author: jovanpop
manager: craigg
---

# Scale database resources

Azure SQL Database enables you to dynamically add more resources to your database with minimal downtime.

## Overview

When demand for your app grows from a handful of devices and customers to millions, Azure SQL Database scales on the fly with minimal downtime. Scalability is one of the most important characteristics of PaaS that enables you to dynamically add more resources to your service when needed. Azure SQL Database enables you to easily change resources (CPU power, memory, IO throughput, and storage) allocated to your databases.  
You can mitigate performance issues due to increased usage of your application that cannot be fixed using indexing or query rewrite methods. Adding more resources enables you to quickly react when your database hits the current resource limits and needs more power to handle the incoming workload. Azure SQL Database also enables you to scale-down the resources when they are not needed to lower the cost.
You don’t need to worry about purchasing hardware and changing underlying infrastructure. Scaling database can be easily done via Azure portal using a slider.

![Scale database performance](media/sql-database-scalability/scale-performance.svg)

Azure SQL Database offers a [DTU-based purchasing model](sql-database-service-tiers-dtu.md) or the [vCore-based purchasing model](sql-database-service-tiers-vcore.md). 
-	The [DTU-based purchasing model](sql-database-service-tiers-dtu.md) offers a blend of compute, memory, and IO resources in three service tiers to support lightweight to heavyweight database workloads: Basic, Standard, and Premium. Performance levels within each tier provide a different mix of these resources, to which you can add additional storage resources.
-	The [vCore-based purchasing model](sql-database-service-tiers-vcore.md) lets you choose the number of vCores, the amount or memory, and the amount and speed of storage.
You can build your first app on a small, single database at a low cost per month and then change its service tier manually or programmatically at any time to meet the needs of your solution. You can adjust performance without downtime to your app or to your customers. Dynamic scalability enables your database to transparently respond to rapidly changing resource requirements and enables you to only pay for the resources that you need when you need them.


> [!NOTE]
> Dynamic scalability is different from autoscale. Autoscale is when a service scales automatically based on criteria, whereas dynamic scalability allows for manual scaling without downtime.
>


Single Azure SQL Database supports manual dynamic scalability, but not autoscale. For a more *automatic* experience, consider using elastic pools, which allow databases to share resources in a pool based on individual database needs.
However, there are scripts that can help automate scalability for a single Azure SQL Database. For an example, see [Use PowerShell to monitor and scale a single SQL Database](scripts/sql-database-monitor-and-scale-database-powershell.md).


All three flavors of Azure SQL Database offer some ability to dynamically scale your databases:
-	In [Azure SQL Single Database](sql-database-single-database-scale.md), you can use either [DTU](sql-database-dtu-resource-limits-single-databases.md) or [vCore](sql-database-vcore-resource-limits-single-databases.md) models to define maximum amount of resources that will be assigned to each database.
-	[Azure SQL Managed Instance](sql-database-managed-instance.md) uses [vCores](/azure/sql-database/sql-database-managed-instance#vcore-based-purchasing-model-preview) mode and enables you to define maximum CPU cores and maximum of storage allocated to your instance. All databases within the instance will share the resources allocated to the instance.
-	[Azure SQL Elastic Pools](sql-database-elastic-pool-scale.md) enable you to define maximum resource limit per group of databases in the pool.

## Alternative scale methods
Scaling resources is the easiest and the most effective way to improve performance of your database without changing either database or application code.
In some cases, even the highest performance tiers and performance optimizations might not handle your workload on successful and cost-effective way. In that cases you have other options to scale your database:
-	[Read scale-out](sql-database-read-scale-out.md) is a feature available in where you are getting one read-only replica of your data where you can execute demanding read-only queries such as reports. Red-only replica will handle your read-only workload without affecting resource usage on your primary database.
-	[Database sharding](sql-database-elastic-scale-introduction.md) is a set of techniques that enables you to split your data into several databases and scale them independently.

## Next steps
- For information about improving database performance by changing database code, see [Find and apply performance recommendations](sql-database-advisor-portal.md).
- For information about letting built-in database intelligence optimize your database, see [Automatic tuning](sql-database-automatic-tuning.md).
- For information about Read Scale-out in the Azure SQL Database service, see how to [use read-only replicas to load balance read-only query workloads](sql-database-read-scale-out.md).
- For information about a Database sharding, see [Scaling out with Azure SQL Database](sql-database-elastic-scale-introduction.md).

