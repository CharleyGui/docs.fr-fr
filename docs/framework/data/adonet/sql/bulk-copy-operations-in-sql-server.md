---
title: Opérations de copie en bloc dans SQL Server
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: e538e48400d955a0013a12dbf2d10f1f96c3ddfe
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649546"
---
# <a name="bulk-copy-operations-in-sql-server"></a><span data-ttu-id="b8016-102">Opérations de copie en bloc dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="b8016-102">Bulk Copy Operations in SQL Server</span></span>
<span data-ttu-id="b8016-103">Microsoft SQL Server inclut un utilitaire de ligne de commande connu nommé **bcp** pour rapidement copier en bloc des fichiers volumineux dans des tables ou vues dans les bases de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b8016-103">Microsoft SQL Server includes a popular command-line utility named **bcp** for quickly bulk copying large files into tables or views in SQL Server databases.</span></span> <span data-ttu-id="b8016-104">La classe <xref:System.Data.SqlClient.SqlBulkCopy> vous permet d'écrire des solutions de code managé qui offrent une fonctionnalité similaire.</span><span class="sxs-lookup"><span data-stu-id="b8016-104">The <xref:System.Data.SqlClient.SqlBulkCopy> class allows you to write managed code solutions that provide similar functionality.</span></span> <span data-ttu-id="b8016-105">Il existe d'autres manières de charger des données dans une table SQL Server (par exemple, des instructions INSERT) mais <xref:System.Data.SqlClient.SqlBulkCopy> présente un avantage sensible sur le plan des performances.</span><span class="sxs-lookup"><span data-stu-id="b8016-105">There are other ways to load data into a SQL Server table (INSERT statements, for example) but <xref:System.Data.SqlClient.SqlBulkCopy> offers a significant performance advantage over them.</span></span>  
  
 <span data-ttu-id="b8016-106">La classe <xref:System.Data.SqlClient.SqlBulkCopy> permet d'écrire des données uniquement dans des tables SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b8016-106">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="b8016-107">Toutefois, la source de données n'est pas limitée à SQL Server ; n'importe quelle source de données peut être utilisée, pour autant que les données puissent être chargées dans une instance de <xref:System.Data.DataTable> ou lues avec une instance de <xref:System.Data.IDataReader>.</span><span class="sxs-lookup"><span data-stu-id="b8016-107">But the data source is not limited to SQL Server; any data source can be used, as long as the data can be loaded to a <xref:System.Data.DataTable> instance or read with a <xref:System.Data.IDataReader> instance.</span></span>  
  
 <span data-ttu-id="b8016-108">La classe <xref:System.Data.SqlClient.SqlBulkCopy> vous permet d'effectuer :</span><span class="sxs-lookup"><span data-stu-id="b8016-108">Using the <xref:System.Data.SqlClient.SqlBulkCopy> class, you can perform:</span></span>  
  
- <span data-ttu-id="b8016-109">une opération unique de copie en bloc ;</span><span class="sxs-lookup"><span data-stu-id="b8016-109">A single bulk copy operation</span></span>  
  
- <span data-ttu-id="b8016-110">plusieurs opérations de copie en bloc ;</span><span class="sxs-lookup"><span data-stu-id="b8016-110">Multiple bulk copy operations</span></span>  
  
- <span data-ttu-id="b8016-111">une opération de copie en bloc à l'intérieur d'une transaction.</span><span class="sxs-lookup"><span data-stu-id="b8016-111">A bulk copy operation within a transaction</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8016-112">Lorsque vous utilisez .NET Framework version 1.1 ou antérieure (qui ne prend pas en charge la <xref:System.Data.SqlClient.SqlBulkCopy> classe), vous pouvez exécuter SQL Server Transact-SQL **BULK INSERT** à l’aide de l’instruction la <xref:System.Data.SqlClient.SqlCommand> objet.</span><span class="sxs-lookup"><span data-stu-id="b8016-112">When using .NET Framework version 1.1 or earlier (which does not support the <xref:System.Data.SqlClient.SqlBulkCopy> class), you can execute the SQL Server Transact-SQL **BULK INSERT** statement using the <xref:System.Data.SqlClient.SqlCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b8016-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b8016-113">In This Section</span></span>  
 [<span data-ttu-id="b8016-114">Exemple de configuration de copie en bloc</span><span class="sxs-lookup"><span data-stu-id="b8016-114">Bulk Copy Example Setup</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 <span data-ttu-id="b8016-115">Décrit les tables utilisées dans les exemples de copie en bloc et fournit des scripts SQL pour créer les tables dans la base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b8016-115">Describes the tables used in the bulk copy examples and provides SQL scripts for creating the tables in the AdventureWorks database.</span></span>  
  
 [<span data-ttu-id="b8016-116">Opérations uniques de copie en bloc</span><span class="sxs-lookup"><span data-stu-id="b8016-116">Single Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 <span data-ttu-id="b8016-117">Décrit comment effectuer une copie en bloc unique de données dans une instance de SQL Server à l'aide de la classe <xref:System.Data.SqlClient.SqlBulkCopy> et comment effectuer l'opération de copie en bloc à l'aide d'instructions Transact-SQL et de la classe <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="b8016-117">Describes how to do a single bulk copy of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class, and how to perform the bulk copy operation using Transact-SQL statements and the <xref:System.Data.SqlClient.SqlCommand> class.</span></span>  
  
 [<span data-ttu-id="b8016-118">Plusieurs opérations de copie en bloc</span><span class="sxs-lookup"><span data-stu-id="b8016-118">Multiple Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 <span data-ttu-id="b8016-119">Décrit comment effectuer plusieurs opérations de copie en bloc de données dans une instance de SQL Server à l'aide de la classe <xref:System.Data.SqlClient.SqlBulkCopy>.</span><span class="sxs-lookup"><span data-stu-id="b8016-119">Describes how to do multiple bulk copy operations of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span>  
  
 [<span data-ttu-id="b8016-120">Transaction et opérations de copie en bloc</span><span class="sxs-lookup"><span data-stu-id="b8016-120">Transaction and Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 <span data-ttu-id="b8016-121">Décrit comment effectuer une opération de copie en bloc à l'intérieur d'une transaction, y compris comment valider ou annuler la transaction.</span><span class="sxs-lookup"><span data-stu-id="b8016-121">Describes how to perform a bulk copy operation within a transaction, including how to commit or rollback the transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8016-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8016-122">See also</span></span>

- [<span data-ttu-id="b8016-123">SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b8016-123">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)
- [<span data-ttu-id="b8016-124">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="b8016-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
