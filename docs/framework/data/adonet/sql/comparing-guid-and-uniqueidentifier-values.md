---
title: Comparaison du GUID et des valeurs uniqueidentifier
description: Découvrez comment créer et comparer des valeurs GUID dans le Fournisseur de données .NET Framework pour SQL Server, qui sont représentées par le type de données uniqueidentifier.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: aababd75-2335-43e3-ace8-4b7ae84191a8
ms.openlocfilehash: 245b7246712822043d302c43a765c29ac2090e00
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286505"
---
# <a name="comparing-guid-and-uniqueidentifier-values"></a>Comparaison du GUID et des valeurs uniqueidentifier
Le type de données d’identificateur global unique (GUID) dans SQL Server est représenté par le type de données `uniqueidentifier`, qui stocke une valeur binaire de 16 octets. Un GUID est un nombre binaire, principalement utilisé en tant qu’identificateur qui doit être unique dans un réseau qui comprend de nombreux ordinateurs répartis sur plusieurs sites. Les GUID peuvent être générés en appelant la fonction Transact-SQL NEWID et sont assurés d’être uniques dans le monde entier. Pour plus d’informations, consultez [uniqueidentifier (Transact-SQL)](/sql/t-sql/data-types/uniqueidentifier-transact-sql).  
  
## <a name="working-with-sqlguid-values"></a>Utilisation de valeurs SqlGuid  
 Étant donné que les GUID sont des valeurs longues et peut intelligibles, ils sont utiles pour les utilisateurs. Si des GUID générés de manière aléatoire sont utilisés pour des valeurs clés et que vous insérez un grand nombre de lignes, vous recevez des e/s aléatoires dans vos index, ce qui peut avoir un impact négatif sur les performances. Les GUID sont également relativement volumineux lorsqu’ils sont comparés à d’autres types de données. En général, nous vous recommandons d’utiliser des GUID uniquement pour des scénarios très étroits pour lesquels aucun autre type de données ne convient.  
  
### <a name="comparing-guid-values"></a>Comparaison de valeurs GUID  
 Des opérateurs de comparaison peuvent être utilisés avec des valeurs `uniqueidentifier`. Toutefois, le classement n'est pas effectué par la comparaison des configurations binaires des deux valeurs. Les seules opérations autorisées sur une `uniqueidentifier` valeur sont les comparaisons (=,  <>, \<, > , \<=, > =) et la recherche de valeurs NULL (IS NULL et is not null). Aucun autre opérateur arithmétique n'est autorisé.  
  
 <xref:System.Guid> et <xref:System.Data.SqlTypes.SqlGuid> disposent d’une méthode `CompareTo` pour comparer différentes valeurs de GUID. Toutefois, `System.Guid.CompareTo` et `SqlTypes.SqlGuid.CompareTo` sont implémentés différemment. <xref:System.Data.SqlTypes.SqlGuid> implémente `CompareTo` à l'aide du comportement de SQL Server, dans lequel les 6 derniers octets d'une valeur sont importants. <xref:System.Guid> évalue les 16 octets. L’exemple suivant illustre cette différence de comportement. La première section de code affiche des valeurs <xref:System.Guid> non triées et la deuxième section de code affiche les valeurs <xref:System.Guid> triées. La troisième section affiche les valeurs <xref:System.Data.SqlTypes.SqlGuid> triées. Le résultat est affiché sous la liste de codes.  
  
 [!code-csharp[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/VB/source.vb#1)]  
  
 Cet exemple produit les résultats suivants.  
  
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
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
