---
title: DataAdapters et DataReaders
ms.date: 03/30/2017
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
ms.openlocfilehash: 20c6d514e70d2e4db451e0fff02e72688bf7d0ba
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786650"
---
# <a name="dataadapters-and-datareaders"></a>DataAdapters et DataReaders
Vous pouvez utiliser le **DataReader** ADO.net pour récupérer un flux de données avant uniquement en lecture seule à partir d’une base de données. Les résultats sont retournés à mesure que la requête s’exécute et sont stockés dans la mémoire tampon réseau sur le client jusqu’à ce que vous les interrogez à l’aide de la méthode **Read** de **DataReader**. L’utilisation du **DataReader** peut augmenter les performances de l’application en récupérant les données dès qu’elles sont disponibles et (par défaut) en stockant une seule ligne à la fois en mémoire, ce qui réduit la surcharge du système.  
  
 Un objet <xref:System.Data.Common.DataAdapter> est utilisé pour extraire les données d'une source de données et remplir les tables d'un <xref:System.Data.DataSet>. Le `DataAdapter` répercute également les modifications apportées au `DataSet` dans la source de données. `DataAdapter` utilise l'objet `Connection` du fournisseur de données .NET Framework pour se connecter à une source de données et les objets `Command` pour extraire les données de la source et y répercuter les modifications.  
  
 Chaque fournisseur de données .NET Framework inclus dans le .NET Framework comprend un objet <xref:System.Data.Common.DbDataReader> et un objet <xref:System.Data.Common.DbDataAdapter> : le fournisseur de données .NET Framework pour OLE DB inclut un objet <xref:System.Data.OleDb.OleDbDataReader> et un objet <xref:System.Data.OleDb.OleDbDataAdapter>, le fournisseur de données .NET Framework pour SQL Server inclut un objet <xref:System.Data.SqlClient.SqlDataReader> et un objet <xref:System.Data.SqlClient.SqlDataAdapter>, le fournisseur de données .NET Framework pour ODBC inclut un objet <xref:System.Data.Odbc.OdbcDataReader> et un objet <xref:System.Data.Odbc.OdbcDataAdapter>, tandis que le fournisseur de données .NET Framework pour Oracle inclut un objet <xref:System.Data.OracleClient.OracleDataReader> et un objet <xref:System.Data.OracleClient.OracleDataAdapter>.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Récupération de données à l’aide d’un DataReader](retrieving-data-using-a-datareader.md)  
 Décrit l’objet ADO.NET **DataReader** et comment l’utiliser pour retourner un flux de résultats à partir d’une source de données.  
  
 [Remplissage d’un DataSet à partir d’un DataAdapter](populating-a-dataset-from-a-dataadapter.md)  
 Explique comment remplir un `DataSet` avec des tables, des colonnes et des lignes au moyen d'un `DataAdapter`.  
  
 [Paramètres DataAdapter](dataadapter-parameters.md)  
 Décrit l'utilisation des paramètres avec les propriétés de commande d'un `DataAdapter`, y compris le mappage du contenu d'une colonne d'un `DataSet` à un paramètre de commande.  
  
 [Ajout de contraintes existantes à un DataSet](adding-existing-constraints-to-a-dataset.md)  
 Décrit comment ajouter des contraintes existantes à un `DataSet`.  
  
 [Mappages de DataAdapter, DataTable et DataColumn](dataadapter-datatable-and-datacolumn-mappings.md)  
 Décrit comment configurer des `DataTableMappings` et des `ColumnMappings` pour un `DataAdapter`.  
  
 [Pagination via un résultat de requête](paging-through-a-query-result.md)  
 Propose un exemple de visualisation des résultats d'une requête sous forme de pages de données.  
  
 [Mise à jour de sources de données avec des DataAdapters](updating-data-sources-with-dataadapters.md)  
 Explique comment utiliser un `DataAdapter` pour répercuter les modifications apportées à un objet `DataSet` dans la base de données.  
  
 [Gestion des événements DataAdapter](handling-dataadapter-events.md)  
 Décrit les événements `DataAdapter` et comment les utiliser.  
  
 [Exécution d’opérations de traitement par lots à l’aide des DataAdapters](performing-batch-operations-using-dataadapters.md)  
 Décrit l'amélioration des performances de l'application en réduisant le nombre d'allers-retours vers SQL Server lors de l'application de mises à jour à partir du `DataSet`.  
  
## <a name="see-also"></a>Voir aussi

- [Connexion à une source de données](connecting-to-a-data-source.md)
- [Commandes et paramètres](commands-and-parameters.md)
- [Transactions et accès concurrentiel](transactions-and-concurrency.md)
- [DataSets, DataTables et DataViews](./dataset-datatable-dataview/index.md)
- [Vue d’ensemble d’ADO.NET](ado-net-overview.md)
