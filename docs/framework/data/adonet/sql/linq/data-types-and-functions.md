---
title: Fonctions et types de données
ms.date: 03/30/2017
ms.assetid: 683413c5-0312-4e60-8619-9a97bdc6e62a
ms.openlocfilehash: 456cf5acf42221379e68ff79ee57c084664e30e5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147760"
---
# <a name="data-types-and-functions"></a>Fonctions et types de données

Les rubriques répertoriées dans le tableau suivant décrivent la prise en charge de LINQ to SQL pour les membres, les constructions et les casts du Common Language Runtime (CLR). Les membres et constructions pris en charge peuvent être utilisés dans vos requêtes LINQ to SQL.  
  
 Un élément non pris en charge dans le tableau signifie que LINQ to SQL ne peut pas traduire le membre, la construction ou le cast CLR pour qu'ils soient exécutés sur le serveur SQL Server. Vous pouvez toujours les utiliser dans votre code, mais ils doivent être évalués avant la traduction de la requête en données Transact-SQL ou après l'extraction des résultats de la base de données.  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Mappage de type SQL-CLR](sql-clr-type-mapping.md)|Fournit une matrice détaillée des mappages entre les types CLR et les types SQL Server.|  
|[Types de données de base](basic-data-types.md)|Résume les différences de comportement par rapport au .NET Framework.|  
|[Types de données Boolean](boolean-data-types.md)|Résume les différences de comportement par rapport au .NET Framework.|  
|[Sémantique Null](null-semantics.md)|Fournit des liens vers des rubriques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] qui abordent les questions des types null et nullables.|  
|[Opérateurs de comparaison et opérateurs numériques](numeric-and-comparison-operators.md)|Résume les différences de comportement par rapport au .NET Framework.|  
|[Opérateurs de séquence](sequence-operators.md)|Résume les différences de comportement par rapport au .NET Framework.|  
|[System.Convert, méthodes](system-convert-methods.md)|Résume les différences de comportement par rapport au .NET Framework.|  
|[System.DateTime, méthodes](system-datetime-methods.md)|Décrit la prise en charge de LINQ to SQL pour les membres de la structure <xref:System.DateTime?displayProperty=nameWithType>.|  
|[System.DateTimeOffset, méthodes](system-datetimeoffset-methods.md)|Décrit la prise en charge de LINQ to SQL pour les membres de la structure <xref:System.DateTimeOffset?displayProperty=nameWithType>.|  
|[System.Math, méthodes](system-math-methods.md)|Résume les différences de comportement par rapport au .NET Framework.|  
|[System.Object, méthodes](system-object-methods.md)|Résume les différences de comportement par rapport au .NET Framework.|  
|[System.String, méthodes](system-string-methods.md)|Résume les différences de comportement par rapport au .NET Framework.|  
|[System.TimeSpan, méthodes](system-timespan-methods.md)|Décrit la prise en charge de LINQ to SQL pour les membres de la structure <xref:System.TimeSpan?displayProperty=nameWithType>.|  
|[Fonctionnalités non prises en charge](unsupported-functionality.md)|Décrit les fonctionnalités qui ne sont pas prises en charge dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
  
## <a name="see-also"></a>Voir aussi

- [Incompatibilité entre types SQL-CLR](sql-clr-type-mismatches.md)
- [Référence](reference.md)
