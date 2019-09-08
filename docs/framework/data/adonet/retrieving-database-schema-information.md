---
title: Extraction des informations de schéma de base de données
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: 26b234e35a0d0849914d87b61f4e8c8a87599448
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782738"
---
# <a name="retrieving-database-schema-information"></a><span data-ttu-id="00856-102">Extraction des informations de schéma de base de données</span><span class="sxs-lookup"><span data-stu-id="00856-102">Retrieving Database Schema Information</span></span>
<span data-ttu-id="00856-103">L'obtention des informations de schéma à partir d'une base de données est effectuée avec le processus de découverte de schéma.</span><span class="sxs-lookup"><span data-stu-id="00856-103">Obtaining schema information from a database is accomplished with the process of schema discovery.</span></span> <span data-ttu-id="00856-104">La découverte de schéma permet aux applications de demander que les fournisseurs managés recherchent et retournent des informations sur le schéma de base de données, également appelées *métadonnées*, d’une base de données donnée.</span><span class="sxs-lookup"><span data-stu-id="00856-104">Schema discovery allows applications to request that managed providers find and return information about the database schema, also known as *metadata*, of a given database.</span></span> <span data-ttu-id="00856-105">Différents éléments de schéma de base de données tels que des tables, des colonnes et des procédures stockées, sont exposés à l’aide de collections de schémas.</span><span class="sxs-lookup"><span data-stu-id="00856-105">Different database schema elements such as tables, columns, and stored-procedures are exposed through schema collections.</span></span> <span data-ttu-id="00856-106">Chaque collection de schémas contient une série d'informations de schéma spécifiques au fournisseur utilisé.</span><span class="sxs-lookup"><span data-stu-id="00856-106">Each schema collection contains a variety of schema information specific to the provider being used.</span></span>  
  
 <span data-ttu-id="00856-107">Chacun des .NET Framework fournisseurs managés implémente la méthode **GetSchema** dans la classe **Connection** , et les informations de schéma retournées par la méthode **GetSchema** sont fournies sous la <xref:System.Data.DataTable>forme d’un.</span><span class="sxs-lookup"><span data-stu-id="00856-107">Each of the .NET Framework managed providers implement the **GetSchema** method in the **Connection** class, and the schema information that is returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="00856-108">La méthode **GetSchema** est une méthode surchargée qui fournit des paramètres facultatifs pour spécifier la collection de schémas à retourner et restreindre la quantité d’informations retournées.</span><span class="sxs-lookup"><span data-stu-id="00856-108">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
 <span data-ttu-id="00856-109">Les fournisseurs de données .NET Framework pour OLE DB, ODBC, Oracle et SqlClient fournissent une méthode **GetSchemaTable** qui retourne un DataTable décrivant les métadonnées de colonne du **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="00856-109">The .NET Framework Data Providers for OLE DB, ODBC, Oracle, and SqlClient provide a **GetSchemaTable** method that returns a DataTable describing the column metadata of the **DataReader**.</span></span>  
  
 <span data-ttu-id="00856-110">Le fournisseur de données .NET Framework pour OLE DB expose également des informations de schéma à l'aide de la méthode <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> de l'objet <xref:System.Data.OleDb.OleDbConnection>.</span><span class="sxs-lookup"><span data-stu-id="00856-110">The .NET Framework Data Provider for OLE DB also exposes schema information by using the <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> method of the <xref:System.Data.OleDb.OleDbConnection> object.</span></span> <span data-ttu-id="00856-111">En tant qu' arguments, GetOleDbSchemaTable <xref:System.Data.OleDb.OleDbSchemaGuid> prend un qui identifie les informations de schéma à retourner et un tableau de restrictions sur ces colonnes retournées.</span><span class="sxs-lookup"><span data-stu-id="00856-111">As arguments, **GetOleDbSchemaTable** takes an <xref:System.Data.OleDb.OleDbSchemaGuid> that identifies the schema information to return, and an array of restrictions on those returned columns.</span></span> <span data-ttu-id="00856-112">**GetOleDbSchemaTable** retourne un <xref:System.Data.DataTable> rempli avec les informations de schéma demandées.</span><span class="sxs-lookup"><span data-stu-id="00856-112">**GetOleDbSchemaTable** returns a <xref:System.Data.DataTable> populated with the requested schema information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="00856-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="00856-113">In This Section</span></span>  
 [<span data-ttu-id="00856-114">Collections GetSchema et Schema</span><span class="sxs-lookup"><span data-stu-id="00856-114">GetSchema and Schema Collections</span></span>](getschema-and-schema-collections.md)  
 <span data-ttu-id="00856-115">Décrit la méthode **GetSchema** et la façon dont elle peut être utilisée pour récupérer et restreindre les informations de schéma d’une base de données.</span><span class="sxs-lookup"><span data-stu-id="00856-115">Describes the **GetSchema** method and how it can be used to retrieve and restrict schema information from a database.</span></span>  
  
 <span data-ttu-id="00856-116">Restrictions de schéma</span><span class="sxs-lookup"><span data-stu-id="00856-116">Schema Restrictions</span></span>  
 <span data-ttu-id="00856-117">Décrit les restrictions de schéma qui peuvent être utilisées avec **GetSchema**.</span><span class="sxs-lookup"><span data-stu-id="00856-117">Describes schema restrictions that can be used with **GetSchema**.</span></span>  
  
 [<span data-ttu-id="00856-118">Collections de schémas courantes</span><span class="sxs-lookup"><span data-stu-id="00856-118">Common Schema Collections</span></span>](common-schema-collections.md)  
 <span data-ttu-id="00856-119">Décrit toutes les collections de schémas communes prises en charge par tous les fournisseurs .NET Framework managés.</span><span class="sxs-lookup"><span data-stu-id="00856-119">Describes all of the common schema collections supported by all of the .NET Framework managed providers.</span></span>  
  
 [<span data-ttu-id="00856-120">Collections de schémas SQL Server</span><span class="sxs-lookup"><span data-stu-id="00856-120">SQL Server Schema Collections</span></span>](sql-server-schema-collections.md)  
 <span data-ttu-id="00856-121">Décrit la collection de schémas prise en charge par le fournisseur .NET Framework pour SQL Server.</span><span class="sxs-lookup"><span data-stu-id="00856-121">Describes the schema collection supported by the .NET Framework provider for SQL Server.</span></span>  
  
 [<span data-ttu-id="00856-122">Collections de schémas Oracle</span><span class="sxs-lookup"><span data-stu-id="00856-122">Oracle Schema Collections</span></span>](oracle-schema-collections.md)  
 <span data-ttu-id="00856-123">Décrit la collection de schémas prise en charge par le fournisseur .NET Framework pour Oracle.</span><span class="sxs-lookup"><span data-stu-id="00856-123">Describes the schema collection supported by the .NET Framework provider for Oracle.</span></span>  
  
 [<span data-ttu-id="00856-124">Collections de schémas ODBC</span><span class="sxs-lookup"><span data-stu-id="00856-124">ODBC Schema Collections</span></span>](odbc-schema-collections.md)  
 <span data-ttu-id="00856-125">Décrit les collections de schémas pour les pilotes ODBC.</span><span class="sxs-lookup"><span data-stu-id="00856-125">Describes the schema collections for ODBC drivers.</span></span>  
  
 [<span data-ttu-id="00856-126">Collections de schémas OLE DB</span><span class="sxs-lookup"><span data-stu-id="00856-126">OLE DB Schema Collections</span></span>](ole-db-schema-collections.md)  
 <span data-ttu-id="00856-127">Décrit les collections de schémas pour les fournisseurs OLE DB.</span><span class="sxs-lookup"><span data-stu-id="00856-127">Describes the schema collections for OLE DB providers.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="00856-128">Référence</span><span class="sxs-lookup"><span data-stu-id="00856-128">Reference</span></span>  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 <span data-ttu-id="00856-129">Décrit la méthode **GetSchema** de la <xref:System.Data.Common.DbConnection> classe.</span><span class="sxs-lookup"><span data-stu-id="00856-129">Describes the **GetSchema** method of the <xref:System.Data.Common.DbConnection> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 <span data-ttu-id="00856-130">Décrit la méthode **GetSchema** de la <xref:System.Data.Odbc.OdbcConnection> classe.</span><span class="sxs-lookup"><span data-stu-id="00856-130">Describes the **GetSchema** method of the <xref:System.Data.Odbc.OdbcConnection> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 <span data-ttu-id="00856-131">Décrit la méthode **GetSchema** de la <xref:System.Data.OleDb.OleDbConnection> classe.</span><span class="sxs-lookup"><span data-stu-id="00856-131">Describes the **GetSchema** method of the <xref:System.Data.OleDb.OleDbConnection> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 <span data-ttu-id="00856-132">Décrit la méthode **GetSchema** de la <xref:System.Data.OracleClient.OracleConnection> classe.</span><span class="sxs-lookup"><span data-stu-id="00856-132">Describes the **GetSchema** method of the <xref:System.Data.OracleClient.OracleConnection> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 <span data-ttu-id="00856-133">Décrit la méthode **GetSchema** de la <xref:System.Data.SqlClient.SqlConnection> classe.</span><span class="sxs-lookup"><span data-stu-id="00856-133">Describes the **GetSchema** method of the <xref:System.Data.SqlClient.SqlConnection> class.</span></span>  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="00856-134">Décrit la méthode **GetSchemaTable** de la <xref:System.Data.Common.DbDataReader> classe.</span><span class="sxs-lookup"><span data-stu-id="00856-134">Describes the **GetSchemaTable** method of the <xref:System.Data.Common.DbDataReader> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="00856-135">Décrit la méthode **GetSchemaTable** de la <xref:System.Data.Odbc.OdbcDataReader> classe.</span><span class="sxs-lookup"><span data-stu-id="00856-135">Describes the **GetSchemaTable** method of the <xref:System.Data.Odbc.OdbcDataReader> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="00856-136">Décrit la méthode **GetSchemaTable** de la <xref:System.Data.OleDb.OleDbDataReader> classe.</span><span class="sxs-lookup"><span data-stu-id="00856-136">Describes the **GetSchemaTable** method of the <xref:System.Data.OleDb.OleDbDataReader> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="00856-137">Décrit la méthode **GetSchemaTable** de la <xref:System.Data.OracleClient.OracleDataReader> classe.</span><span class="sxs-lookup"><span data-stu-id="00856-137">Describes the **GetSchemaTable** method of the <xref:System.Data.OracleClient.OracleDataReader> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="00856-138">Décrit la méthode **GetSchemaTable** de la <xref:System.Data.SqlClient.SqlDataReader> classe.</span><span class="sxs-lookup"><span data-stu-id="00856-138">Describes the **GetSchemaTable** method of the <xref:System.Data.SqlClient.SqlDataReader> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00856-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00856-139">See also</span></span>

- [<span data-ttu-id="00856-140">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="00856-140">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="00856-141">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="00856-141">ADO.NET Overview</span></span>](ado-net-overview.md)
