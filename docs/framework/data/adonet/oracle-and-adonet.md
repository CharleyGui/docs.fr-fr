---
title: Oracle et ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: a49634f712e32f873df8e47fbcb0c91dbe33fa94
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039825"
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="b964c-102">Oracle et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b964c-102">Oracle and ADO.NET</span></span>
> [!NOTE]
> <span data-ttu-id="b964c-103">Les types dans <xref:System.Data.OracleClient> sont déconseillés.</span><span class="sxs-lookup"><span data-stu-id="b964c-103">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="b964c-104">Les types restent pris en charge dans la version actuelle du .NET Framework, mais seront supprimés dans une mise en production ultérieure.</span><span class="sxs-lookup"><span data-stu-id="b964c-104">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="b964c-105">Microsoft recommande l'utilisation d'un fournisseur Oracle tiers.</span><span class="sxs-lookup"><span data-stu-id="b964c-105">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="b964c-106">Cette section décrit les fonctionnalités et les comportements spécifiques aux Fournisseur de données .NET Framework pour Oracle.</span><span class="sxs-lookup"><span data-stu-id="b964c-106">This section describes features and behaviors that are specific to the .NET Framework Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="b964c-107">La .NET Framework Fournisseur de données pour Oracle permet d’accéder à une base de données Oracle à l’aide de l’interface OCI (Oracle Call Interface) fournie par le logiciel client Oracle.</span><span class="sxs-lookup"><span data-stu-id="b964c-107">The .NET Framework Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="b964c-108">La fonctionnalité du fournisseur de données est conçue pour être similaire à celle des fournisseurs de données .NET Framework pour SQL Server, OLE DB et ODBC.</span><span class="sxs-lookup"><span data-stu-id="b964c-108">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for SQL Server, OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="b964c-109">Pour utiliser le Fournisseur de données .NET Framework pour Oracle, une application doit référencer l’espace de noms <xref:System.Data.OracleClient> comme suit :</span><span class="sxs-lookup"><span data-stu-id="b964c-109">To use the .NET Framework Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="b964c-110">Vous devez également inclure une référence à la DLL lorsque vous compilez votre code.</span><span class="sxs-lookup"><span data-stu-id="b964c-110">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="b964c-111">Par exemple, si vous compilez un programme C#, votre ligne de commande doit inclure :</span><span class="sxs-lookup"><span data-stu-id="b964c-111">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```console
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="b964c-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b964c-112">In This Section</span></span>  
 [<span data-ttu-id="b964c-113">Configuration système requise</span><span class="sxs-lookup"><span data-stu-id="b964c-113">System Requirements</span></span>](system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="b964c-114">Décrit la configuration requise pour l’utilisation du Fournisseur de données .NET Framework pour Oracle et décrit un certain nombre de problèmes à prendre en compte lors de son utilisation.</span><span class="sxs-lookup"><span data-stu-id="b964c-114">Describes requirements for using the .NET Framework Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="b964c-115">BFILE Oracle</span><span class="sxs-lookup"><span data-stu-id="b964c-115">Oracle BFILEs</span></span>](oracle-bfiles.md)  
 <span data-ttu-id="b964c-116">Décrit la classe <xref:System.Data.OracleClient.OracleBFile> qui est utilisée pour travailler avec le type de données Oracle BFILE.</span><span class="sxs-lookup"><span data-stu-id="b964c-116">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="b964c-117">LOB Oracle</span><span class="sxs-lookup"><span data-stu-id="b964c-117">Oracle LOBs</span></span>](oracle-lobs.md)  
 <span data-ttu-id="b964c-118">Décrit la classe <xref:System.Data.OracleClient.OracleLob> qui est utilisée pour travailler avec les types de données Oracle LOB.</span><span class="sxs-lookup"><span data-stu-id="b964c-118">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="b964c-119">REF CURSOR Oracle</span><span class="sxs-lookup"><span data-stu-id="b964c-119">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)  
 <span data-ttu-id="b964c-120">Décrit la prise en charge pour le type de données Oracle REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="b964c-120">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="b964c-121">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="b964c-121">OracleTypes</span></span>](oracletypes.md)  
 <span data-ttu-id="b964c-122">Décrit les structures que vous pouvez utiliser pour travailler avec des types de données Oracle, notamment <xref:System.Data.OracleClient.OracleNumber> et <xref:System.Data.OracleClient.OracleString>.</span><span class="sxs-lookup"><span data-stu-id="b964c-122">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="b964c-123">Séquences Oracle</span><span class="sxs-lookup"><span data-stu-id="b964c-123">Oracle Sequences</span></span>](oracle-sequences.md)  
 <span data-ttu-id="b964c-124">Décrit la prise en charge de l'extraction des valeurs de séquence Oracle générées par le serveur.</span><span class="sxs-lookup"><span data-stu-id="b964c-124">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="b964c-125">Mappages de types de données Oracle</span><span class="sxs-lookup"><span data-stu-id="b964c-125">Oracle Data Type Mappings</span></span>](oracle-data-type-mappings.md)  
 <span data-ttu-id="b964c-126">Répertorie les types de données Oracle et leurs mappages sur le <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="b964c-126">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="b964c-127">Transactions distribuées Oracle</span><span class="sxs-lookup"><span data-stu-id="b964c-127">Oracle Distributed Transactions</span></span>](oracle-distributed-transactions.md)  
 <span data-ttu-id="b964c-128">Décrit la manière dont l’objet <xref:System.Data.OracleClient.OracleConnection> s’inscrit automatiquement dans une transaction distribuée existante s’il détermine qu’une transaction est active.</span><span class="sxs-lookup"><span data-stu-id="b964c-128">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b964c-129">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="b964c-129">Related Sections</span></span>  
 [<span data-ttu-id="b964c-130">Sécurisation des applications ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b964c-130">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)  
 <span data-ttu-id="b964c-131">Décrit des pratiques de codage sécurisées dans ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="b964c-131">Describes secure coding practices when using ADO.NET.</span></span>  
  
 [<span data-ttu-id="b964c-132">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="b964c-132">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)  
 <span data-ttu-id="b964c-133">Explique comment créer et utiliser des `DataSets`, des `DataSets` typés, des `DataTables` et des `DataViews`.</span><span class="sxs-lookup"><span data-stu-id="b964c-133">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 [<span data-ttu-id="b964c-134">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b964c-134">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)  
 <span data-ttu-id="b964c-135">Décrit comment utiliser des données dans ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="b964c-135">Describes how to work with data in ADO.NET.</span></span>  
  
 [<span data-ttu-id="b964c-136">SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b964c-136">SQL Server and ADO.NET</span></span>](./sql/index.md)  
 <span data-ttu-id="b964c-137">Décrit comment utiliser des fonctions et fonctionnalités spécifiques à SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b964c-137">Describes how to work with features and functionality that are specific to SQL Server.</span></span>  
  
 [<span data-ttu-id="b964c-138">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="b964c-138">DbProviderFactories</span></span>](dbproviderfactories.md)  
 <span data-ttu-id="b964c-139">Décrit des classes génériques qui vous permettent d'écrire du code indépendant du fournisseur dans ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="b964c-139">Describes generic classes that allow you to write provider-independent code in ADO.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b964c-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b964c-140">See also</span></span>

- [<span data-ttu-id="b964c-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b964c-141">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="b964c-142">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b964c-142">ADO.NET Overview</span></span>](ado-net-overview.md)
