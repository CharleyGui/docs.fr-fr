---
title: Tri des données (C#)
description: En savoir plus sur les opérations de tri et les méthodes d’opérateur de requête standard qui effectuent des opérations de tri dans LINQ en C#.
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 5feeb0e2229fc370fdcb9608817f41832bffd7cc
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302332"
---
# <a name="sorting-data-c"></a>Tri des données (C#)
Une opération de tri ordonne les éléments d’une séquence en fonction d’un ou de plusieurs attributs. Le premier critère de tri effectue un tri principal sur les éléments. En spécifiant un deuxième critère de tri, vous pouvez trier les éléments dans chaque groupe de tri principal.  
  
 L’illustration suivante montre les résultats d’une opération de tri par ordre alphabétique sur une séquence de caractères :
  
 ![Graphique montrant une opération de tri par ordre alphabétique.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 Les méthodes d’opérateurs de requête standard qui trient les données sont répertoriées dans la section suivante.  
  
## <a name="methods"></a>Méthodes  
  
|Nom de la méthode|Description|Syntaxe d'expression de requête C#|Informations complémentaires|  
|-----------------|-----------------|---------------------------------|----------------------|  
|OrderBy|Trie les valeurs dans l’ordre croissant.|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|OrderByDescending|Trie les valeurs dans l’ordre décroissant.|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|ThenBy|Effectue un tri secondaire dans l’ordre croissant.|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|ThenByDescending|Effectue un tri secondaire dans l’ordre décroissant.|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|Inverser|Inverse l’ordre des éléments dans une collection.|Non applicable.|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Exemples de syntaxe d'expression de requête  
  
### <a name="primary-sort-examples"></a>Exemples de tri principal  
  
#### <a name="primary-ascending-sort"></a>Tri principal croissant  
 L’exemple suivant montre comment utiliser la clause `orderby` dans une requête LINQ pour trier les chaînes dans un tableau par longueur de chaîne, dans l’ordre croissant.  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    brown  
    jumps  
*/  
```  
  
#### <a name="primary-descending-sort"></a>Tri principal décroissant  
 L’exemple suivant montre comment utiliser la clause `orderby descending` dans une requête LINQ pour trier les chaînes selon leur première lettre, dans l’ordre décroissant.  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    quick  
    jumps  
    fox  
    brown  
*/  
```  
  
### <a name="secondary-sort-examples"></a>Exemples de tri secondaire  
  
#### <a name="secondary-ascending-sort"></a>Tri secondaire croissant  
 L’exemple suivant montre comment utiliser la clause `orderby` dans une requête LINQ pour effectuer un tri principal et un tri secondaire des chaînes dans un tableau. Les chaînes sont triées en premier lieu selon leur longueur, puis secondairement en fonction de la première lettre de la chaîne, chaque fois dans l’ordre croissant.  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1)  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    fox  
    the  
    brown  
    jumps  
    quick  
*/  
```  
  
#### <a name="secondary-descending-sort"></a>Tri secondaire décroissant  
 L’exemple suivant montre comment utiliser la clause `orderby descending` dans une requête LINQ pour effectuer un tri principal dans l’ordre croissant et un tri secondaire dans l’ordre décroissant. Les chaînes sont triées en premier lieu selon leur longueur, puis secondairement en fonction de la première lettre de la chaîne.  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    jumps  
    brown  
*/  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Linq>
- [Vue d’ensemble des opérateurs de requête standard (C#)](./standard-query-operators-overview.md)
- [orderby, clause](../../../language-reference/keywords/orderby-clause.md)
- [Classer les résultats d’une clause join](../../../linq/order-the-results-of-a-join-clause.md)
- [Guide pratique pour trier ou filtrer des données texte par mot ou par champ (LINQ) (C#)](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
