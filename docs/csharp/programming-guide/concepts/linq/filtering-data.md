---
title: Filtrage des données (C#)
description: Le filtrage, également appelé « sélection », limite les résultats en fonction d’une condition. En savoir plus sur les méthodes d’opérateur de requête standard dans LINQ en C# qui effectuent le filtrage.
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 51bf9f930ba67ba07c7c0f357910d5e36014138d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186040"
---
# <a name="filtering-data-c"></a>Filtrage des données (C#)

Le filtrage fait référence à l’opération de restriction du jeu de résultats pour que celui-ci contienne uniquement les éléments qui répondent à une condition spécifiée. Cette opération est également appelée « sélection ».  
  
 L’illustration suivante montre les résultats du filtrage d’une séquence de caractères. Le prédicat de l’opération de filtrage spécifie que le caractère doit être « A ».  
  
 ![Diagramme illustrant une opération de filtrage LINQ](./media/filtering-data/linq-filter-operation.png)  
  
 Les méthodes d’opérateurs de requête standard qui effectuent des opérations de sélection sont répertoriées dans la section suivante.  
  
## <a name="methods"></a>Méthodes  
  
|Nom de la méthode|Description|Syntaxe d'expression de requête C#|Informations complémentaires|  
|-----------------|-----------------|---------------------------------|----------------------|  
|OfType|Sélectionne des valeurs, en fonction de leur capacité à être castées en un type spécifié.|Non applicable.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|Where|Sélectionne les valeurs qui sont basées sur une fonction de prédicat.|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Exemple de syntaxe d’expression de requête  

 L’exemple suivant utilise la clause `where` pour filtrer les chaînes d’un tableau qui ont une longueur spécifique.  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            where word.Length == 3  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
*/  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Linq>
- [Présentation des opérateurs de requête standard (C#)](./standard-query-operators-overview.md)
- [clause WHERE](../../../language-reference/keywords/where-clause.md)
- [Spécifier dynamiquement des filtres de prédicat au moment de l’exécution](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [Comment interroger les métadonnées d’un assembly avec la réflexion (LINQ) (C#)](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [Comment rechercher des fichiers avec un attribut ou un nom spécifié (C#)](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [Guide pratique pour trier ou filtrer des données texte par mot ou par champ (LINQ) (C#)](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
