---
title: Opérations ensemblistes
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: b6ff14794343ae7623ee38894cef02cfc0a2a597
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406818"
---
# <a name="set-operations-visual-basic"></a>Opérations de définition (Visual Basic)

Les opérations ensemblistes dans LINQ font référence à des opérations de requête qui génèrent un jeu de résultats basé sur la présence ou l’absence d’éléments équivalents dans la même collection (ou le même ensemble) ou dans une collection distincte (ou un ensemble distinct).

Les méthodes d’opérateur de requête standard qui effectuent des opérations ensemblistes sont répertoriées dans la section suivante.

## <a name="methods"></a>Méthodes

|Nom de la méthode|Description|Syntaxe des expressions de requête Visual Basic|Informations complémentaires|
|-----------------|-----------------|------------------------------------------|----------------------|
|Distinct|Supprime les valeurs en double d’une collection.|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|
|Except|Retourne la différence ensembliste, à savoir les éléments d’une collection qui n’apparaissent pas dans une seconde collection.|Non applicable.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|
|Intersect|Retourne l’intersection ensembliste, à savoir les éléments qui apparaissent dans chacune des deux collections.|Non applicable.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|
|Union|Retourne l’union ensembliste, à savoir les éléments uniques qui apparaissent dans l’une ou l’autre des deux collections.|Non applicable.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|

## <a name="comparison-of-set-operations"></a>Comparaison d’opérations ensemblistes

### <a name="distinct"></a>Distinct

L’illustration suivante représente le comportement de la méthode <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> sur une séquence de caractères. La séquence retournée contient les éléments uniques de la séquence d’entrée.

![Graphique illustrant le comportement de Distinct&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)

### <a name="except"></a>Except

L’illustration suivante représente le comportement de <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>. La séquence retournée contient uniquement les éléments de la première séquence d’entrée qui ne figurent pas dans la seconde séquence d’entrée.

![Graphique présentant l’action de, à l’exception de&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Montre le comportement de except.")

### <a name="intersect"></a>Intersect

L’illustration suivante représente le comportement de <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>. La séquence retournée contient les éléments qui sont communs aux deux séquences d’entrée.

![Graphique illustrant l’intersection de deux séquences.](./media/set-operations/intersection-two-sequences.png)

### <a name="union"></a>Union

L’illustration suivante représente une opération d’union sur deux séquences de caractères. La séquence retournée contient les éléments uniques des deux séquences d’entrée.

![Graphique illustrant l’union de deux séquences.](./media/set-operations/union-operation-two-sequences.png)

## <a name="query-expression-syntax-example"></a>Exemple de syntaxe d’expression de requête

L’exemple suivant utilise la `Distinct` clause dans une requête LINQ pour retourner les nombres uniques d’une liste d’entiers.

[!code-vb[CsLINQSetOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQSetOps/VB/setops.vb#1)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Linq>
- [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](standard-query-operators-overview.md)
- [Distinct (clause)](../../../language-reference/queries/distinct-clause.md)
- [Comment : combiner et comparer des collections de chaînes (LINQ) (Visual Basic)](how-to-combine-and-compare-string-collections-linq.md)
- [Comment : Rechercher la différence définie entre deux listes (LINQ) (Visual Basic)](how-to-find-the-set-difference-between-two-lists-linq.md)
