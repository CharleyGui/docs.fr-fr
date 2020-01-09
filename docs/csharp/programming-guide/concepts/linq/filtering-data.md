---
title: Filtrage des données (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 74399244990f8ff2deaa1d10576ea94a57c16bee
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346992"
---
# <a name="filtering-data-c"></a>Filtrage des données (C#)
Le filtrage fait référence à l’opération de restriction du jeu de résultats pour que celui-ci contienne uniquement les éléments qui répondent à une condition spécifiée. Cette opération est également appelée « sélection ».  
  
 L’illustration suivante montre les résultats du filtrage d’une séquence de caractères. Le prédicat de l’opération de filtrage spécifie que le caractère doit être « A ».  
  
 ![Diagramme illustrant une opération de filtrage LINQ](./media/filtering-data/linq-filter-operation.png)  
  
 Les méthodes d’opérateurs de requête standard qui effectuent des opérations de sélection sont répertoriées dans la section suivante.  
  
## <a name="methods"></a>Méthodes  
  
|Nom de la méthode|Description|Syntaxe d'expression de requête C#|Plus d’informations|  
|-----------------|-----------------|---------------------------------|----------------------|  
|OfType|Sélectionne des valeurs, en fonction de leur capacité à être castées en un type spécifié.|Non applicable.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|Où|Sélectionne les valeurs qui sont basées sur une fonction de prédicat.|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
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
- [Vue d’ensemble des opérateurs de requête standard (C#)](./standard-query-operators-overview.md)
- [where, clause](../../../language-reference/keywords/where-clause.md)
- [Spécifier dynamiquement des filtres de prédicat au moment de l’exécution](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [Comment interroger les métadonnées d’un assembly avec la réflexionC#(LINQ) ()](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [Comment interroger des fichiers ayant un attribut ou un nom spécifiéC#()](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [Guide pratique pour trier ou filtrer des données texte par mot ou par champ (LINQC#) ()](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
