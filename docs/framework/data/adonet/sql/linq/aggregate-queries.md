---
title: Requêtes d'agrégation
ms.date: 03/30/2017
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
ms.openlocfilehash: 8dfe24a84c707b6d21afb7ccfc57ac7b0423942f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161540"
---
# <a name="aggregate-queries"></a>Requêtes d'agrégation

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prend en charge les opérateurs d'agrégation `Average`, `Count`, `Max`, `Min` et `Sum`. Notez les caractéristiques suivantes des opérateurs d'agrégation dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] :  
  
- Les requêtes d'agrégation sont exécutées immédiatement.  
  
     Pour plus d’informations, consultez [Introduction aux requêtes LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
- Les requêtes d’agrégation retournent généralement un nombre au lieu d’une collection.  
  
     Pour plus d’informations, consultez [opérations d’agrégation](/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120)).  
  
- Vous ne pouvez pas appeler d'agrégats à l'aide de types anonymes.  
  
 Les exemples des rubriques suivantes dérivent de l'exemple de base de données Northwind. Pour plus d’informations, consultez [téléchargement d’exemples de bases de données](downloading-sample-databases.md).  
  
## <a name="in-this-section"></a>Dans cette section  

 [Retourner la valeur moyenne d'une séquence numérique](return-the-average-value-from-a-numeric-sequence.md)  
 Montre comment utiliser l'opérateur <xref:System.Linq.Enumerable.Average%2A>.  
  
 [Dénombrer les éléments d'une séquence](count-the-number-of-elements-in-a-sequence.md)  
 Montre comment utiliser l'opérateur <xref:System.Linq.Enumerable.Count%2A>.  
  
 [Comment : rechercher la valeur maximale dans une séquence numérique](find-the-maximum-value-in-a-numeric-sequence.md)  
 Montre comment utiliser l'opérateur <xref:System.Linq.Enumerable.Max%2A>.  
  
 [Comment : rechercher la valeur minimale dans une séquence numérique](find-the-minimum-value-in-a-numeric-sequence.md)  
 Montre comment utiliser l'opérateur <xref:System.Linq.Enumerable.Min%2A>.  
  
 [Comment : calculer la somme de valeurs dans une séquence numérique](compute-the-sum-of-values-in-a-numeric-sequence.md)  
 Montre comment utiliser l'opérateur <xref:System.Linq.Enumerable.Sum%2A>.  
  
## <a name="related-sections"></a>Sections connexes  

 [Exemples de requêtes](query-examples.md)  
 Fournit des liens vers les requêtes [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dans Visual Basic et C#.  
  
 [Concepts relatifs aux requêtes](query-concepts.md)  
 Fournit des liens vers des rubriques qui expliquent les concepts de conception de requêtes LINQ dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .  
  
 [Introduction aux requêtes LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 Explique le fonctionnement des requêtes dans LINQ.
