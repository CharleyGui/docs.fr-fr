---
title: Oracle et ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: 381f796bec31bece354001ad46bf5079381d1b3d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914558"
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="76e54-102">Oracle et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="76e54-102">Oracle and ADO.NET</span></span>
> [!NOTE]
> <span data-ttu-id="76e54-103">Les types dans <xref:System.Data.OracleClient> sont déconseillés.</span><span class="sxs-lookup"><span data-stu-id="76e54-103">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="76e54-104">Les types restent pris en charge dans la version actuelle du .NET Framework, mais seront supprimés dans une mise en production ultérieure.</span><span class="sxs-lookup"><span data-stu-id="76e54-104">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="76e54-105">Microsoft recommande l'utilisation d'un fournisseur Oracle tiers.</span><span class="sxs-lookup"><span data-stu-id="76e54-105">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="76e54-106">Cette section décrit les fonctionnalités et les comportements spécifiques aux Fournisseur de données .NET Framework pour Oracle.</span><span class="sxs-lookup"><span data-stu-id="76e54-106">This section describes features and behaviors that are specific to the .NET Framework Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="76e54-107">La .NET Framework Fournisseur de données pour Oracle permet d’accéder à une base de données Oracle à l’aide de l’interface OCI (Oracle Call Interface) fournie par le logiciel client Oracle.</span><span class="sxs-lookup"><span data-stu-id="76e54-107">The .NET Framework Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="76e54-108">La fonctionnalité du fournisseur de données est conçue pour être similaire à celle des fournisseurs de données .NET Framework pour SQL Server, OLE DB et ODBC.</span><span class="sxs-lookup"><span data-stu-id="76e54-108">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for SQL Server, OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="76e54-109">Pour utiliser le fournisseur de données .NET Framework pour Oracle, une application doit faire référence <xref:System.Data.OracleClient> à l’espace de noms comme suit:</span><span class="sxs-lookup"><span data-stu-id="76e54-109">To use the .NET Framework Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="76e54-110">Vous devez également inclure une référence à la DLL lorsque vous compilez votre code.</span><span class="sxs-lookup"><span data-stu-id="76e54-110">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="76e54-111">Par exemple, si vous compilez un programme C#, votre ligne de commande doit inclure :</span><span class="sxs-lookup"><span data-stu-id="76e54-111">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="76e54-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="76e54-112">In This Section</span></span>  
 [<span data-ttu-id="76e54-113">Configuration système requise</span><span class="sxs-lookup"><span data-stu-id="76e54-113">System Requirements</span></span>](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="76e54-114">Décrit la configuration requise pour l’utilisation du Fournisseur de données .NET Framework pour Oracle et décrit un certain nombre de problèmes à prendre en compte lors de son utilisation.</span><span class="sxs-lookup"><span data-stu-id="76e54-114">Describes requirements for using the .NET Framework Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="76e54-115">BFILE Oracle</span><span class="sxs-lookup"><span data-stu-id="76e54-115">Oracle BFILEs</span></span>](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 <span data-ttu-id="76e54-116">Décrit la classe <xref:System.Data.OracleClient.OracleBFile> qui est utilisée pour travailler avec le type de données Oracle BFILE.</span><span class="sxs-lookup"><span data-stu-id="76e54-116">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="76e54-117">LOB Oracle</span><span class="sxs-lookup"><span data-stu-id="76e54-117">Oracle LOBs</span></span>](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 <span data-ttu-id="76e54-118">Décrit la classe <xref:System.Data.OracleClient.OracleLob> qui est utilisée pour travailler avec les types de données Oracle LOB.</span><span class="sxs-lookup"><span data-stu-id="76e54-118">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="76e54-119">REF CURSOR Oracle</span><span class="sxs-lookup"><span data-stu-id="76e54-119">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 <span data-ttu-id="76e54-120">Décrit la prise en charge pour le type de données Oracle REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="76e54-120">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="76e54-121">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="76e54-121">OracleTypes</span></span>](../../../../docs/framework/data/adonet/oracletypes.md)  
 <span data-ttu-id="76e54-122">Décrit les structures que vous pouvez utiliser pour travailler avec des types de données Oracle, notamment <xref:System.Data.OracleClient.OracleNumber> et <xref:System.Data.OracleClient.OracleString>.</span><span class="sxs-lookup"><span data-stu-id="76e54-122">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="76e54-123">Séquences Oracle</span><span class="sxs-lookup"><span data-stu-id="76e54-123">Oracle Sequences</span></span>](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 <span data-ttu-id="76e54-124">Décrit la prise en charge de l'extraction des valeurs de séquence Oracle générées par le serveur.</span><span class="sxs-lookup"><span data-stu-id="76e54-124">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="76e54-125">Mappages de types de données Oracle</span><span class="sxs-lookup"><span data-stu-id="76e54-125">Oracle Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 <span data-ttu-id="76e54-126">Répertorie les types de données Oracle et leurs mappages sur le <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="76e54-126">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="76e54-127">Transactions distribuées Oracle</span><span class="sxs-lookup"><span data-stu-id="76e54-127">Oracle Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 <span data-ttu-id="76e54-128">Décrit la manière dont l’objet <xref:System.Data.OracleClient.OracleConnection> s’inscrit automatiquement dans une transaction distribuée existante s’il détermine qu’une transaction est active.</span><span class="sxs-lookup"><span data-stu-id="76e54-128">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="76e54-129">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="76e54-129">Related Sections</span></span>  
 [<span data-ttu-id="76e54-130">Sécurisation des applications ADO.NET</span><span class="sxs-lookup"><span data-stu-id="76e54-130">Securing ADO.NET Applications</span></span>](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 <span data-ttu-id="76e54-131">Décrit des pratiques de codage sécurisées dans ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="76e54-131">Describes secure coding practices when using ADO.NET.</span></span>  
  
 [<span data-ttu-id="76e54-132">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="76e54-132">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="76e54-133">Explique comment créer et utiliser des `DataSets`, des `DataSets` typés, des `DataTables` et des `DataViews`.</span><span class="sxs-lookup"><span data-stu-id="76e54-133">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 [<span data-ttu-id="76e54-134">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="76e54-134">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 <span data-ttu-id="76e54-135">Décrit comment utiliser des données dans ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="76e54-135">Describes how to work with data in ADO.NET.</span></span>  
  
 [<span data-ttu-id="76e54-136">SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="76e54-136">SQL Server and ADO.NET</span></span>](../../../../docs/framework/data/adonet/sql/index.md)  
 <span data-ttu-id="76e54-137">Décrit comment utiliser des fonctions et fonctionnalités spécifiques à SQL Server.</span><span class="sxs-lookup"><span data-stu-id="76e54-137">Describes how to work with features and functionality that are specific to SQL Server.</span></span>  
  
 [<span data-ttu-id="76e54-138">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="76e54-138">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 <span data-ttu-id="76e54-139">Décrit des classes génériques qui vous permettent d'écrire du code indépendant du fournisseur dans ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="76e54-139">Describes generic classes that allow you to write provider-independent code in ADO.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76e54-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76e54-140">See also</span></span>

- [<span data-ttu-id="76e54-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="76e54-141">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
- [<span data-ttu-id="76e54-142">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="76e54-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
