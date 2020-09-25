---
title: Exécution distante et exécution locale
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
ms.openlocfilehash: c99e726902192fc8324e77441b80aa4519c55ddc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91196947"
---
# <a name="remote-vs-local-execution"></a>Exécution distante et exécution locale

Vous pouvez décider d'exécuter vos requêtes à distance (autrement dit, le moteur de base de données exécute la requête sur la base de données) ou localement ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] exécute la requête sur un cache local).  
  
## <a name="remote-execution"></a>Communication à distance  

 Considérez la requête suivante :  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 Si votre base de données contient des milliers de lignes de commandes, vous ne souhaitez pas toutes les récupérer pour traiter un petit sous-ensemble. Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], la classe <xref:System.Data.Linq.EntitySet%601> implémente l'interface <xref:System.Linq.IQueryable>. Cette approche permet de s'assurer que de telles requêtes peuvent être exécutées à distance. Deux avantages majeurs découlent de cette technique :  
  
- Les données inutiles ne sont pas récupérées.  
  
- Une requête exécutée par le moteur de base de données est souvent plus efficace en raison des index de la base de données.  
  
## <a name="local-execution"></a>Exécution locale  

 Dans d'autres situations, vous pouvez souhaiter disposer du jeu complet d'entités connexes dans le cache local. Pour cela, <xref:System.Data.Linq.EntitySet%601> fournit la méthode <xref:System.Data.Linq.EntitySet%601.Load%2A> pour charger explicitement tous les membres de <xref:System.Data.Linq.EntitySet%601>.  
  
 Si un <xref:System.Data.Linq.EntitySet%601> est déjà chargé, les requêtes suivantes sont exécutées localement. Cette approche est utile pour les raisons suivantes :  
  
- Si le jeu complet doit être utilisé localement ou plusieurs fois, vous pouvez éviter des requêtes distantes et des latences associées.  
  
- L'entité peut être sérialisée comme une entité complète.  
  
 Le fragment de code suivant illustre comment obtenir l'exécution locale :  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a>Comparaison  

 Ces deux fonctions fournissent une combinaison puissante d'options : communication à distance pour les grandes collections et exécution locale pour les petites collections ou lorsque la collection complète est nécessaire. Implémentez la communication à distance via <xref:System.Linq.IQueryable> et l'exécution locale sur une collection <xref:System.Collections.Generic.IEnumerable%601> en mémoire. Pour forcer l’exécution locale (autrement dit, <xref:System.Collections.Generic.IEnumerable%601> ), consultez [convertir un type en IEnumerable générique](convert-a-type-to-a-generic-ienumerable.md).  
  
### <a name="queries-against-unordered-sets"></a>Requêtes sur des jeux non ordonnés  

 Notez la différence importante entre une collection locale qui implémente <xref:System.Collections.Generic.List%601> et une collection qui fournit des requêtes distantes exécutées sur des *jeux non ordonnés* dans une base de données relationnelle. Les méthodes <xref:System.Collections.Generic.List%601> telles que celles qui utilisent des valeurs d'index requièrent des sémantiques de liste que l'on ne peut généralement pas obtenir via une requête distante sur un jeu non ordonné. Pour cette raison, de telles méthodes chargent implicitement le <xref:System.Data.Linq.EntitySet%601> pour autoriser l'exécution locale.  
  
## <a name="see-also"></a>Voir aussi

- [Concepts relatifs aux requêtes](query-concepts.md)
