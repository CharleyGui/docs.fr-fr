---
title: Opérations de copie en bloc dans SQL Server
description: Apprenez à utiliser la classe SqlBulkCopy pour écrire des solutions de code managé qui copient en bloc des fichiers volumineux dans des tables ou des vues dans des bases de données SQL Server.
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: 43d63f3671ea8ff05da3e10580c2784fa3aae581
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197428"
---
# <a name="bulk-copy-operations-in-sql-server"></a><span data-ttu-id="8472a-103">Opérations de copie en bloc dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="8472a-103">Bulk Copy Operations in SQL Server</span></span>

<span data-ttu-id="8472a-104">Microsoft SQL Server inclut un utilitaire en ligne de commande connu, **bcp**, pour rapidement copier en bloc des fichiers volumineux dans des tables ou des vues de bases de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8472a-104">Microsoft SQL Server includes a popular command-line utility named **bcp** for quickly bulk copying large files into tables or views in SQL Server databases.</span></span> <span data-ttu-id="8472a-105">La classe <xref:System.Data.SqlClient.SqlBulkCopy> vous permet d’écrire des solutions de code managé, qui fournissent des fonctionnalités similaires.</span><span class="sxs-lookup"><span data-stu-id="8472a-105">The <xref:System.Data.SqlClient.SqlBulkCopy> class allows you to write managed code solutions that provide similar functionality.</span></span> <span data-ttu-id="8472a-106">Il existe d’autres façons de charger des données dans une table SQL Server (instructions INSERT, par exemple) mais <xref:System.Data.SqlClient.SqlBulkCopy> offre de meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="8472a-106">There are other ways to load data into a SQL Server table (INSERT statements, for example) but <xref:System.Data.SqlClient.SqlBulkCopy> offers a significant performance advantage over them.</span></span>  
  
 <span data-ttu-id="8472a-107">La classe <xref:System.Data.SqlClient.SqlBulkCopy> peut être utilisée pour écrire des données uniquement sur les tables SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8472a-107">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="8472a-108">Toutefois, la source de données n'est pas limitée à SQL Server ; n'importe quelle source de données peut être utilisée, pour autant que les données puissent être chargées dans une instance de <xref:System.Data.DataTable> ou lues avec une instance de <xref:System.Data.IDataReader>.</span><span class="sxs-lookup"><span data-stu-id="8472a-108">But the data source is not limited to SQL Server; any data source can be used, as long as the data can be loaded to a <xref:System.Data.DataTable> instance or read with a <xref:System.Data.IDataReader> instance.</span></span>  
  
 <span data-ttu-id="8472a-109">À l'aide de la classe <xref:System.Data.SqlClient.SqlBulkCopy>, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="8472a-109">Using the <xref:System.Data.SqlClient.SqlBulkCopy> class, you can perform:</span></span>  
  
- <span data-ttu-id="8472a-110">Une opération unique de copie en bloc</span><span class="sxs-lookup"><span data-stu-id="8472a-110">A single bulk copy operation</span></span>  
  
- <span data-ttu-id="8472a-111">Plusieurs opérations de copie en bloc</span><span class="sxs-lookup"><span data-stu-id="8472a-111">Multiple bulk copy operations</span></span>  
  
- <span data-ttu-id="8472a-112">Une opération de copie en bloc dans une transaction</span><span class="sxs-lookup"><span data-stu-id="8472a-112">A bulk copy operation within a transaction</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8472a-113">Quand vous utilisez .NET Framework version 1.1 ou antérieure (ne prenant pas en charge la classe <xref:System.Data.SqlClient.SqlBulkCopy>), vous pouvez exécuter l’instruction SQL Server Transact-SQL **BULK INSERT** à l’aide de l’objet <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="8472a-113">When using .NET Framework version 1.1 or earlier (which does not support the <xref:System.Data.SqlClient.SqlBulkCopy> class), you can execute the SQL Server Transact-SQL **BULK INSERT** statement using the <xref:System.Data.SqlClient.SqlCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8472a-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8472a-114">In This Section</span></span>  

 [<span data-ttu-id="8472a-115">Configuration de l’exemple de copie en bloc</span><span class="sxs-lookup"><span data-stu-id="8472a-115">Bulk Copy Example Setup</span></span>](bulk-copy-example-setup.md)  
 <span data-ttu-id="8472a-116">Décrit les tables utilisées dans les exemples de copie en bloc et fournit des scripts SQL pour créer les tables dans la base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="8472a-116">Describes the tables used in the bulk copy examples and provides SQL scripts for creating the tables in the AdventureWorks database.</span></span>  
  
 [<span data-ttu-id="8472a-117">Opérations de copie en bloc uniques</span><span class="sxs-lookup"><span data-stu-id="8472a-117">Single Bulk Copy Operations</span></span>](single-bulk-copy-operations.md)  
 <span data-ttu-id="8472a-118">Décrit comment effectuer une seule copie en bloc de données dans une instance de SQL Server à l’aide de la classe <xref:System.Data.SqlClient.SqlBulkCopy> et comment effectuer l’opération de copie en bloc à l’aide d’instructions Transact-SQL et de la classe <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="8472a-118">Describes how to do a single bulk copy of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class, and how to perform the bulk copy operation using Transact-SQL statements and the <xref:System.Data.SqlClient.SqlCommand> class.</span></span>  
  
 [<span data-ttu-id="8472a-119">Plusieurs opérations de copie en bloc</span><span class="sxs-lookup"><span data-stu-id="8472a-119">Multiple Bulk Copy Operations</span></span>](multiple-bulk-copy-operations.md)  
 <span data-ttu-id="8472a-120">Décrit comment effectuer plusieurs opérations de copie en bloc de données dans une instance de SQL Server à l’aide de la classe <xref:System.Data.SqlClient.SqlBulkCopy>.</span><span class="sxs-lookup"><span data-stu-id="8472a-120">Describes how to do multiple bulk copy operations of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span>  
  
 [<span data-ttu-id="8472a-121">Transaction et opérations de copie en bloc</span><span class="sxs-lookup"><span data-stu-id="8472a-121">Transaction and Bulk Copy Operations</span></span>](transaction-and-bulk-copy-operations.md)  
 <span data-ttu-id="8472a-122">Décrit comment effectuer une opération de copie en bloc dans une transaction, y compris la validation ou la restauration de la transaction.</span><span class="sxs-lookup"><span data-stu-id="8472a-122">Describes how to perform a bulk copy operation within a transaction, including how to commit or rollback the transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8472a-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8472a-123">See also</span></span>

- [<span data-ttu-id="8472a-124">SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8472a-124">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="8472a-125">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8472a-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
