---
title: LIMIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: 432dfe2c8b2b87daf885be6de4da9bbeaaa37638
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250444"
---
# <a name="limit-entity-sql"></a>LIMIT (Entity SQL)
Une pagination physique peut être effectuée par le biais de la sous-clause LIMIT de la clause ORDER BY. La sous-clause LIMIT ne peut pas être utilisée sans la clause ORDER BY.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a>Arguments  
 `n`  
 Nombre d'éléments qui seront sélectionnés.  
  
 Si une sous-clause d'expression LIMIT est présente dans une clause ORDER BY, la requête sera triée en fonction de la spécification de classement et le nombre de lignes obtenu sera limité par l'expression LIMIT. Par exemple, LIMIT 5 limitera le jeu de résultats à 5 instances ou lignes. LIMIT est d'un point de vue fonctionnel équivalent à TOP, sauf que LIMIT a besoin de la présence de la clause ORDER BY. SKIP et LIMIT peuvent être utilisés indépendamment avec la clause ORDER BY.  
  
> [!NOTE]
> Une requête Entity SQL est considérée comme non valide si le modificateur TOP et la sous-clause SKIP se trouvent dans une même expression de requête. La requête doit être réécrite en remplaçant l'expression TOP par l'expression LIMIT.  
  
## <a name="example"></a>Exemples  
 La requête Entity SQL suivante utilise l'opérateur ORDER BY avec LIMIT pour spécifier l'ordre de classement employé sur les objets retournés dans une instruction SELECT. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure décrite [dans la rubrique Procédure : Exécutez une requête qui retourne les résultats](../how-to-execute-a-query-that-returns-structuraltype-results.md)de StructuralType.  
  
2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a>Voir aussi

- [ORDER BY](order-by-entity-sql.md)
- [Guide pratique pour Page des résultats de la requête](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [Pagination](paging-entity-sql.md)
- [TOP](top-entity-sql.md)
