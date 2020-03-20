---
title: Exemple de configuration de copie en bloc
ms.date: 03/30/2017
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.openlocfilehash: 80350d112da03c00e422432ce271ca5ea3ac58ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148840"
---
# <a name="bulk-copy-example-setup"></a><span data-ttu-id="291ef-102">Exemple de configuration de copie en bloc</span><span class="sxs-lookup"><span data-stu-id="291ef-102">Bulk Copy Example Setup</span></span>
<span data-ttu-id="291ef-103">La classe <xref:System.Data.SqlClient.SqlBulkCopy> peut être utilisée pour écrire des données uniquement sur les tables SQL Server.</span><span class="sxs-lookup"><span data-stu-id="291ef-103">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="291ef-104">Les exemples de code présentés dans cette rubrique utilisent l’exemple de base de données SQL Server **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="291ef-104">The code samples shown in this topic use the SQL Server sample database, **AdventureWorks**.</span></span> <span data-ttu-id="291ef-105">Pour éviter de modifier les exemples de code des tables existantes, écrivez les données dans des tables que vous aurez préalablement créées.</span><span class="sxs-lookup"><span data-stu-id="291ef-105">To avoid altering the existing tables code samples write data to tables that you must create first.</span></span>  
  
 <span data-ttu-id="291ef-106">Les tables **BulkCopyDemoMatchingColumns** et **BulkCopyDemoDifferentColumns** sont basées sur la table **AdventureWorks** \*\* Production.Products\*\*.</span><span class="sxs-lookup"><span data-stu-id="291ef-106">The **BulkCopyDemoMatchingColumns** and **BulkCopyDemoDifferentColumns** tables are both based on the **AdventureWorks** **Production.Products** table.</span></span> <span data-ttu-id="291ef-107">Dans les exemples de code qui utilisent ces tables, les données sont ajoutées à partir de la table **Production.Products** à l’un de ces exemples de tables.</span><span class="sxs-lookup"><span data-stu-id="291ef-107">In code samples that use these tables, data is added from the **Production.Products** table to one of these sample tables.</span></span> <span data-ttu-id="291ef-108">La table **BulkCopyDemoDifferentColumns** est utilisée quand l’exemple illustre comment mapper des colonnes de données source à la table de destination. **BulkCopyDemoMatchingColumns** est utilisé pour la plupart des autres exemples.</span><span class="sxs-lookup"><span data-stu-id="291ef-108">The **BulkCopyDemoDifferentColumns** table is used when the sample illustrates how to map columns from the source data to the destination table; **BulkCopyDemoMatchingColumns** is used for most other samples.</span></span>  
  
 <span data-ttu-id="291ef-109">Certains exemples de code montrent comment utiliser une classe <xref:System.Data.SqlClient.SqlBulkCopy> pour écrire dans plusieurs tables.</span><span class="sxs-lookup"><span data-stu-id="291ef-109">A few of the code samples demonstrate how to use one <xref:System.Data.SqlClient.SqlBulkCopy> class to write to multiple tables.</span></span> <span data-ttu-id="291ef-110">Pour ces échantillons, les tables **BulkCopyDemoOrderHeader** et **BulkCopyDemoOrderDetail** sont utilisées comme tables de destination.</span><span class="sxs-lookup"><span data-stu-id="291ef-110">For these samples, the **BulkCopyDemoOrderHeader** and **BulkCopyDemoOrderDetail** tables are used as the destination tables.</span></span> <span data-ttu-id="291ef-111">Ces tables sont basées sur les tables **Sales.SalesOrderHeader** et **Sales.SalesOrderDetail** dans **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="291ef-111">These tables are based on the **Sales.SalesOrderHeader** and **Sales.SalesOrderDetail** tables in **AdventureWorks**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="291ef-112">Les exemples de code **SqlBulkCopy** sont fournis uniquement pour illustrer la syntaxe de l’utilisation de **SqlBulkCopy**.</span><span class="sxs-lookup"><span data-stu-id="291ef-112">The **SqlBulkCopy** code samples are provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="291ef-113">Si les tables source et de destination se trouvent dans la même instance SQL Server, il est plus facile et plus rapide d’utiliser une instruction Transact-SQL `INSERT … SELECT` pour copier les données.</span><span class="sxs-lookup"><span data-stu-id="291ef-113">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
## <a name="table-setup"></a><span data-ttu-id="291ef-114">Configuration de table</span><span class="sxs-lookup"><span data-stu-id="291ef-114">Table Setup</span></span>  
 <span data-ttu-id="291ef-115">Pour créer les tables nécessaires à la bonne exécution des exemples de code, vous devez exécuter les instructions Transact-SQL suivantes dans une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="291ef-115">To create the tables necessary for the code samples to run correctly, you must run the following Transact-SQL statements in a SQL Server database.</span></span>  
  
```sql
USE AdventureWorks  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoMatchingColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoMatchingColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoMatchingColumns]([ProductID] [int] IDENTITY(1,1) NOT NULL,  
    [Name] [nvarchar](50) NOT NULL,  
    [ProductNumber] [nvarchar](25) NOT NULL,  
 CONSTRAINT [PK_ProductID] PRIMARY KEY CLUSTERED  
(  
    [ProductID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoDifferentColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoDifferentColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoDifferentColumns]([ProdID] [int] IDENTITY(1,1) NOT NULL,  
    [ProdNum] [nvarchar](25) NOT NULL,  
    [ProdName] [nvarchar](50) NOT NULL,  
 CONSTRAINT [PK_ProdID] PRIMARY KEY CLUSTERED  
(  
    [ProdID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderHeader]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderHeader]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderHeader]([SalesOrderID] [int] IDENTITY(1,1) NOT NULL,  
    [OrderDate] [datetime] NOT NULL,  
    [AccountNumber] [nvarchar](15) NULL,  
 CONSTRAINT [PK_SalesOrderID] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderDetail]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderDetail]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderDetail]([SalesOrderID] [int] NOT NULL,  
    [SalesOrderDetailID] [int] NOT NULL,  
    [OrderQty] [smallint] NOT NULL,  
    [ProductID] [int] NOT NULL,  
    [UnitPrice] [money] NOT NULL,  
 CONSTRAINT [PK_LineNumber] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC,  
    [SalesOrderDetailID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
```  
  
## <a name="see-also"></a><span data-ttu-id="291ef-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="291ef-116">See also</span></span>

- [<span data-ttu-id="291ef-117">Opérations de copie en vrac dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="291ef-117">Bulk Copy Operations in SQL Server</span></span>](bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="291ef-118">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="291ef-118">ADO.NET Overview</span></span>](../ado-net-overview.md)
