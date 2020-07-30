---
title: Opérations de quantificateur (C#)
description: En savoir plus sur les opérations de quantificateur. Ces opérations retournent une valeur booléenne indiquant si certains ou tous les éléments d’une séquence satisfont à une condition.
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: ce06f887d3ad7b10cbdedf9e33072df2c0819ef1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299147"
---
# <a name="quantifier-operations-c"></a>Opérations de quantificateur (C#)
Les opérations de quantificateur retournent une valeur <xref:System.Boolean> qui indique si certains ou tous les éléments d’une séquence remplissent une condition.  
  
 L’illustration suivante représente deux opérations de quantificateur différentes sur deux séquences sources différentes. La première opération demande si un ou plusieurs des éléments sont le caractère 'A' et le résultat est `true`. La deuxième opération demande si tous les éléments sont le caractère 'A' et le résultat est `true`.  
  
 ![Opérations de quantificateur LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 Les méthodes d’opérateur de requête standard qui effectuent des opérations de quantificateur sont répertoriées dans la section suivante.  
  
## <a name="methods"></a>Méthodes  
  
|Nom de la méthode|Description|Syntaxe d'expression de requête C#|Informations complémentaires|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Tous|Détermine si tous les éléments d’une séquence remplissent une condition.|Non applicable.|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|Quelconque|Détermine si certains éléments d’une séquence remplissent une condition.|Non applicable.|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|Contient|Détermine si une séquence contient un élément spécifié.|Non applicable.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a>Exemples de syntaxe d'expression de requête  
  
### <a name="all"></a>Tous  
L’exemple suivant utilise `All` pour vérifier que toutes les chaînes ont une longueur spécifique.
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a>Quelconque  
L’exemple suivant utilise `Any` pour vérifier que toutes les chaînes commencent par « o ».  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a>Contient  
L’exemple suivant utilise `Contains` pour vérifier qu’un tableau a un élément spécifique.  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Linq>
- [Vue d’ensemble des opérateurs de requête standard (C#)](./standard-query-operators-overview.md)
- [Spécifier dynamiquement des filtres de prédicat au moment de l’exécution](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [Comment interroger des phrases qui contiennent un ensemble de mots spécifié (LINQ) (C#)](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
