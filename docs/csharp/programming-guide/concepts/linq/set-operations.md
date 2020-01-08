---
title: Opérations ensemblistes (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: 170316b36705eaed51a9a17f8f79333a29e8c315
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346511"
---
# <a name="set-operations-c"></a>Opérations ensemblistes (C#)
Les opérations ensemblistes dans LINQ font référence à des opérations de requête qui génèrent un jeu de résultats basé sur la présence ou l’absence d’éléments équivalents dans la même collection (ou le même ensemble) ou dans une collection distincte (ou un ensemble distinct).  
  
 Les méthodes d’opérateur de requête standard qui effectuent des opérations ensemblistes sont répertoriées dans la section suivante.  
  
## <a name="methods"></a>Méthodes  
  
|Nom de la méthode|Description|Syntaxe d'expression de requête C#|Plus d’informations|  
|-----------------|-----------------|---------------------------------|----------------------|  
|distinct|Supprime les valeurs en double d’une collection.|Non applicable.|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|À l'exception|Retourne la différence ensembliste, à savoir les éléments d’une collection qui n’apparaissent pas dans une seconde collection.|Non applicable.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|Définir une intersection|Retourne l’intersection ensembliste, à savoir les éléments qui apparaissent dans chacune des deux collections.|Non applicable.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|Union|Retourne l’union ensembliste, à savoir les éléments uniques qui apparaissent dans l’une ou l’autre des deux collections.|Non applicable.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a>Comparaison d’opérations ensemblistes  
  
### <a name="distinct"></a>distinct  
 L’exemple suivant illustre le comportement de la méthode <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> sur une séquence de caractères. La séquence retournée contient les éléments uniques de la séquence d’entrée.  
  
 ![Graphique illustrant le comportement de Distinct&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)  
 
 [!code-csharp-interactive[Distinct](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#1)]
  
### <a name="except"></a>À l'exception  
 L’exemple suivant illustre le comportement de <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>. La séquence retournée contient uniquement les éléments de la première séquence d’entrée qui ne figurent pas dans la seconde séquence d’entrée.  
  
 ![Graphique présentant l’action de Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Montre le comportement de except.")  
  
[!code-csharp-interactive[Except](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#2)]

### <a name="intersect"></a>Définir une intersection  
 L’exemple suivant illustre le comportement de <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>. La séquence retournée contient les éléments qui sont communs aux deux séquences d’entrée.  
  
 ![Graphique illustrant l’intersection de deux séquences.](./media/set-operations/intersection-two-sequences.png)  
 
[!code-csharp-interactive[Intersect](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#3)]

### <a name="union"></a>Union  
 L’exemple suivant illustre une opération d’Union sur deux séquences de caractères. La séquence retournée contient les éléments uniques des deux séquences d’entrée.  
  
 ![Graphique illustrant l’union de deux séquences.](./media/set-operations/union-operation-two-sequences.png)  

[!code-csharp-interactive[Union](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#4)]
 
## <a name="see-also"></a>Voir aussi

- <xref:System.Linq>
- [Vue d’ensemble des opérateurs de requête standard (C#)](./standard-query-operators-overview.md)
- [Comment combiner et comparer des collections de chaînes (LINQ)C#()](./how-to-combine-and-compare-string-collections-linq.md)
- [Comment rechercher la différence définie entre deux listes (LINQ) (C#)](./how-to-find-the-set-difference-between-two-lists-linq.md)
