---
title: Tri des données
ms.date: 07/20/2015
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
ms.openlocfilehash: a5ccff745995ed7f41731cf98fb7c49d3247d994
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406792"
---
# <a name="sorting-data-visual-basic"></a>Tri des données (Visual Basic)

Une opération de tri ordonne les éléments d’une séquence en fonction d’un ou de plusieurs attributs. Le premier critère de tri effectue un tri principal sur les éléments. En spécifiant un deuxième critère de tri, vous pouvez trier les éléments dans chaque groupe de tri principal.

L’illustration suivante montre les résultats d’une opération de tri alphabétique sur une séquence de caractères.

![Graphique montrant une opération de tri par ordre alphabétique.](./media/sorting-data/alphabetical-sort-operation.png)

Les méthodes d’opérateurs de requête standard qui trient les données sont répertoriées dans la section suivante.

## <a name="methods"></a>Méthodes

|Nom de la méthode|Description|Syntaxe des expressions de requête Visual Basic|Informations complémentaires|
|-----------------|-----------------|------------------------------------------|----------------------|
|OrderBy|Trie les valeurs dans l’ordre croissant.|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|
|OrderByDescending|Trie les valeurs dans l’ordre décroissant.|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|
|ThenBy|Effectue un tri secondaire dans l’ordre croissant.|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|
|ThenByDescending|Effectue un tri secondaire dans l’ordre décroissant.|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|
|Inverser|Inverse l’ordre des éléments dans une collection.|Non applicable.|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-examples"></a>Exemples de syntaxe d'expression de requête

### <a name="primary-sort-examples"></a>Exemples de tri principal

#### <a name="primary-ascending-sort"></a>Tri principal croissant

L’exemple suivant montre comment utiliser la clause `Order By` dans une requête LINQ pour trier les chaînes dans un tableau par longueur de chaîne, dans l’ordre croissant.

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Length
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' fox
' quick
' brown
' jumps
```

#### <a name="primary-descending-sort"></a>Tri principal décroissant

L’exemple suivant montre comment utiliser la clause `Order By Descending` dans une requête LINQ pour trier les chaînes selon leur première lettre, dans l’ordre décroissant.

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Substring(0, 1) Descending
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' quick
' jumps
' fox
' brown
```

### <a name="secondary-sort-examples"></a>Exemples de tri secondaire

#### <a name="secondary-ascending-sort"></a>Tri secondaire croissant

L’exemple suivant montre comment utiliser la clause `Order By` dans une requête LINQ pour effectuer un tri principal et un tri secondaire des chaînes dans un tableau. Les chaînes sont triées en premier lieu selon leur longueur, puis secondairement en fonction de la première lettre de la chaîne, chaque fois dans l’ordre croissant.

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Length, word.Substring(0, 1)
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' fox
' the
' brown
' jumps
' quick
```

#### <a name="secondary-descending-sort"></a>Tri secondaire décroissant

L’exemple suivant montre comment utiliser la clause `Order By Descending` dans une requête LINQ pour effectuer un tri principal dans l’ordre croissant et un tri secondaire dans l’ordre décroissant. Les chaînes sont triées en premier lieu selon leur longueur, puis secondairement en fonction de la première lettre de la chaîne.

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Length, word.Substring(0, 1) Descending
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' fox
' the
' quick
' jumps
' brown
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Linq>
- [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](standard-query-operators-overview.md)
- [Order By (clause)](../../../language-reference/queries/order-by-clause.md)
- [Guide pratique : trier les résultats d’une requête](../../language-features/linq/how-to-sort-query-results-by-using-linq.md)
- [Comment : trier ou filtrer des données texte par mot ou par champ (LINQ) (Visual Basic)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
