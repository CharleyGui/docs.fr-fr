---
title: Oracle et ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: ccfe40f218e3f09de53d6cb596a31b2520d9ff9b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783475"
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="877f6-102">Oracle et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="877f6-102">Oracle and ADO.NET</span></span>
> [!NOTE]
> <span data-ttu-id="877f6-103">Les types dans <xref:System.Data.OracleClient> sont déconseillés.</span><span class="sxs-lookup"><span data-stu-id="877f6-103">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="877f6-104">Les types restent pris en charge dans la version actuelle du .NET Framework, mais seront supprimés dans une mise en production ultérieure.</span><span class="sxs-lookup"><span data-stu-id="877f6-104">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="877f6-105">Microsoft recommande l'utilisation d'un fournisseur Oracle tiers.</span><span class="sxs-lookup"><span data-stu-id="877f6-105">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="877f6-106">Cette section décrit les fonctionnalités et les comportements spécifiques aux Fournisseur de données .NET Framework pour Oracle.</span><span class="sxs-lookup"><span data-stu-id="877f6-106">This section describes features and behaviors that are specific to the .NET Framework Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="877f6-107">La .NET Framework Fournisseur de données pour Oracle permet d’accéder à une base de données Oracle à l’aide de l’interface OCI (Oracle Call Interface) fournie par le logiciel client Oracle.</span><span class="sxs-lookup"><span data-stu-id="877f6-107">The .NET Framework Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="877f6-108">La fonctionnalité du fournisseur de données est conçue pour être similaire à celle des fournisseurs de données .NET Framework pour SQL Server, OLE DB et ODBC.</span><span class="sxs-lookup"><span data-stu-id="877f6-108">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for SQL Server, OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="877f6-109">Pour utiliser le fournisseur de données .NET Framework pour Oracle, une application doit faire référence <xref:System.Data.OracleClient> à l’espace de noms comme suit :</span><span class="sxs-lookup"><span data-stu-id="877f6-109">To use the .NET Framework Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="877f6-110">Vous devez également inclure une référence à la DLL lorsque vous compilez votre code.</span><span class="sxs-lookup"><span data-stu-id="877f6-110">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="877f6-111">Par exemple, si vous compilez un programme C#, votre ligne de commande doit inclure :</span><span class="sxs-lookup"><span data-stu-id="877f6-111">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="877f6-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="877f6-112">In This Section</span></span>  
 [<span data-ttu-id="877f6-113">Configuration système requise</span><span class="sxs-lookup"><span data-stu-id="877f6-113">System Requirements</span></span>](system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="877f6-114">Décrit la configuration requise pour l’utilisation du Fournisseur de données .NET Framework pour Oracle et décrit un certain nombre de problèmes à prendre en compte lors de son utilisation.</span><span class="sxs-lookup"><span data-stu-id="877f6-114">Describes requirements for using the .NET Framework Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="877f6-115">BFILE Oracle</span><span class="sxs-lookup"><span data-stu-id="877f6-115">Oracle BFILEs</span></span>](oracle-bfiles.md)  
 <span data-ttu-id="877f6-116">Décrit la classe <xref:System.Data.OracleClient.OracleBFile> qui est utilisée pour travailler avec le type de données Oracle BFILE.</span><span class="sxs-lookup"><span data-stu-id="877f6-116">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="877f6-117">LOB Oracle</span><span class="sxs-lookup"><span data-stu-id="877f6-117">Oracle LOBs</span></span>](oracle-lobs.md)  
 <span data-ttu-id="877f6-118">Décrit la classe <xref:System.Data.OracleClient.OracleLob> qui est utilisée pour travailler avec les types de données Oracle LOB.</span><span class="sxs-lookup"><span data-stu-id="877f6-118">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="877f6-119">REF CURSOR Oracle</span><span class="sxs-lookup"><span data-stu-id="877f6-119">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)  
 <span data-ttu-id="877f6-120">Décrit la prise en charge pour le type de données Oracle REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="877f6-120">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="877f6-121">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="877f6-121">OracleTypes</span></span>](oracletypes.md)  
 <span data-ttu-id="877f6-122">Décrit les structures que vous pouvez utiliser pour travailler avec des types de données Oracle, notamment <xref:System.Data.OracleClient.OracleNumber> et <xref:System.Data.OracleClient.OracleString>.</span><span class="sxs-lookup"><span data-stu-id="877f6-122">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="877f6-123">Séquences Oracle</span><span class="sxs-lookup"><span data-stu-id="877f6-123">Oracle Sequences</span></span>](oracle-sequences.md)  
 <span data-ttu-id="877f6-124">Décrit la prise en charge de l'extraction des valeurs de séquence Oracle générées par le serveur.</span><span class="sxs-lookup"><span data-stu-id="877f6-124">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="877f6-125">Mappages de types de données Oracle</span><span class="sxs-lookup"><span data-stu-id="877f6-125">Oracle Data Type Mappings</span></span>](oracle-data-type-mappings.md)  
 <span data-ttu-id="877f6-126">Répertorie les types de données Oracle et leurs mappages sur le <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="877f6-126">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="877f6-127">Transactions distribuées Oracle</span><span class="sxs-lookup"><span data-stu-id="877f6-127">Oracle Distributed Transactions</span></span>](oracle-distributed-transactions.md)  
 <span data-ttu-id="877f6-128">Décrit la manière dont l’objet <xref:System.Data.OracleClient.OracleConnection> s’inscrit automatiquement dans une transaction distribuée existante s’il détermine qu’une transaction est active.</span><span class="sxs-lookup"><span data-stu-id="877f6-128">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="877f6-129">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="877f6-129">Related Sections</span></span>  
 [<span data-ttu-id="877f6-130">Sécurisation des applications ADO.NET</span><span class="sxs-lookup"><span data-stu-id="877f6-130">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)  
 <span data-ttu-id="877f6-131">Décrit des pratiques de codage sécurisées dans ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="877f6-131">Describes secure coding practices when using ADO.NET.</span></span>  
  
 [<span data-ttu-id="877f6-132">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="877f6-132">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)  
 <span data-ttu-id="877f6-133">Explique comment créer et utiliser des `DataSets`, des `DataSets` typés, des `DataTables` et des `DataViews`.</span><span class="sxs-lookup"><span data-stu-id="877f6-133">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 [<span data-ttu-id="877f6-134">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="877f6-134">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)  
 <span data-ttu-id="877f6-135">Décrit comment utiliser des données dans ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="877f6-135">Describes how to work with data in ADO.NET.</span></span>  
  
 [<span data-ttu-id="877f6-136">SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="877f6-136">SQL Server and ADO.NET</span></span>](./sql/index.md)  
 <span data-ttu-id="877f6-137">Décrit comment utiliser des fonctions et fonctionnalités spécifiques à SQL Server.</span><span class="sxs-lookup"><span data-stu-id="877f6-137">Describes how to work with features and functionality that are specific to SQL Server.</span></span>  
  
 [<span data-ttu-id="877f6-138">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="877f6-138">DbProviderFactories</span></span>](dbproviderfactories.md)  
 <span data-ttu-id="877f6-139">Décrit des classes génériques qui vous permettent d'écrire du code indépendant du fournisseur dans ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="877f6-139">Describes generic classes that allow you to write provider-independent code in ADO.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="877f6-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="877f6-140">See also</span></span>

- [<span data-ttu-id="877f6-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="877f6-141">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="877f6-142">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="877f6-142">ADO.NET Overview</span></span>](ado-net-overview.md)
