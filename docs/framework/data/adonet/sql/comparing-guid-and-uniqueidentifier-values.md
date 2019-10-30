---
title: Comparaison du GUID et des valeurs uniqueidentifier
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: aababd75-2335-43e3-ace8-4b7ae84191a8
ms.openlocfilehash: 18f7ad8f6ef9cdf726bdf606ab108e2c5140aed7
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040466"
---
# <a name="comparing-guid-and-uniqueidentifier-values"></a>Comparaison du GUID et des valeurs uniqueidentifier
Le type de données GUID (Identificateur Global Unique) dans SQL Server est représenté par le type de données `uniqueidentifier`, qui stocke une valeur binaire de 16 octets. Un GUID est un nombre binaire et son usage principal est celui d'identificateur qui doit être unique dans un réseau comportant de nombreux ordinateurs implantés dans de nombreux sites. Il est possible de générer des GUID en appelant la fonction Transact-SQL NEWID et il est garanti qu'ils sont uniques dans le monde entier. Pour plus d’informations, consultez [uniqueidentifier (Transact-SQL)](/sql/t-sql/data-types/uniqueidentifier-transact-sql).  
  
## <a name="working-with-sqlguid-values"></a>Utilisation de valeurs SqlGuid  
 Comme les valeurs GUID sont longues et obscures, elles ont peu de signification pour les utilisateurs. Si des GUID générés de façon aléatoire sont utilisés pour les valeurs clés et si vous insérez un grand nombre de lignes, vous obtenez des E/S aléatoires dans les index, ce qui peut contribuer à altérer les performances. Les GUID sont également relativement volumineux en comparaison d'autres types de données. En règle générale, il est recommandé d'utiliser les GUID uniquement pour des scénarios très restrictifs pour lesquels aucun autre type de données ne convient.  
  
### <a name="comparing-guid-values"></a>Comparaison de valeurs GUID  
 Des opérateurs de comparaison peuvent être utilisés avec des valeurs `uniqueidentifier`. Toutefois, la mise en ordre n’est pas implémentée en comparant les modèles binaires des deux valeurs. Les seules opérations autorisées sur une valeur `uniqueidentifier` sont les comparaisons (=, < >, \<, >, \<=, > =) et la recherche de valeurs NULL (IS NULL et IS NOT NULL). Aucun autre opérateur arithmétique n'est autorisé.  
  
 <xref:System.Guid> et <xref:System.Data.SqlTypes.SqlGuid> possèdent tous deux une méthode `CompareTo` pour comparer différentes valeurs GUID. Toutefois, `System.Guid.CompareTo` et `SqlTypes.SqlGuid.CompareTo` sont implémentés différemment. <xref:System.Data.SqlTypes.SqlGuid> implémente `CompareTo` à l'aide du comportement SQL Server, dans lequel les six derniers octets d'une valeur sont significatifs. <xref:System.Guid> évalue les 16 octets. L'exemple suivant illustre cette différence de comportement. La première section du code affiche les valeurs <xref:System.Guid> non triées et la seconde les valeurs <xref:System.Guid> triées. La troisième section affiche les valeurs <xref:System.Data.SqlTypes.SqlGuid> triées. La sortie s'affiche sous les codes.  
  
 [!code-csharp[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/VB/source.vb#1)]  
  
 Cet exemple génère les résultats suivants :  
  
```output  
Unsorted Guids:  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
  
Sorted Guids:  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
  
Sorted SqlGuids:  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
```  
  
## <a name="see-also"></a>Voir aussi

- [Types de données SQL Server et ADO.NET](sql-server-data-types.md)
- [Vue d’ensemble d’ADO.NET](../ado-net-overview.md)
