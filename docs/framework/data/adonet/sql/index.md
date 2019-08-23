---
title: SQL Server et ADO.NET
ms.date: 03/30/2017
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.openlocfilehash: c58c6da7a6028c9167c73af820e922f59b528f15
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938093"
---
# <a name="sql-server-and-adonet"></a><span data-ttu-id="a23fe-102">SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a23fe-102">SQL Server and ADO.NET</span></span>
<span data-ttu-id="a23fe-103">Cette section décrit des fonctions et des comportements spécifiques au fournisseur de données .NET Framework pour SQL Server (<xref:System.Data.SqlClient>).</span><span class="sxs-lookup"><span data-stu-id="a23fe-103">This section describes features and behaviors that are specific to the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>).</span></span>  
  
 <span data-ttu-id="a23fe-104"><xref:System.Data.SqlClient> permet d'accéder à différentes versions de SQL Server, qui encapsule des protocoles spécifiques à la base de données.</span><span class="sxs-lookup"><span data-stu-id="a23fe-104"><xref:System.Data.SqlClient> provides access to versions of SQL Server, which encapsulates database-specific protocols.</span></span> <span data-ttu-id="a23fe-105">La fonctionnalité du fournisseur de données est conçue pour être similaire à celle des fournisseurs de données .NET Framework pour OLE DB, ODBC et Oracle.</span><span class="sxs-lookup"><span data-stu-id="a23fe-105">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for OLE DB, ODBC, and Oracle.</span></span> <span data-ttu-id="a23fe-106"><xref:System.Data.SqlClient> inclut un analyseur TDS (Tabular Data Stream) qui permet de communiquer directement avec SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a23fe-106"><xref:System.Data.SqlClient> includes a tabular data stream (TDS) parser to communicate directly with SQL Server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a23fe-107">Pour utiliser le fournisseur de données .NET Framework pour SQL Server, une application doit faire référence à l'espace de noms <xref:System.Data.SqlClient>.</span><span class="sxs-lookup"><span data-stu-id="a23fe-107">To use the .NET Framework Data Provider for SQL Server, an application must reference the <xref:System.Data.SqlClient> namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a23fe-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a23fe-108">In This Section</span></span>  
 [<span data-ttu-id="a23fe-109">Sécurité SQL Server</span><span class="sxs-lookup"><span data-stu-id="a23fe-109">SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 <span data-ttu-id="a23fe-110">Fournit une vue d’ensemble des fonctionnalités de sécurité de SQL Server et des scénarios d’application consacrés à la création d’applications ADO.NET sécurisées ciblant SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a23fe-110">Provides an overview of SQL Server security features, and application scenarios for creating secure ADO.NET applications that target SQL Server.</span></span>  
  
 [<span data-ttu-id="a23fe-111">Types de données SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a23fe-111">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 <span data-ttu-id="a23fe-112">Décrit comment utiliser les types de données SQL Server et comment ces derniers interagissent avec les types de données .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a23fe-112">Describes how to work with SQL Server data types and how they interact with .NET Framework data types.</span></span>  
  
 [<span data-ttu-id="a23fe-113">Données binaires et de valeur élevée SQL Server</span><span class="sxs-lookup"><span data-stu-id="a23fe-113">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 <span data-ttu-id="a23fe-114">Décrit comment utiliser des données de valeur élevée dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a23fe-114">Describes how to work with large value data in SQL Server.</span></span>  
  
 [<span data-ttu-id="a23fe-115">Opérations sur les données SQL Server dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a23fe-115">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 <span data-ttu-id="a23fe-116">Décrit comment utiliser des données dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a23fe-116">Describes how to work with data in SQL Server.</span></span> <span data-ttu-id="a23fe-117">Contient des sections consacrées aux opérations de copie en bloc, à MARS, aux opérations asynchrones et aux paramètres table.</span><span class="sxs-lookup"><span data-stu-id="a23fe-117">Contains sections about bulk copy operations, MARS, asynchronous operations, and table-valued parameters.</span></span>  
  
 [<span data-ttu-id="a23fe-118">Fonctionnalités SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a23fe-118">SQL Server Features and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 <span data-ttu-id="a23fe-119">Décrit les fonctionnalités de SQL Server utiles aux développeurs d’applications ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="a23fe-119">Describes SQL Server features that are useful for ADO.NET application developers.</span></span>  
  
 [<span data-ttu-id="a23fe-120">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a23fe-120">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="a23fe-121">Décrit les blocs de construction, les processus et les techniques de base requis pour la création d'applications LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="a23fe-121">Describes the basic building blocks, processes, and techniques required for creating LINQ to SQL applications.</span></span>  
  
 <span data-ttu-id="a23fe-122">Pour la documentation complète du moteur de base de données SQL Server, consultez la documentation en ligne de SQL Server correspondant à la version de SQL Server que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="a23fe-122">For complete documentation of the SQL Server Database Engine, see SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 [<span data-ttu-id="a23fe-123">Documentation en ligne de SQL Server</span><span class="sxs-lookup"><span data-stu-id="a23fe-123">SQL Server Books Online</span></span>](/sql/sql-server/sql-server-technical-documentation)  
  
## <a name="see-also"></a><span data-ttu-id="a23fe-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a23fe-124">See also</span></span>

- [<span data-ttu-id="a23fe-125">Sécurisation des applications ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a23fe-125">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [<span data-ttu-id="a23fe-126">Mappages de types de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a23fe-126">Data Type Mappings in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="a23fe-127">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="a23fe-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="a23fe-128">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a23fe-128">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="a23fe-129">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="a23fe-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
