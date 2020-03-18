---
title: Programmation parallèle en .NET
ms.date: 09/12/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
ms.openlocfilehash: ae129ef0cb2b331c1eb0220282f21fec6f6fb77d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73134144"
---
# <a name="parallel-programming-in-net"></a>Programmation parallèle en .NET

De nombreux ordinateurs personnels et stations de travail ont plusieurs cœurs de processeur qui permettent à plusieurs threads de s’exécuter simultanément. Pour tirer parti du matériel, vous pouvez paralléliser votre code pour distribuer le travail sur plusieurs processeurs.

Dans le passé, la parallélisation nécessitait un niveau peu élevé de manipulation de threads et de verrous. Visual Studio et le .NET Framework améliorent la prise en charge de la programmation parallèle en fournissant une exécution, des types de bibliothèques de classes et des outils de diagnostics. Ces fonctionnalités, qui ont été introduites avec le .NET Framework 4, simplifient le développement parallèle. Vous pouvez écrire du code parallèle efficace, à grains fins et évolutif dans un idiome naturel sans devoir utiliser directement des threads ou le pool de threads.

L’illustration suivante fournit une vue d’ensemble générale de l’architecture de programmation parallèle dans le .NET Framework :

![Architecture de programmation parallèle du .NET](./media/tpl-architecture.png)

## <a name="related-topics"></a>Rubriques connexes

|Technology|Description|
|----------------|-----------------|
|[Bibliothèque parallèle de tâches](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Fournit la documentation pour la classe <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>, qui inclut des versions parallèles de `For` et des boucles `ForEach`, et également pour la classe <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, qui représente la meilleure façon d'exprimer des opérations asynchrones.|
|[Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|Implémentation parallèle de LINQ to Objects qui améliore de manière significative la performance dans de nombreux scénarios.|
|[Structures de données pour la programmation parallèle](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)|Fournit des liens vers la documentation pour les classes de collection thread-safe, les types de synchronisation légers et les types pour l’initialisation tardive.|
|[Outils de diagnostic parallèles](../../../docs/standard/parallel-programming/parallel-diagnostic-tools.md)|Fournit des liens vers la documentation relative aux fenêtres du débogueur Visual Studio pour les tâches et les piles parallèles, et au [Visualiseur concurrentiel](/visualstudio/profiling/concurrency-visualizer).|
|[Partitionneurs personnalisés pour PLINQ et la bibliothèque parallèle de tâches (TPL)](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)|Décrit le fonctionnement des partitionneurs et comment configurer les partitionneurs par défaut ou en créer.|
|[Planificateurs de tâches](xref:System.Threading.Tasks.TaskScheduler)|Décrit le fonctionnement des planificateurs et comment les planificateurs par défaut peuvent être configurés.|
|[Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)|Fournit une vue d’ensemble d’expressions lambda en C#  et Visual Basic, et affiche comment elles sont utilisées dans PLINQ et la bibliothèque parallèle de tâches.|
|[Pour une lecture plus approfondie](../../../docs/standard/parallel-programming/for-further-reading-parallel-programming.md)|Fournit des liens vers des informations supplémentaires et des exemples de ressources pour la programmation parallèle dans .NET.|

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble asynchrone](../async.md)
- [Threading managé](../threading/index.md)
