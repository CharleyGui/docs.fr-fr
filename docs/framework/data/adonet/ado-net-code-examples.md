---
title: Exemples de code
description: Ces exemples montrent .NET Framework aux programmeurs comment récupérer des données d’une base de données à l’aide des fournisseurs de données ADO.NET et des Entity Framework ADO.NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c119657a-9ce6-4940-91e4-ac1d5f0d9584
ms.openlocfilehash: 9d12c7c7dcbc3a24cf51ade5481f59715c4c4d88
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555105"
---
# <a name="adonet-code-examples"></a>Exemples de code ADO.NET

Les listes de code sur cette page montrent comment récupérer des données à partir d’une base de données à l’aide des technologies ADO.NET suivantes :

- Fournisseurs de données ADO.NET :

  - [SqlClient](#sqlclient) ( `System.Data.SqlClient` )

  - [OLEDB](#oledb) ( `System.Data.OleDb` )

  - [ODBC](#odbc) ( `System.Data.Odbc` )

  - [OracleClient](#oracleclient) ( `System.Data.OracleClient` )

- ADO.NET Entity Framework :

  - [LINQ to Entities](#linq-to-entities)

  - [ObjectQuery typé](#typed-objectquery)

  - [EntityClient](#entityclient) ( `System.Data.EntityClient` )

- [LINQ to SQL](#linq-to-sql)

## <a name="adonet-data-provider-examples"></a>Exemples de fournisseurs de données ADO.NET
Les listings de code suivants montrent comment récupérer des données d'une base de données à l'aide des fournisseurs de données ADO.NET. Les données sont retournées dans un `DataReader`. Pour plus d’informations, consultez [récupération de données à l’aide d’un DataReader](retrieving-data-using-a-datareader.md).

### <a name="sqlclient"></a>SqlClient
Dans cet exemple, le code suppose que vous pouvez vous connecter à l' `Northwind` exemple de base de données sur Microsoft SQL Server. Le code crée une <xref:System.Data.SqlClient.SqlCommand> pour sélectionner des lignes dans la table des produits, en ajoutant un <xref:System.Data.SqlClient.SqlParameter> afin de limiter les résultats aux lignes présentant un prix unitaire supérieur à la valeur de paramètre spécifiée, dans le cas 5. Le <xref:System.Data.SqlClient.SqlConnection> est ouvert à l’intérieur d’un `using` bloc, ce qui garantit la fermeture et la suppression des ressources lorsque le code s’arrête. Le code exécute la commande à l'aide d'un <xref:System.Data.SqlClient.SqlDataReader> et affiche les résultats dans la fenêtre de console.

 [!code-csharp[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/VB/source.vb#1)]

### <a name="oledb"></a>OleDb
Le code de cet exemple est basé sur l'hypothèse que vous pouvez vous connecter à l'exemple de base de données Northwind Microsoft Access. Le code crée une <xref:System.Data.OleDb.OleDbCommand> pour sélectionner des lignes dans la table des produits, en ajoutant un <xref:System.Data.OleDb.OleDbParameter> afin de limiter les résultats aux lignes présentant un prix unitaire supérieur à la valeur de paramètre spécifiée, dans le cas 5. <xref:System.Data.OleDb.OleDbConnection> s'ouvre dans un bloc `using`, ce qui garantit la fermeture et la suppression des ressources lorsque le code s'arrête. Le code exécute la commande à l'aide d'un <xref:System.Data.OleDb.OleDbDataReader> et affiche les résultats dans la fenêtre de console.

 [!code-csharp[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/VB/source.vb#1)]

### <a name="odbc"></a>Odbc
Le code de cet exemple est basé sur l'hypothèse que vous pouvez vous connecter à l'exemple de base de données Northwind Microsoft Access. Le code crée une <xref:System.Data.Odbc.OdbcCommand> pour sélectionner des lignes dans la table des produits, en ajoutant un <xref:System.Data.Odbc.OdbcParameter> afin de limiter les résultats aux lignes présentant un prix unitaire supérieur à la valeur de paramètre spécifiée, dans le cas 5. Le <xref:System.Data.Odbc.OdbcConnection> est ouvert à l’intérieur d’un `using` bloc, ce qui garantit la fermeture et la suppression des ressources lorsque le code s’arrête. Le code exécute la commande à l'aide d'un <xref:System.Data.Odbc.OdbcDataReader> et affiche les résultats dans la fenêtre de console.

[!code-csharp[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/CS/source.cs#1)]
[!code-vb[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/VB/source.vb#1)]

### <a name="oracleclient"></a>OracleClient
Le code de cet exemple suppose une connexion à DEMO.CUSTOMER sur un serveur Oracle. Vous devez également ajouter une référence au fichier System.Data.OracleClient.dll. Ce code retourne les données dans un objet <xref:System.Data.OracleClient.OracleDataReader>.

 [!code-csharp[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/VB/source.vb#1)]

## <a name="entity-framework-examples"></a>Exemples de Entity Framework
Les listings de code suivants montrent comment récupérer des données d'une source de données en interrogeant des entités d'un modèle de données d'entité (EDM, Entity Data Model). Ces exemples utilisent un modèle basé sur l’exemple de base de données Northwind. Pour plus d’informations sur Entity Framework, consultez [Entity Framework vue d’ensemble](./ef/overview.md).

### <a name="linq-to-entities"></a>LINQ to Entities
Le code dans cet exemple utilise une requête LINQ pour retourner des données en tant qu'objets Categories, qui sont projetés comme type anonyme contenant uniquement les propriétés CategoryID et CategoryName. Pour plus d’informations, consultez [LINQ to Entities vue d’ensemble](./ef/language-reference/linq-to-entities.md).

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

### <a name="typed-objectquery"></a>ObjectQuery typé
Le code dans cet exemple utilise un <xref:System.Data.Objects.ObjectQuery%601> pour retourner des données en tant qu'objets Categories. Pour plus d’informations, consultez [requêtes d’objet](/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)).

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

### <a name="entityclient"></a>EntityClient
Le code dans cet exemple utilise une <xref:System.Data.EntityClient.EntityCommand> pour exécuter une requête Entity SQL. Cette requête retourne une liste d'enregistrements représentant des instances du type d'entité Categories. Un <xref:System.Data.EntityClient.EntityDataReader> est utilisé pour accéder aux enregistrements de données du jeu de résultats. Pour plus d’informations, consultez la page [Fournisseur EntityClient pour Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).

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

## <a name="linq-to-sql"></a>LINQ to SQL
Le code dans cet exemple utilise une requête LINQ pour retourner des données en tant qu'objets Categories, qui sont projetés comme type anonyme contenant uniquement les propriétés CategoryID et CategoryName. Cet exemple est basé sur le contexte de données Northwind. Pour plus d’informations, consultez [prise en main](./sql/linq/getting-started.md).

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

## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
- [Extraction et modification de données dans ADO.NET](retrieving-and-modifying-data.md)
- [Création d’applications de données](/previous-versions/visualstudio/visual-studio-2013/h0y4a0f6(v=vs.120))
- [Interrogation d'un modèle EDM (Tâches Entity Framework)](/previous-versions/bb738455(v=vs.90))
- [Comment : exécuter une requête qui retourne des objets de type anonyme](/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))
