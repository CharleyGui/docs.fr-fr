---
title: Exemples de code
description: Ces exemples montrent .NET Framework aux programmeurs comment récupérer des données d’une base de données à l’aide des fournisseurs de données ADO.NET et des Entity Framework ADO.NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c119657a-9ce6-4940-91e4-ac1d5f0d9584
ms.openlocfilehash: 54df0e253716c970cf23446434d96b104b8e9b03
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287166"
---
# <a name="adonet-code-examples"></a><span data-ttu-id="7b2dd-103">Exemples de code ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7b2dd-103">ADO.NET code examples</span></span>

<span data-ttu-id="7b2dd-104">Les listes de code sur cette page montrent comment récupérer des données à partir d’une base de données à l’aide des technologies ADO.NET suivantes :</span><span class="sxs-lookup"><span data-stu-id="7b2dd-104">The code listings on this page demonstrate how to retrieve data from a database by using the following ADO.NET technologies:</span></span>

- <span data-ttu-id="7b2dd-105">Fournisseurs de données ADO.NET :</span><span class="sxs-lookup"><span data-stu-id="7b2dd-105">ADO.NET data providers:</span></span>

  - <span data-ttu-id="7b2dd-106">[SqlClient](#sqlclient) ( `System.Data.SqlClient` )</span><span class="sxs-lookup"><span data-stu-id="7b2dd-106">[SqlClient](#sqlclient) (`System.Data.SqlClient`)</span></span>

  - <span data-ttu-id="7b2dd-107">[OLEDB](#oledb) ( `System.Data.OleDb` )</span><span class="sxs-lookup"><span data-stu-id="7b2dd-107">[OleDb](#oledb) (`System.Data.OleDb`)</span></span>

  - <span data-ttu-id="7b2dd-108">[ODBC](#odbc) ( `System.Data.Odbc` )</span><span class="sxs-lookup"><span data-stu-id="7b2dd-108">[Odbc](#odbc) (`System.Data.Odbc`)</span></span>

  - <span data-ttu-id="7b2dd-109">[OracleClient](#oracleclient) ( `System.Data.OracleClient` )</span><span class="sxs-lookup"><span data-stu-id="7b2dd-109">[OracleClient](#oracleclient) (`System.Data.OracleClient`)</span></span>

- <span data-ttu-id="7b2dd-110">ADO.NET Entity Framework :</span><span class="sxs-lookup"><span data-stu-id="7b2dd-110">ADO.NET Entity Framework:</span></span>

  - [<span data-ttu-id="7b2dd-111">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="7b2dd-111">LINQ to Entities</span></span>](#linq-to-entities)

  - [<span data-ttu-id="7b2dd-112">ObjectQuery typé</span><span class="sxs-lookup"><span data-stu-id="7b2dd-112">Typed ObjectQuery</span></span>](#typed-objectquery)

  - <span data-ttu-id="7b2dd-113">[EntityClient](#entityclient) ( `System.Data.EntityClient` )</span><span class="sxs-lookup"><span data-stu-id="7b2dd-113">[EntityClient](#entityclient) (`System.Data.EntityClient`)</span></span>

- [<span data-ttu-id="7b2dd-114">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7b2dd-114">LINQ to SQL</span></span>](#linq-to-sql)

## <a name="adonet-data-provider-examples"></a><span data-ttu-id="7b2dd-115">Exemples de fournisseurs de données ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7b2dd-115">ADO.NET data provider examples</span></span>
<span data-ttu-id="7b2dd-116">Les listings de code suivants montrent comment récupérer des données d'une base de données à l'aide des fournisseurs de données ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="7b2dd-116">The following code listings demonstrate how to retrieve data from a database using ADO.NET data providers.</span></span> <span data-ttu-id="7b2dd-117">Les données sont retournées dans un `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="7b2dd-117">The data is returned in a `DataReader`.</span></span> <span data-ttu-id="7b2dd-118">Pour plus d’informations, consultez [récupération de données à l’aide d’un DataReader](retrieving-data-using-a-datareader.md).</span><span class="sxs-lookup"><span data-stu-id="7b2dd-118">For more information, see [Retrieving Data Using a DataReader](retrieving-data-using-a-datareader.md).</span></span>

### <a name="sqlclient"></a><span data-ttu-id="7b2dd-119">SqlClient</span><span class="sxs-lookup"><span data-stu-id="7b2dd-119">SqlClient</span></span>
<span data-ttu-id="7b2dd-120">Dans cet exemple, le code suppose que vous pouvez vous connecter à l' `Northwind` exemple de base de données sur Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7b2dd-120">The code in this example assumes that you can connect to the `Northwind` sample database on Microsoft SQL Server.</span></span> <span data-ttu-id="7b2dd-121">Le code crée une <xref:System.Data.SqlClient.SqlCommand> pour sélectionner des lignes dans la table des produits, en ajoutant un <xref:System.Data.SqlClient.SqlParameter> afin de limiter les résultats aux lignes présentant un prix unitaire supérieur à la valeur de paramètre spécifiée, dans le cas 5.</span><span class="sxs-lookup"><span data-stu-id="7b2dd-121">The code creates a <xref:System.Data.SqlClient.SqlCommand> to select rows from the Products table, adding a <xref:System.Data.SqlClient.SqlParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="7b2dd-122">Le <xref:System.Data.SqlClient.SqlConnection> est ouvert à l’intérieur d’un `using` bloc, ce qui garantit la fermeture et la suppression des ressources lorsque le code s’arrête.</span><span class="sxs-lookup"><span data-stu-id="7b2dd-122">The <xref:System.Data.SqlClient.SqlConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="7b2dd-123">Le code exécute la commande à l'aide d'un <xref:System.Data.SqlClient.SqlDataReader> et affiche les résultats dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="7b2dd-123">The code executes the command by using a <xref:System.Data.SqlClient.SqlDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/VB/source.vb#1)]

### <a name="oledb"></a><span data-ttu-id="7b2dd-124">OleDb</span><span class="sxs-lookup"><span data-stu-id="7b2dd-124">OleDb</span></span>
<span data-ttu-id="7b2dd-125">Le code de cet exemple est basé sur l'hypothèse que vous pouvez vous connecter à l'exemple de base de données Northwind Microsoft Access.</span><span class="sxs-lookup"><span data-stu-id="7b2dd-125">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="7b2dd-126">Le code crée une <xref:System.Data.OleDb.OleDbCommand> pour sélectionner des lignes dans la table des produits, en ajoutant un <xref:System.Data.OleDb.OleDbParameter> afin de limiter les résultats aux lignes présentant un prix unitaire supérieur à la valeur de paramètre spécifiée, dans le cas 5.</span><span class="sxs-lookup"><span data-stu-id="7b2dd-126">The code creates a <xref:System.Data.OleDb.OleDbCommand> to select rows from the Products table, adding a <xref:System.Data.OleDb.OleDbParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="7b2dd-127"><xref:System.Data.OleDb.OleDbConnection> s'ouvre dans un bloc `using`, ce qui garantit la fermeture et la suppression des ressources lorsque le code s'arrête.</span><span class="sxs-lookup"><span data-stu-id="7b2dd-127">The <xref:System.Data.OleDb.OleDbConnection> is opened inside of a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="7b2dd-128">Le code exécute la commande à l'aide d'un <xref:System.Data.OleDb.OleDbDataReader> et affiche les résultats dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="7b2dd-128">The code executes the command by using a <xref:System.Data.OleDb.OleDbDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/VB/source.vb#1)]

### <a name="odbc"></a><span data-ttu-id="7b2dd-129">Odbc</span><span class="sxs-lookup"><span data-stu-id="7b2dd-129">Odbc</span></span>
<span data-ttu-id="7b2dd-130">Le code de cet exemple est basé sur l'hypothèse que vous pouvez vous connecter à l'exemple de base de données Northwind Microsoft Access.</span><span class="sxs-lookup"><span data-stu-id="7b2dd-130">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="7b2dd-131">Le code crée une <xref:System.Data.Odbc.OdbcCommand> pour sélectionner des lignes dans la table des produits, en ajoutant un <xref:System.Data.Odbc.OdbcParameter> afin de limiter les résultats aux lignes présentant un prix unitaire supérieur à la valeur de paramètre spécifiée, dans le cas 5.</span><span class="sxs-lookup"><span data-stu-id="7b2dd-131">The code creates a <xref:System.Data.Odbc.OdbcCommand> to select rows from the Products table, adding a <xref:System.Data.Odbc.OdbcParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="7b2dd-132">Le <xref:System.Data.Odbc.OdbcConnection> est ouvert à l’intérieur d’un `using` bloc, ce qui garantit la fermeture et la suppression des ressources lorsque le code s’arrête.</span><span class="sxs-lookup"><span data-stu-id="7b2dd-132">The <xref:System.Data.Odbc.OdbcConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="7b2dd-133">Le code exécute la commande à l'aide d'un <xref:System.Data.Odbc.OdbcDataReader> et affiche les résultats dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="7b2dd-133">The code executes the command by using a <xref:System.Data.Odbc.OdbcDataReader>, and displays the results in the console window.</span></span>

[!code-csharp[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/CS/source.cs#1)]
[!code-vb[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/VB/source.vb#1)]

### <a name="oracleclient"></a><span data-ttu-id="7b2dd-134">OracleClient</span><span class="sxs-lookup"><span data-stu-id="7b2dd-134">OracleClient</span></span>
<span data-ttu-id="7b2dd-135">Le code de cet exemple suppose une connexion à DEMO.CUSTOMER sur un serveur Oracle.</span><span class="sxs-lookup"><span data-stu-id="7b2dd-135">The code in this example assumes a connection to DEMO.CUSTOMER on an Oracle server.</span></span> <span data-ttu-id="7b2dd-136">Vous devez également ajouter une référence au fichier System.Data.OracleClient.dll.</span><span class="sxs-lookup"><span data-stu-id="7b2dd-136">You must also add a reference to the System.Data.OracleClient.dll.</span></span> <span data-ttu-id="7b2dd-137">Ce code retourne les données dans un objet <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="7b2dd-137">The code returns the data in an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>

 [!code-csharp[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/VB/source.vb#1)]

## <a name="entity-framework-examples"></a><span data-ttu-id="7b2dd-138">Exemples de Entity Framework</span><span class="sxs-lookup"><span data-stu-id="7b2dd-138">Entity Framework examples</span></span>
<span data-ttu-id="7b2dd-139">Les listings de code suivants montrent comment récupérer des données d'une source de données en interrogeant des entités d'un modèle de données d'entité (EDM, Entity Data Model).</span><span class="sxs-lookup"><span data-stu-id="7b2dd-139">The following code listings demonstrate how to retrieve data from a data source by querying entities in an Entity Data Model (EDM).</span></span> <span data-ttu-id="7b2dd-140">Ces exemples utilisent un modèle basé sur l’exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="7b2dd-140">These examples use a model based on the Northwind sample database.</span></span> <span data-ttu-id="7b2dd-141">Pour plus d’informations sur Entity Framework, consultez [Entity Framework vue d’ensemble](./ef/overview.md).</span><span class="sxs-lookup"><span data-stu-id="7b2dd-141">For more information about Entity Framework, see [Entity Framework Overview](./ef/overview.md).</span></span>

### <a name="linq-to-entities"></a><span data-ttu-id="7b2dd-142">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="7b2dd-142">LINQ to Entities</span></span>
<span data-ttu-id="7b2dd-143">Le code dans cet exemple utilise une requête LINQ pour retourner des données en tant qu'objets Categories, qui sont projetés comme type anonyme contenant uniquement les propriétés CategoryID et CategoryName.</span><span class="sxs-lookup"><span data-stu-id="7b2dd-143">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="7b2dd-144">Pour plus d’informations, consultez [LINQ to Entities vue d’ensemble](./ef/language-reference/linq-to-entities.md).</span><span class="sxs-lookup"><span data-stu-id="7b2dd-144">For more information, see [LINQ to Entities Overview](./ef/language-reference/linq-to-entities.md).</span></span>

```csharp
using System;
using System.Linq;
using System.Data.Objects;
using NorthwindModel;

class LinqSample
{
    public static void ExecuteQuery()
    {
        using (NorthwindEntities context = new NorthwindEntities())
        {
            try
            {
                var query = from category in context.Categories
                            select new
                            {
                                categoryID = category.CategoryID,
                                categoryName = category.CategoryName
                            };

                foreach (var categoryInfo in query)
                {
                    Console.WriteLine("\t{0}\t{1}",
                        categoryInfo.categoryID, categoryInfo.categoryName);
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System.Linq
Imports System.Data.Objects
Imports NorthwindModel

Class LinqSample
    Public Shared Sub ExecuteQuery()
        Using context As NorthwindEntities = New NorthwindEntities()
            Try
                Dim query = From category In context.Categories _
                            Select New With _
                            { _
                                .categoryID = category.CategoryID, _
                                .categoryName = category.CategoryName _
                            }

                For Each categoryInfo In query
                    Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                        categoryInfo.categoryID, categoryInfo.categoryName)
                Next
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
        End Using
    End Sub
End Class
```

### <a name="typed-objectquery"></a><span data-ttu-id="7b2dd-145">ObjectQuery typé</span><span class="sxs-lookup"><span data-stu-id="7b2dd-145">Typed ObjectQuery</span></span>
<span data-ttu-id="7b2dd-146">Le code dans cet exemple utilise un <xref:System.Data.Objects.ObjectQuery%601> pour retourner des données en tant qu'objets Categories.</span><span class="sxs-lookup"><span data-stu-id="7b2dd-146">The code in this example uses an <xref:System.Data.Objects.ObjectQuery%601> to return data as Categories objects.</span></span> <span data-ttu-id="7b2dd-147">Pour plus d’informations, consultez [requêtes d’objet](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="7b2dd-147">For more information, see [Object Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)).</span></span>

```csharp
using System;
using System.Data.Objects;
using NorthwindModel;

class ObjectQuerySample
{
    public static void ExecuteQuery()
    {
        using (NorthwindEntities context = new NorthwindEntities())
        {
            ObjectQuery<Categories> categoryQuery = context.Categories;

            foreach (Categories category in
                categoryQuery.Execute(MergeOption.AppendOnly))
            {
                Console.WriteLine("\t{0}\t{1}",
                    category.CategoryID, category.CategoryName);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System.Data.Objects
Imports NorthwindModel

Class ObjectQuerySample
    Public Shared Sub ExecuteQuery()
        Using context As NorthwindEntities = New NorthwindEntities()
            Dim categoryQuery As ObjectQuery(Of Categories) = context.Categories

            For Each category As Categories In _
                categoryQuery.Execute(MergeOption.AppendOnly)
                Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                    category.CategoryID, category.CategoryName)
            Next
        End Using
    End Sub
End Class
```

### <a name="entityclient"></a><span data-ttu-id="7b2dd-148">EntityClient</span><span class="sxs-lookup"><span data-stu-id="7b2dd-148">EntityClient</span></span>
<span data-ttu-id="7b2dd-149">Le code dans cet exemple utilise une <xref:System.Data.EntityClient.EntityCommand> pour exécuter une requête Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="7b2dd-149">The code in this example uses an <xref:System.Data.EntityClient.EntityCommand> to execute an Entity SQL query.</span></span> <span data-ttu-id="7b2dd-150">Cette requête retourne une liste d'enregistrements représentant des instances du type d'entité Categories.</span><span class="sxs-lookup"><span data-stu-id="7b2dd-150">This query returns a list of records that represent instances of the Categories entity type.</span></span> <span data-ttu-id="7b2dd-151">Un <xref:System.Data.EntityClient.EntityDataReader> est utilisé pour accéder aux enregistrements de données du jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="7b2dd-151">An <xref:System.Data.EntityClient.EntityDataReader> is used to access data records in the result set.</span></span> <span data-ttu-id="7b2dd-152">Pour plus d’informations, consultez la page [Fournisseur EntityClient pour Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="7b2dd-152">For more information, see [EntityClient Provider for the Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).</span></span>

```csharp
using System;
using System.Data;
using System.Data.Common;
using System.Data.EntityClient;
using NorthwindModel;

class EntityClientSample
{
    public static void ExecuteQuery()
    {
        string queryString =
            @"SELECT c.CategoryID, c.CategoryName
                FROM NorthwindEntities.Categories AS c";

        using (EntityConnection conn =
            new EntityConnection("name=NorthwindEntities"))
        {
            try
            {
                conn.Open();
                using (EntityCommand query = new EntityCommand(queryString, conn))
                {
                    using (DbDataReader rdr =
                        query.ExecuteReader(CommandBehavior.SequentialAccess))
                    {
                        while (rdr.Read())
                        {
                            Console.WriteLine("\t{0}\t{1}", rdr[0], rdr[1]);
                        }
                    }
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System.Data
Imports System.Data.Common
Imports System.Data.EntityClient
Imports NorthwindModel

Class EntityClientSample
    Public Shared Sub ExecuteQuery()
        Dim queryString As String = _
            "SELECT c.CategoryID, c.CategoryName " & _
                "FROM NorthwindEntities.Categories AS c"

        Using conn As EntityConnection = _
            New EntityConnection("name=NorthwindEntities")

            Try
                conn.Open()
                Using query As EntityCommand = _
                New EntityCommand(queryString, conn)
                    Using rdr As DbDataReader = _
                        query.ExecuteReader(CommandBehavior.SequentialAccess)
                        While rdr.Read()
                            Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                                              rdr(0), rdr(1))
                        End While
                    End Using
                End Using
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
        End Using
    End Sub
End Class
```

## <a name="linq-to-sql"></a><span data-ttu-id="7b2dd-153">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7b2dd-153">LINQ to SQL</span></span>
<span data-ttu-id="7b2dd-154">Le code dans cet exemple utilise une requête LINQ pour retourner des données en tant qu'objets Categories, qui sont projetés comme type anonyme contenant uniquement les propriétés CategoryID et CategoryName.</span><span class="sxs-lookup"><span data-stu-id="7b2dd-154">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="7b2dd-155">Cet exemple est basé sur le contexte de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="7b2dd-155">This example is based on the Northwind data context.</span></span> <span data-ttu-id="7b2dd-156">Pour plus d’informations, consultez [prise en main](./sql/linq/getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="7b2dd-156">For more information, see [Getting Started](./sql/linq/getting-started.md).</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Northwind;

    class LinqSqlSample
    {
        public static void ExecuteQuery()
        {
            using (NorthwindDataContext db = new NorthwindDataContext())
            {
                try
                {
                    var query = from category in db.Categories
                                select new
                                {
                                    categoryID = category.CategoryID,
                                    categoryName = category.CategoryName
                                };

                    foreach (var categoryInfo in query)
                    {
                        Console.WriteLine("vbTab {0} vbTab {1}",
                            categoryInfo.categoryID, categoryInfo.categoryName);
                    }
                }
                catch (Exception ex)
                {
                    Console.WriteLine(ex.Message);
                }
            }
        }
    }
```

```vb
Option Explicit On
Option Strict On

Imports System.Collections.Generic
Imports System.Linq
Imports System.Text
Imports Northwind

Class LinqSqlSample
    Public Shared Sub ExecuteQuery()
        Using db As NorthwindDataContext = New NorthwindDataContext()
            Try
                Dim query = From category In db.Categories _
                                Select New With _
                                { _
                                    .categoryID = category.CategoryID, _
                                    .categoryName = category.CategoryName _
                                }

                For Each categoryInfo In query
                    Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                            categoryInfo.categoryID, categoryInfo.categoryName)
                Next
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
            End Using
    End Sub
End Class
```

## <a name="see-also"></a><span data-ttu-id="7b2dd-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b2dd-157">See also</span></span>

- [<span data-ttu-id="7b2dd-158">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7b2dd-158">ADO.NET Overview</span></span>](ado-net-overview.md)
- [<span data-ttu-id="7b2dd-159">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7b2dd-159">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- <span data-ttu-id="7b2dd-160">[Création d’applications de données](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h0y4a0f6(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="7b2dd-160">[Creating Data Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h0y4a0f6(v=vs.120))</span></span>
- <span data-ttu-id="7b2dd-161">[Interrogation d'un modèle EDM (Tâches Entity Framework)](https://docs.microsoft.com/previous-versions/bb738455(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="7b2dd-161">[Querying an Entity Data Model (Entity Framework Tasks)](https://docs.microsoft.com/previous-versions/bb738455(v=vs.90))</span></span>
- <span data-ttu-id="7b2dd-162">[Comment : exécuter une requête qui retourne des objets de type anonyme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7b2dd-162">[How to: Execute a Query that Returns Anonymous Type Objects](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span></span>
