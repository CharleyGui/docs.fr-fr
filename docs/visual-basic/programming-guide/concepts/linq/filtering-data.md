---
title: Filtrage des données (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: 27765247daa2155e685b1cd2bfccebb3216ca672
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582439"
---
# <a name="filtering-data-visual-basic"></a>Filtrage des données (Visual Basic)

Le filtrage fait référence à l’opération de restriction du jeu de résultats pour que celui-ci contienne uniquement les éléments qui répondent à une condition spécifiée. Cette opération est également appelée « sélection ».

L’illustration suivante montre les résultats du filtrage d’une séquence de caractères. Le prédicat de l’opération de filtrage spécifie que le caractère doit être « A ».

![Diagramme illustrant une opération de filtrage LINQ](./media/filtering-data/linq-filter-operation.png)

Les méthodes d’opérateurs de requête standard qui effectuent des opérations de sélection sont répertoriées dans la section suivante.

## <a name="methods"></a>Méthodes

|Nom de la méthode|Description|Syntaxe des expressions de requête Visual Basic|Informations complémentaires|
|-----------------|-----------------|------------------------------------------|----------------------|
|OfType|Sélectionne des valeurs, en fonction de leur capacité à être castées en un type spécifié.|Non applicable.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|Où|Sélectionne les valeurs qui sont basées sur une fonction de prédicat.|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a>Exemple de syntaxe d’expression de requête

L’exemple suivant utilise la `Where` pour filtrer à partir d’un tableau les chaînes qui ont une longueur spécifique.

```vb
Dim words() As String = {"the", "quick", "brown", "fox", "jumps"}

Dim query = From word In words
            Where word.Length = 3
            Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In query
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' fox
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Linq>
- [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Where (clause)](../../../../visual-basic/language-reference/queries/where-clause.md)
- [Guide pratique : filtrer les résultats d’une requête](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)
- [Comment : interroger les métadonnées d’un assembly avec la réflexion (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [Comment : interroger des fichiers ayant un attribut ou un nom spécifié (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [Comment : trier ou filtrer des données texte par mot ou par champ (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
