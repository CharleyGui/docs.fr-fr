---
title: Parallel LINQ (PLINQ)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ, overview
ms.assetid: 3d4d0cd3-bde4-490b-99e7-f4e41be96455
ms.openlocfilehash: 1ea880c6403a5fc8b26ba67fe21dfce79c4683db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140037"
---
# <a name="parallel-linq-plinq"></a>Parallel LINQ (PLINQ)
Parallel LINQ (PLINQ) est une implémentation parallèle de LINQ to Objects. PLINQ implémente le jeu complet d’opérateurs de requête standard LINQ comme méthodes d’extension pour l’espace de noms <xref:System.Linq> et inclut des opérateurs supplémentaires pour les opérations parallèles. PLINQ combine la simplicité et la lisibilité de la syntaxe LINQ à la puissance de la programmation parallèle. Comme le code qui cible la bibliothèque parallèle de tâches, les requêtes PLINQ sont mises à l’échelle dans le degré de concurrence basé sur les fonctionnalités de l’ordinateur hôte.  
  
 Dans de nombreux scénarios, PLINQ peut considérablement augmenter la vitesse des requêtes LINQ to Objects en utilisant plus efficacement tous les cœurs disponibles sur l’ordinateur hôte. Ces performances accrues apportent une puissance informatique hautes performances sur le Bureau.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Introduction à PLINQ](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
  
 [Fonctionnement de l'accélération dans PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)  
  
 [Conservation de l'ordre en PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)  
  
 [Options de fusion en PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)  
  
 [Comment : créer et exécuter une requête PLINQ simple](../../../docs/standard/parallel-programming/how-to-create-and-execute-a-simple-plinq-query.md)  
  
 [Comment : contrôler l'ordre dans une requête PLINQ](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)  
  
 [Comment : combiner des requêtes LINQ parallèles et séquentielles](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md)  
  
 [Comment : gérer des exceptions dans une requête PLINQ](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)  
  
 [Comment : annuler une requête PLINQ](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)  
  
 [Comment : écrire une fonction d'agrégation PLINQ personnalisée](../../../docs/standard/parallel-programming/how-to-write-a-custom-plinq-aggregate-function.md)  
  
 [Comment : spécifier le mode d'exécution en PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)  
  
 [Comment : spécifier des options de fusion en PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)  
  
 [Comment : itérer les répertoires de fichiers avec PLINQ](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)  
  
 [Comment : mesurer les performances de requêtes PLINQ](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)  
  
 [Données PLINQ, exemple](../../../docs/standard/parallel-programming/plinq-data-sample.md)  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Linq.ParallelEnumerable>
- [Programmation parallèle](../../../docs/standard/parallel-programming/index.md)
- [LINQ (Language-Integrated Query) - C#](../../csharp/programming-guide/concepts/linq/index.md)  
- [LINQ (Language-Integrated Query) - Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md)  
