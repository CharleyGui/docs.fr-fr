---
title: SQL Server et ADO.NET
description: En savoir plus sur les fonctionnalités et les comportements du Fournisseur de données .NET Framework pour SQL Server, qui encapsule des protocoles spécifiques à la base de données.
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.openlocfilehash: eeb0ab69a68dfc2fc0faa1b4e833f80b307fffe5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286441"
---
# <a name="sql-server-and-adonet"></a><span data-ttu-id="cce21-103">SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cce21-103">SQL Server and ADO.NET</span></span>
<span data-ttu-id="cce21-104">Cette section décrit des fonctions et des comportements spécifiques au fournisseur de données .NET Framework pour SQL Server (<xref:System.Data.SqlClient>).</span><span class="sxs-lookup"><span data-stu-id="cce21-104">This section describes features and behaviors that are specific to the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>).</span></span>  
  
 <span data-ttu-id="cce21-105"><xref:System.Data.SqlClient> permet d’accéder à différentes versions de SQL Server, qui encapsule des protocoles spécifiques à la base de données.</span><span class="sxs-lookup"><span data-stu-id="cce21-105"><xref:System.Data.SqlClient> provides access to versions of SQL Server, which encapsulates database-specific protocols.</span></span> <span data-ttu-id="cce21-106">La fonctionnalité du fournisseur de données est conçue pour être similaire à celle des fournisseurs de données .NET Framework pour OLE DB, ODBC et Oracle.</span><span class="sxs-lookup"><span data-stu-id="cce21-106">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for OLE DB, ODBC, and Oracle.</span></span> <span data-ttu-id="cce21-107"><xref:System.Data.SqlClient> comprend un analyseur TDS (Tabular Data Stream) pour communiquer directement avec SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cce21-107"><xref:System.Data.SqlClient> includes a tabular data stream (TDS) parser to communicate directly with SQL Server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cce21-108">Pour utiliser le fournisseur de données .NET Framework pour SQL Server, une application doit faire référence à l'espace de noms <xref:System.Data.SqlClient>.</span><span class="sxs-lookup"><span data-stu-id="cce21-108">To use the .NET Framework Data Provider for SQL Server, an application must reference the <xref:System.Data.SqlClient> namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cce21-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="cce21-109">In This Section</span></span>  
 [<span data-ttu-id="cce21-110">Sécurité SQL Server</span><span class="sxs-lookup"><span data-stu-id="cce21-110">SQL Server Security</span></span>](sql-server-security.md)  
 <span data-ttu-id="cce21-111">Fournit une vue d’ensemble de la sécurité de SQL Server et des scénarios d’application pour créer des applications ADO.NET sécurisées qui ciblent SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cce21-111">Provides an overview of SQL Server security features, and application scenarios for creating secure ADO.NET applications that target SQL Server.</span></span>  
  
 [<span data-ttu-id="cce21-112">Types de données SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cce21-112">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)  
 <span data-ttu-id="cce21-113">Décrit comment utiliser les types de données SQL Server et comment ces derniers interagissent avec les types de données .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cce21-113">Describes how to work with SQL Server data types and how they interact with .NET Framework data types.</span></span>  
  
 [<span data-ttu-id="cce21-114">SQL Server des données binaires et de grande valeur</span><span class="sxs-lookup"><span data-stu-id="cce21-114">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)  
 <span data-ttu-id="cce21-115">Décrit comment utiliser les données à valeurs élevées dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cce21-115">Describes how to work with large value data in SQL Server.</span></span>  
  
 [<span data-ttu-id="cce21-116">SQL Server des opérations de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cce21-116">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)  
 <span data-ttu-id="cce21-117">Décrit comment utiliser des données dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cce21-117">Describes how to work with data in SQL Server.</span></span> <span data-ttu-id="cce21-118">Contient des sections sur les opérations de copie en bloc, MARS, les opérations asynchrones et les paramètres table.</span><span class="sxs-lookup"><span data-stu-id="cce21-118">Contains sections about bulk copy operations, MARS, asynchronous operations, and table-valued parameters.</span></span>  
  
 [<span data-ttu-id="cce21-119">Fonctionnalités de SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cce21-119">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)  
 <span data-ttu-id="cce21-120">Décrit les fonctionnalités de SQL Server utiles pour les développeurs d’applications ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="cce21-120">Describes SQL Server features that are useful for ADO.NET application developers.</span></span>  
  
 [<span data-ttu-id="cce21-121">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="cce21-121">LINQ to SQL</span></span>](./linq/index.md)  
 <span data-ttu-id="cce21-122">Décrit les blocs de construction, les processus et les techniques de base requis pour la création d'applications LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="cce21-122">Describes the basic building blocks, processes, and techniques required for creating LINQ to SQL applications.</span></span>  
  
 <span data-ttu-id="cce21-123">Pour obtenir une documentation complète sur le moteur de base de données SQL Server, consultez la documentation en ligne de SQL Server correspondant à la version que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="cce21-123">For complete documentation of the SQL Server Database Engine, see SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 [<span data-ttu-id="cce21-124">Documentation en ligne de SQL Server</span><span class="sxs-lookup"><span data-stu-id="cce21-124">SQL Server Books Online</span></span>](/sql/sql-server/sql-server-technical-documentation)  
  
## <a name="see-also"></a><span data-ttu-id="cce21-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cce21-125">See also</span></span>

- [<span data-ttu-id="cce21-126">Sécurisation des applications ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cce21-126">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="cce21-127">Mappages de types de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cce21-127">Data Type Mappings in ADO.NET</span></span>](../data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="cce21-128">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="cce21-128">DataSets, DataTables, and DataViews</span></span>](../dataset-datatable-dataview/index.md)
- [<span data-ttu-id="cce21-129">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cce21-129">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="cce21-130">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cce21-130">ADO.NET Overview</span></span>](../ado-net-overview.md)
