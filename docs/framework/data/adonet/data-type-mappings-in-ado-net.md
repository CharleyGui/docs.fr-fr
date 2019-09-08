---
title: Mappages de types de données dans ADO.NET
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: 9c0d19f724c1876f7dac86055bed2ef77ac76a77
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785592"
---
# <a name="data-type-mappings-in-adonet"></a>Mappages de types de données dans ADO.NET
Le .NET Framework est basé sur le système de type commun, qui définit la manière dont les types sont déclarés, utilisés et gérés dans le runtime. Il est constitué de types de valeur et de types de référence, qui dérivent tous du type de base <xref:System.Object>. Lorsque vous travaillez avec une source de données, le type de données est déduit du fournisseur de données s'il n'est pas explicitement spécifié. Par exemple, un objet <xref:System.Data.DataSet> est indépendant de toute source de données spécifique. Les données d'un `DataSet` sont extraites d'une source de données et les modifications y sont répercutées à l'aide d'un `DataAdapter`. Cela signifie que lorsqu’un `DataAdapter` remplit <xref:System.Data.DataTable> un dans un `DataSet` avec les valeurs d’une source de données, les types de données résultants des colonnes `DataTable` dans le sont des types .NET Framework, au lieu de types spécifiques au fournisseur de données .NET Framework qui est utilisé pour se connecter à la source de données.  
  
 De même, lorsqu' `DataReader` un retourne une valeur d’une source de données, la valeur résultante est stockée dans une variable locale qui a un type de .NET Framework. Pour les `Fill` opérations `DataAdapter` `Get` du`DataReader`et des méthodes du, le type de .NET Framework est déduit de la valeur retournée par le fournisseur de données .NET Framework.  
  
 Si vous ne souhaitez pas utiliser le type de données déduit, vous pouvez appeler les méthodes d’accesseur typé du `DataReader`, lorsque vous connaissez le type spécifique de la valeur retournée. Les méthodes d’accesseur typées offrent de meilleures performances en retournant une valeur en tant que type de .NET Framework spécifique, ce qui élimine la nécessité d’une conversion de type supplémentaire.  
  
> [!NOTE]
> Les valeurs NULL pour .NET Framework types de données du fournisseur de `DBNull.Value`données sont représentées par.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Mappages de types de données SQL Server](sql-server-data-type-mappings.md)  
 Répertorie les mappages de types de données déduits et les méthodes d'accesseur de données pour <xref:System.Data.SqlClient>.  
  
 [Mappages de types de données OLE DB](ole-db-data-type-mappings.md)  
 Répertorie les mappages de types de données déduits et les méthodes d'accesseur de données pour <xref:System.Data.OleDb>.  
  
 [Mappages de types de données ODBC](odbc-data-type-mappings.md)  
 Répertorie les mappages de types de données déduits et les méthodes d'accesseur de données pour <xref:System.Data.Odbc>.  
  
 [Mappages de types de données Oracle](oracle-data-type-mappings.md)  
 Répertorie les mappages de types de données déduits et les méthodes d'accesseur de données pour <xref:System.Data.OracleClient>.  
  
 [Nombres à virgule flottante](floating-point-numbers.md)  
 Décrit les problèmes que les développeurs rencontrent fréquemment lorsqu'ils utilisent des nombres à virgule flottante.  
  
## <a name="see-also"></a>Voir aussi

- [Types de données SQL Server et ADO.NET](./sql/sql-server-data-types.md)
- [Configuration des paramètres et des types de données des paramètres](configuring-parameters-and-parameter-data-types.md)
- [Récupération des informations de schéma de base de données](retrieving-database-schema-information.md)
- [Système de type commun](../../../standard/base-types/common-type-system.md)
- [Conversion de types](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))
- [Vue d’ensemble d’ADO.NET](ado-net-overview.md)
