---
title: Partitionnement des données
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: 34749f9d7b137bade66b6103650871246c3cc532
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406844"
---
# <a name="partitioning-data-visual-basic"></a>Partitionnement des données (Visual Basic)
Le partitionnement dans LINQ désigne l’opération consistant à diviser une séquence d’entrée en deux sections, sans réorganiser les éléments, puis à retourner l’une des sections.  
  
 L’illustration suivante montre les résultats de trois opérations de partitionnement différentes sur une séquence de caractères. La première opération retourne les trois premiers éléments de la séquence. La deuxième opération ignore les trois premiers éléments et retourne les éléments restants. La troisième opération ignore les deux premiers éléments de la séquence et retourne les trois éléments suivants.  
  
 ![Illustration des trois opérations de partitionnement LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 Les méthodes d’opérateurs de requête standard qui partitionnent des séquences sont répertoriées dans la section suivante.  
  
## <a name="operators"></a>Opérateurs  
  
|Nom de l’opérateur|Description|Syntaxe des expressions de requête Visual Basic|Informations complémentaires|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|Ignorer|Ignore les éléments jusqu’à une position spécifiée dans une séquence.|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile|Ignore les éléments basés sur une fonction de prédicat jusqu’à un élément qui ne remplit pas la condition.|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Prend les éléments jusqu’à une position spécifiée dans une séquence.|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|TakeWhile|Prend les éléments basés sur une fonction de prédicat jusqu’à un élément qui ne remplit pas la condition.|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Exemples de syntaxe d'expression de requête  
  
### <a name="skip"></a>Ignorer  
 L’exemple de code suivant utilise la `Skip` clause dans Visual Basic pour ignorer les quatre premières chaînes d’un tableau de chaînes avant de retourner les chaînes restantes dans le tableau.  
  
 [!code-vb[CsLINQPartitioning#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#1)]  
  
### <a name="skipwhile"></a>SkipWhile  
 L’exemple de code suivant utilise la `Skip While` clause dans Visual Basic pour ignorer les chaînes dans un tableau, tandis que la première lettre de la chaîne est « a ». Les chaînes restantes dans le tableau sont retournées.  
  
 [!code-vb[CsLINQPartitioning#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#2)]  
  
### <a name="take"></a>Take  
 L’exemple de code suivant utilise la `Take` clause dans Visual Basic pour retourner les deux premières chaînes dans un tableau de chaînes.  
  
 [!code-vb[CsLINQPartitioning#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#3)]  
  
### <a name="takewhile"></a>TakeWhile  
 L’exemple de code suivant utilise la `Take While` clause dans Visual Basic pour retourner des chaînes à partir d’un tableau, tandis que la longueur de la chaîne est inférieure ou égale à cinq.  
  
 [!code-vb[CsLINQPartitioning#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#4)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Linq>
- [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](standard-query-operators-overview.md)
- [Skip (clause)](../../../language-reference/queries/skip-clause.md)
- [SkipWhile (clause)](../../../language-reference/queries/skip-while-clause.md)
- [Take (clause)](../../../language-reference/queries/take-clause.md)
- [Take While (clause)](../../../language-reference/queries/take-while-clause.md)
