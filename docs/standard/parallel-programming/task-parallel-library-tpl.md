---
title: Bibliothèque parallèle de tâches
description: Explorez la bibliothèque parallèle de tâches (TPL), un ensemble de types publics et d’API pour simplifier le processus d’ajout du parallélisme & la concurrence aux applications dans .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET, concurrency in
- .NET, parallel programming in
- Parallel Programming
ms.assetid: b8f99f43-9104-45fd-9bff-385a20488a23
ms.openlocfilehash: 596671b267484561a8697546caa5a4764242ebd3
ms.sourcegitcommit: 6d09ae36acba0b0e2ba47999f8f1a725795462a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92925231"
---
# <a name="task-parallel-library-tpl"></a>Bibliothèque parallèle de tâches

La bibliothèque parallèle de tâches est un ensemble de types publics et d’API dans les espaces de noms <xref:System.Threading?displayProperty=nameWithType> et <xref:System.Threading.Tasks?displayProperty=nameWithType>. L'objectif de la bibliothèque parallèle de tâches est d'accroître la productivité des développeurs en simplifiant le processus d'ajout du parallélisme et de l'accès concurrentiel aux applications. La bibliothèque parallèle de tâches met à l'échelle dynamiquement le degré d'accès concurrentiel pour utiliser plus efficacement tous les processeurs disponibles. De plus, la bibliothèque parallèle de tâches gère le partitionnement du travail, la planification de threads sur le <xref:System.Threading.ThreadPool>, la prise en charge de l'annulation, la gestion d'état et d'autres détails de bas niveau. L'utilisation de la bibliothèque parallèle de tâches vous permet de maximiser les performances de votre code tout en vous concentrant sur le travail que votre programme doit accomplir.  
  
 À partir de .NET Framework 4, la bibliothèque parallèle de tâches est la meilleure façon d’écrire du code multithread et parallèle. Toutefois, tout le code n’est pas adapté à la parallélisation. Par exemple, si une boucle exécute uniquement une petite quantité de travail sur chaque itération, ou si elle ne s’exécute pas pour de nombreuses itérations, la surcharge de la parallélisation peut entraîner un ralentissement de l’exécution du code. En outre, comme tout code multithread, la parallélisation rend l'exécution du programme plus complexe. Même si la bibliothèque parallèle de tâches simplifie les scénarios multithread, il est recommandé de connaître les notions fondamentales des concepts de threading, tels que les verrous, les interblocages et les conditions de concurrence critique, afin de pouvoir utiliser efficacement la bibliothèque parallèle de tâches.  
  
## <a name="related-articles"></a>Articles connexes  
  
|Titre|Description|  
|-|-|  
|[Parallélisme des données](data-parallelism-task-parallel-library.md)|Décrit comment créer des boucles parallèles `for` et `foreach` (`For` et `For Each` en Visual Basic).|  
|[Programmation asynchrone basée sur les tâches](task-based-asynchronous-programming.md)|Décrit comment créer et exécuter implicitement des tâches à l’aide de <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> ou explicitement en utilisant des objets <xref:System.Threading.Tasks.Task> directement.|  
|[Dataflow](dataflow-task-parallel-library.md)|Explique comment utiliser les composants de flux de données dans la bibliothèque de flux de données de TPL pour effectuer plusieurs opérations qui doivent communiquer entre elles ou pour traiter les données lorsqu'elles sont disponibles.|
|[Pièges potentiels dans le parallélisme des données et des tâches](potential-pitfalls-in-data-and-task-parallelism.md)|Décrit des pièges courants et la manière de les éviter.|  
|[Parallel LINQ (PLINQ)](introduction-to-plinq.md)|Décrit comment atteindre le parallélisme des données avec les requêtes LINQ.|  
|[Programmation parallèle](index.md)|Nœud de niveau supérieur pour la programmation parallèle .NET.|  
  
## <a name="see-also"></a>Voir aussi

- [Exemples de programmation parallèle avec .NET Core & .NET Standard](/samples/browse/?products=dotnet-core%2Cdotnet-standard&term=parallel)
