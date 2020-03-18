---
title: Bibliothèque parallèle de tâches
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET, concurrency in
- .NET, parallel programming in
- Parallel Programming
ms.assetid: b8f99f43-9104-45fd-9bff-385a20488a23
ms.openlocfilehash: 487fe48462803ac19318f450f2576989f196a9be
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139957"
---
# <a name="task-parallel-library-tpl"></a>Bibliothèque parallèle de tâches
La bibliothèque parallèle de tâches est un ensemble de types publics et d’API dans les espaces de noms <xref:System.Threading?displayProperty=nameWithType> et <xref:System.Threading.Tasks?displayProperty=nameWithType>. L'objectif de la bibliothèque parallèle de tâches est d'accroître la productivité des développeurs en simplifiant le processus d'ajout du parallélisme et de l'accès concurrentiel aux applications. La bibliothèque parallèle de tâches met à l'échelle dynamiquement le degré d'accès concurrentiel pour utiliser plus efficacement tous les processeurs disponibles. De plus, la bibliothèque parallèle de tâches gère le partitionnement du travail, la planification de threads sur le <xref:System.Threading.ThreadPool>, la prise en charge de l'annulation, la gestion d'état et d'autres détails de bas niveau. L'utilisation de la bibliothèque parallèle de tâches vous permet de maximiser les performances de votre code tout en vous concentrant sur le travail que votre programme doit accomplir.  
  
 À compter de .NET Framework 4, la bibliothèque parallèle de tâches est la meilleure méthode pour écrire le code multithread et parallèle. Toutefois, tout le code est pas approprié pour la parallélisation ; par exemple, si une boucle exécute uniquement une petite quantité de travail sur chaque itération ou ne s'exécute que pour un nombre limité d'itérations, la charge mémoire de la parallélisation peut ralentir l'exécution du code. En outre, comme tout code multithread, la parallélisation rend l'exécution du programme plus complexe. Même si la bibliothèque parallèle de tâches simplifie les scénarios multithread, il est recommandé de connaître les notions fondamentales des concepts de threading, tels que les verrous, les interblocages et les conditions de concurrence critique, afin de pouvoir utiliser efficacement la bibliothèque parallèle de tâches.  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Intitulé|Description|  
|-|-|  
|[Parallélisme de données](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|Décrit comment créer des boucles parallèles `for` et `foreach` (`For` et `For Each` en Visual Basic).|  
|[Programmation asynchrone basée sur les tâches](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)|Décrit comment créer et exécuter implicitement des tâches à l’aide de <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> ou explicitement en utilisant des objets <xref:System.Threading.Tasks.Task> directement.|  
|[Flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)|Explique comment utiliser les composants de flux de données dans la bibliothèque de flux de données de TPL pour effectuer plusieurs opérations qui doivent communiquer entre elles ou pour traiter les données lorsqu'elles sont disponibles.|  
|[Utilisation de la bibliothèque parallèle de tâches (TPL) avec d’autres modèles asynchrones](../../../docs/standard/parallel-programming/using-tpl-with-other-asynchronous-patterns.md)|Décrit comment utiliser la bibliothèque parallèle de tâches avec d’autres modèles asynchrones dans .NET.|  
|[Pièges potentiels dans le parallélisme des données et des tâches](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)|Décrit des pièges courants et la manière de les éviter.|  
|[Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|Décrit comment atteindre le parallélisme des données avec les requêtes LINQ.|  
|[Programmation parallèle](../../../docs/standard/parallel-programming/index.md)|Nœud de niveau supérieur pour la programmation parallèle .NET.|  
  
## <a name="see-also"></a>Voir aussi

- [Exemples de programmation parallèle avec .NET Framework](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
