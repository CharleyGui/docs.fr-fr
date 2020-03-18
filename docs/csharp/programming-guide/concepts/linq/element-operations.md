---
title: Opérations d’éléments (C#)
ms.date: 10/03/2018
ms.assetid: 283206c9-3246-4c48-b01a-d9de409a7231
ms.openlocfilehash: e9ec41793afffe60a7184622f91b5fc023e0958f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345160"
---
# <a name="element-operations-c"></a>Opérations d’éléments (C#)

Les opérations d’éléments retournent un élément unique et spécifique à partir d’une séquence.  
  
 Les méthodes d’opérateurs de requête standard qui effectuent des opérations d’éléments sont répertoriées dans la section suivante.  
  
## <a name="methods"></a>Méthodes  
  
|Nom de la méthode|Description|Syntaxe d'expression de requête C#|Informations complémentaires|  
|-----------------|-----------------|---------------------------------|----------------------|  
|ElementAt|Retourne l’élément situé à un index spécifié dans une collection.|Non applicable.|<xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=nameWithType>|  
|ElementAtOrDefault|Retourne l’élément situé à un index spécifié dans une collection ou une valeur par défaut si l’index est hors limites.|Non applicable.|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=nameWithType>|  
|Premier|Retourne le premier élément d’une collection ou le premier élément qui remplit une condition.|Non applicable.|<xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.First%2A?displayProperty=nameWithType>|  
|FirstOrDefault|Retourne le premier élément d’une collection ou le premier élément qui remplit une condition. Retourne une valeur par défaut s’il n’existe aucun élément répondant aux critères.|Non applicable.|<xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=nameWithType>|  
|Dernier|Retourne le dernier élément d’une collection ou le dernier élément qui remplit une condition.|Non applicable.|<xref:System.Linq.Enumerable.Last%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Last%2A?displayProperty=nameWithType>|  
|LastOrDefault|Retourne le dernier élément d’une collection ou le dernier élément qui remplit une condition. Retourne une valeur par défaut s’il n’existe aucun élément répondant aux critères.|Non applicable.|<xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=nameWithType>|  
|Unique|Retourne le seul élément d’une collection ou le seul élément qui remplit une condition. Lève une <xref:System.InvalidOperationException> s’il n’y a aucun élément ou s’il y a plusieurs éléments à retourner. |Non applicable.|<xref:System.Linq.Enumerable.Single%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Single%2A?displayProperty=nameWithType>|  
|SingleOrDefault|Retourne le seul élément d’une collection ou le seul élément qui remplit une condition. Retourne une valeur par défaut s’il n’y a aucun élément à retourner. Lève une <xref:System.InvalidOperationException> s’il y a plusieurs éléments à retourner. |Non applicable.|<xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Linq>
- [Vue d’ensemble des opérateurs de requête standard (C#)](./standard-query-operators-overview.md)
- [Comment interroger le plus grand fichier ou fichiers dans un arbre d’annuaire (LINQ) (C)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
