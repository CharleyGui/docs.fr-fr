---
title: Opérations d'agrégation
ms.date: 07/20/2015
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
ms.openlocfilehash: 5c7f9344d379af2fed2a8f3d9f7c031c8ca00e8c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345775"
---
# <a name="aggregation-operations-visual-basic"></a>Opérations d’agrégation (Visual Basic)
Une opération d’agrégation calcule une valeur unique à partir d’une collection de valeurs. Par exemple, une opération d'agrégation peut être le calcul de la température quotidienne moyenne à partir des valeurs de température quotidiennes relevées sur un mois.  
  
 L’illustration suivante montre les résultats de deux opérations d’agrégation différentes sur une séquence de nombres. La première opération additionne les nombres. La deuxième opération retourne la valeur maximale dans la séquence.  
  
 ![Illustration qui montre des opérations d’agrégation LINQ.](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 Les méthodes d’opérateurs de requête standard qui effectuent des opérations d’agrégation sont répertoriées dans la section suivante.  
  
## <a name="methods"></a>Méthodes  
  
|Nom de la méthode|Description|Syntaxe des expressions de requête Visual Basic|Informations supplémentaires|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Agrégat|Effectue une opération d’agrégation personnalisée sur les valeurs d’une collection.|Non applicable.|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|Moyenne|Calcule la valeur moyenne d’une collection de valeurs.|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|Nombre|Compte tous les éléments d’une collection, ou uniquement les éléments basés sur une fonction de prédicat.|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|LongCount|Compte tous les éléments d’une grande collection, ou uniquement les éléments basés sur une fonction de prédicat.|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|Max|Détermine la valeur maximale dans une collection.|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|Min|Détermine la valeur minimale dans une collection.|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|Sum|Calcule la somme des valeurs d’une collection.|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Exemples de syntaxe d'expression de requête  
  
### <a name="average"></a>Moyenne  
 L’exemple de code suivant utilise la clause `Aggregate Into Average` dans Visual Basic pour calculer la température moyenne dans un tableau de nombres qui représentent des températures.  
  
 [!code-vb[CsLINQAggregating#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#1)]  
  
### <a name="count"></a>Nombre  
 L’exemple de code suivant utilise la clause `Aggregate Into Count` dans Visual Basic pour compter le nombre de valeurs d’un tableau qui sont supérieures ou égales à 80.  
  
 [!code-vb[CsLINQAggregating#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#2)]  
  
### <a name="longcount"></a>LongCount  
 L’exemple de code suivant utilise la clause `Aggregate Into LongCount` pour compter le nombre de valeurs dans un tableau.  
  
 [!code-vb[CsLINQAggregating#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#3)]  
  
### <a name="max"></a>Max  
 L’exemple de code suivant utilise la clause `Aggregate Into Max` pour calculer la température maximale dans un tableau de nombres qui représentent des températures.  
  
 [!code-vb[CsLINQAggregating#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#4)]  
  
### <a name="min"></a>Min  
 L’exemple de code suivant utilise la clause `Aggregate Into Min` pour calculer la température minimale dans un tableau de nombres qui représentent des températures.  
  
 [!code-vb[CsLINQAggregating#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#5)]  
  
### <a name="sum"></a>Sum  
 L’exemple de code suivant utilise la clause `Aggregate Into Sum` pour calculer le montant total des dépenses à partir d’un tableau de valeurs qui représentent des dépenses.  
  
 [!code-vb[CsLINQAggregating#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#6)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Linq>
- [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Aggregate (clause)](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Comment : calculer des valeurs de colonnes dans un fichier texte CSV (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [Guide pratique : compter, additionner ou faire la moyenne de données](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)
- [Guide pratique : rechercher la valeur minimale ou maximale dans un résultat de requête](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)
- [Comment : interroger les fichiers les plus volumineux dans une arborescence de répertoires (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)
- [Comment : Rechercher le nombre total d’octets dans un ensemble de dossiers (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)
