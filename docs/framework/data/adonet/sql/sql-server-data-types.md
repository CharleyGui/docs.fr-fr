---
title: Types de données SQL Server et ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: db4618ac624ea8401cab682a8c21d8f23c253d05
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155456"
---
# <a name="sql-server-data-types-and-adonet"></a>Types de données SQL Server et ADO.NET

SQL Server et le .NET Framework sont basés sur des systèmes de types différents, ce qui peut entraîner une perte de données potentielle. Afin de protéger l’intégrité des données, le fournisseur de données .NET Framework pour SQL Server (<xref:System.Data.SqlClient>) fournit des méthodes d’accesseur typé pour utiliser les données SQL Server. Vous pouvez utiliser les énumérations dans les classes <xref:System.Data.SqlDbType> pour spécifier les types de données <xref:System.Data.SqlClient.SqlParameter>.  
  
 Pour plus d’informations et pour obtenir un tableau décrivant les mappages de types de données entre SQL Server et les types de données .NET Framework, consultez [SQL Server mappages de types de données](../sql-server-data-type-mappings.md).  
  
 SQL Server 2008 introduit de nouveaux types de données conçus pour répondre aux besoins professionnels pour travailler avec des données de date et d’heure, structurées, semi-structurées et non structurées. Ceux-ci sont décrits dans la Documentation en ligne de SQL Server 2008.  
  
 Les types de données SQL Server qui peuvent être utilisés dans votre application dépendent de la version de SQL Server que vous utilisez. Pour plus d'informations, consultez la version appropriée de la documentation en ligne de SQL Server dans le tableau suivant.  
  
 **Documentation SQL Server**  
  
1. [Types de données (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)  
  
## <a name="in-this-section"></a>Dans cette section  

 [SqlTypes et le DataSet](sqltypes-and-the-dataset.md)  
 Décrit la prise en charge de type pour `SqlTypes` dans le `DataSet`.  
  
 [Gestion des valeurs null](handling-null-values.md)  
 Montre comment utiliser des valeurs null et une logique à trois valeurs.  
  
 [Comparaison du GUID et des valeurs uniqueidentifier](comparing-guid-and-uniqueidentifier-values.md)  
 Montre comment utiliser des valeurs GUID et d'identificateur unique dans SQL Server et le .NET Framework.  
  
 [Données de date et d’heure](date-and-time-data.md)  
 Décrit comment utiliser les nouveaux types de données de date et d’heure introduits dans SQL Server 2008.  
  
 [UDT volumineux](large-udts.md)  
 Montre comment récupérer des données à partir des UDT de valeur élevée introduits dans SQL Server 2008.  
  
 [Données XML dans SQL Server](xml-data-in-sql-server.md)  
 Décrit comment utiliser des données XML extraites de SQL Server.  
  
## <a name="reference"></a>Informations de référence  

 <xref:System.Data.DataSet>  
 Décrit la classe `DataSet` et tous ses membres.  
  
 <xref:System.Data.SqlTypes>  
 Décrit l’espace de noms `SqlTypes` et tous ses membres.  
  
 <xref:System.Data.SqlDbType>  
 Décrit l’énumération `SqlDbType` et tous ses membres.  
  
 <xref:System.Data.DbType>  
 Décrit l’énumération `DbType` et tous ses membres.  
  
## <a name="see-also"></a>Voir aussi

- [Mappages de types de données SQL Server](../sql-server-data-type-mappings.md)
- [Configuration des paramètres et des types de données des paramètres](../configuring-parameters-and-parameter-data-types.md)
- [Paramètres table](table-valued-parameters.md)
- [SQL Server des données binaires et de grande valeur](sql-server-binary-and-large-value-data.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
