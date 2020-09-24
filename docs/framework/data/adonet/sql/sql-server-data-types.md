---
title: Types de données SQL Server et ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: db4618ac624ea8401cab682a8c21d8f23c253d05
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155456"
---
# <a name="sql-server-data-types-and-adonet"></a><span data-ttu-id="454e3-102">Types de données SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="454e3-102">SQL Server Data Types and ADO.NET</span></span>

<span data-ttu-id="454e3-103">SQL Server et le .NET Framework sont basés sur des systèmes de types différents, ce qui peut entraîner une perte de données potentielle.</span><span class="sxs-lookup"><span data-stu-id="454e3-103">SQL Server and the .NET Framework are based on different type systems, which can result in potential data loss.</span></span> <span data-ttu-id="454e3-104">Afin de protéger l’intégrité des données, le fournisseur de données .NET Framework pour SQL Server (<xref:System.Data.SqlClient>) fournit des méthodes d’accesseur typé pour utiliser les données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="454e3-104">To preserve data integrity, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides typed accessor methods for working with SQL Server data.</span></span> <span data-ttu-id="454e3-105">Vous pouvez utiliser les énumérations dans les classes <xref:System.Data.SqlDbType> pour spécifier les types de données <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="454e3-105">You can use the enumerations in the <xref:System.Data.SqlDbType> classes to specify <xref:System.Data.SqlClient.SqlParameter> data types.</span></span>  
  
 <span data-ttu-id="454e3-106">Pour plus d’informations et pour obtenir un tableau décrivant les mappages de types de données entre SQL Server et les types de données .NET Framework, consultez [SQL Server mappages de types de données](../sql-server-data-type-mappings.md).</span><span class="sxs-lookup"><span data-stu-id="454e3-106">For more information and a table that describes the data type mappings between SQL Server and .NET Framework data types, see [SQL Server Data Type Mappings](../sql-server-data-type-mappings.md).</span></span>  
  
 <span data-ttu-id="454e3-107">SQL Server 2008 introduit de nouveaux types de données conçus pour répondre aux besoins professionnels pour travailler avec des données de date et d’heure, structurées, semi-structurées et non structurées.</span><span class="sxs-lookup"><span data-stu-id="454e3-107">SQL Server 2008 introduces new data types that are designed to meet business needs to work with date and time, structured, semi-structured, and unstructured data.</span></span> <span data-ttu-id="454e3-108">Ceux-ci sont décrits dans la Documentation en ligne de SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="454e3-108">These are documented in SQL Server 2008 Books Online.</span></span>  
  
 <span data-ttu-id="454e3-109">Les types de données SQL Server qui peuvent être utilisés dans votre application dépendent de la version de SQL Server que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="454e3-109">The SQL Server data types that are available for use in your application depends on the version of SQL Server that you are using.</span></span> <span data-ttu-id="454e3-110">Pour plus d'informations, consultez la version appropriée de la documentation en ligne de SQL Server dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="454e3-110">For more information, see the relevant version of SQL Server Books Online in the following table.</span></span>  
  
 <span data-ttu-id="454e3-111">**Documentation SQL Server**</span><span class="sxs-lookup"><span data-stu-id="454e3-111">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="454e3-112">Types de données (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="454e3-112">Data Types (Transact-SQL)</span></span>](/sql/t-sql/data-types/data-types-transact-sql)  
  
## <a name="in-this-section"></a><span data-ttu-id="454e3-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="454e3-113">In This Section</span></span>  

 [<span data-ttu-id="454e3-114">SqlTypes et le DataSet</span><span class="sxs-lookup"><span data-stu-id="454e3-114">SqlTypes and the DataSet</span></span>](sqltypes-and-the-dataset.md)  
 <span data-ttu-id="454e3-115">Décrit la prise en charge de type pour `SqlTypes` dans le `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="454e3-115">Describes type support for `SqlTypes` in the `DataSet`.</span></span>  
  
 [<span data-ttu-id="454e3-116">Gestion des valeurs null</span><span class="sxs-lookup"><span data-stu-id="454e3-116">Handling Null Values</span></span>](handling-null-values.md)  
 <span data-ttu-id="454e3-117">Montre comment utiliser des valeurs null et une logique à trois valeurs.</span><span class="sxs-lookup"><span data-stu-id="454e3-117">Demonstrates how to work with null values and three-valued logic.</span></span>  
  
 [<span data-ttu-id="454e3-118">Comparaison du GUID et des valeurs uniqueidentifier</span><span class="sxs-lookup"><span data-stu-id="454e3-118">Comparing GUID and uniqueidentifier Values</span></span>](comparing-guid-and-uniqueidentifier-values.md)  
 <span data-ttu-id="454e3-119">Montre comment utiliser des valeurs GUID et d'identificateur unique dans SQL Server et le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="454e3-119">Demonstrates how to work with GUID and uniqueidentifier values in SQL Server and the .NET Framework.</span></span>  
  
 [<span data-ttu-id="454e3-120">Données de date et d’heure</span><span class="sxs-lookup"><span data-stu-id="454e3-120">Date and Time Data</span></span>](date-and-time-data.md)  
 <span data-ttu-id="454e3-121">Décrit comment utiliser les nouveaux types de données de date et d’heure introduits dans SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="454e3-121">Describes how to use the new date and time data types introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="454e3-122">UDT volumineux</span><span class="sxs-lookup"><span data-stu-id="454e3-122">Large UDTs</span></span>](large-udts.md)  
 <span data-ttu-id="454e3-123">Montre comment récupérer des données à partir des UDT de valeur élevée introduits dans SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="454e3-123">Demonstrates how to retrieve data from large value UDTs introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="454e3-124">Données XML dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="454e3-124">XML Data in SQL Server</span></span>](xml-data-in-sql-server.md)  
 <span data-ttu-id="454e3-125">Décrit comment utiliser des données XML extraites de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="454e3-125">Describes how to work with XML data retrieved from SQL Server.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="454e3-126">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="454e3-126">Reference</span></span>  

 <xref:System.Data.DataSet>  
 <span data-ttu-id="454e3-127">Décrit la classe `DataSet` et tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="454e3-127">Describes the `DataSet` class and all of its members.</span></span>  
  
 <xref:System.Data.SqlTypes>  
 <span data-ttu-id="454e3-128">Décrit l’espace de noms `SqlTypes` et tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="454e3-128">Describes the `SqlTypes` namespace and all of its members.</span></span>  
  
 <xref:System.Data.SqlDbType>  
 <span data-ttu-id="454e3-129">Décrit l’énumération `SqlDbType` et tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="454e3-129">Describes the `SqlDbType` enumeration and all of its members.</span></span>  
  
 <xref:System.Data.DbType>  
 <span data-ttu-id="454e3-130">Décrit l’énumération `DbType` et tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="454e3-130">Describes the `DbType` enumeration and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="454e3-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="454e3-131">See also</span></span>

- [<span data-ttu-id="454e3-132">Mappages de types de données SQL Server</span><span class="sxs-lookup"><span data-stu-id="454e3-132">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="454e3-133">Configuration des paramètres et des types de données des paramètres</span><span class="sxs-lookup"><span data-stu-id="454e3-133">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="454e3-134">Paramètres table</span><span class="sxs-lookup"><span data-stu-id="454e3-134">Table-Valued Parameters</span></span>](table-valued-parameters.md)
- [<span data-ttu-id="454e3-135">SQL Server des données binaires et de grande valeur</span><span class="sxs-lookup"><span data-stu-id="454e3-135">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="454e3-136">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="454e3-136">ADO.NET Overview</span></span>](../ado-net-overview.md)
