---
title: Éléments fondamentaux du threading managé
description: Consultez les liens vers d’autres articles sur le Threading géré, couvrant des sujets tels que les exceptions, la synchronisation des données, le premier plan & les threads d’arrière-plan, le stockage local et bien plus encore.
ms.date: 03/30/2017
helpviewer_keywords:
- multiple threads
- threading [.NET], multiple threads
- threading [.NET], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
ms.openlocfilehash: 16785b1c21c5810e55429f6756dcf591c90d8499
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94819667"
---
# <a name="managed-threading-basics"></a>Éléments fondamentaux du threading managé

Les cinq premiers Articles de cette section sont conçus pour vous aider à déterminer quand utiliser le threading managé et à expliquer certaines fonctionnalités de base. Pour plus d’informations sur les classes qui fournissent des fonctionnalités supplémentaires, consultez [Fonctionnalités et objets de Threading](threading-objects-and-features.md) et [Vue d’ensemble des Primitives de synchronisation](overview-of-synchronization-primitives.md).  
  
 Les autres Articles de cette section traitent des sujets avancés, y compris l’interaction du threading managé avec le système d’exploitation Windows.  
  
> [!NOTE]
> À partir de .NET Framework 4, la bibliothèque parallèle de tâches et PLINQ fournissent des API pour le parallélisme des tâches et des données dans les programmes multithread. Pour plus d’informations, consultez [programmation parallèle](../parallel-programming/index.md).  
  
## <a name="in-this-section"></a>Dans cette section

 [Threads et threading](threads-and-threading.md)  
 Explique les avantages et les inconvénients de plusieurs threads et présente les scénarios dans lesquels vous pouvez créer des threads ou utiliser des threads du pool de threads.  
  
 [Exceptions dans les threads managés](exceptions-in-managed-threads.md)  
 Décrit le comportement des exceptions non gérées dans les threads pour les différentes versions de .NET, en particulier dans les situations où elles entraînent l’arrêt de l’application.  
  
 [Synchronisation des données pour le multithreading](synchronizing-data-for-multithreading.md)  
 Décrit les stratégies de synchronisation des données dans des classes qui seront utilisées avec plusieurs threads.  
  
 [Threads de premier plan et d'arrière-plan](foreground-and-background-threads.md)  
 Explique les différences entre les threads de premier plan et d’arrière-plan.  
  
 [Threading managé et non managé dans Windows](managed-and-unmanaged-threading-in-windows.md)  
 Décrit la relation entre le threading managé et non managé, répertorie les équivalents managés de l’API de threading Windows et explique l’interaction des cloisonnements COM et des threads managés.  
  
 [Stockage local des threads : champs static et emplacements de données relatifs à un thread](thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 Décrit les mécanismes de stockage relatifs aux threads.  
  
## <a name="reference"></a>Référence

 <xref:System.Threading.Thread>  
 Fournit la documentation de référence pour la classe **Thread** qui représente un thread managé, qu’elle provienne de code non managé ou qu’elle ait été créée dans une application managée.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Fournit un moyen sûr d’implémenter le multithreading conjointement avec des objets d’interface utilisateur.  
  
## <a name="related-sections"></a>Sections connexes

 [Vue d’ensemble des primitives de synchronisation](overview-of-synchronization-primitives.md)  
 Décrit les classes managées utilisées pour synchroniser les activités de plusieurs threads.  
  
 [Meilleures pratiques pour le threading managé](managed-threading-best-practices.md)  
 Décrit les problèmes courants avec le multithreading et les stratégies pour les éviter.  
  
 [Programmation parallèle](../parallel-programming/index.md)  
 Décrit la bibliothèque parallèle de tâches et PLINQ, qui simplifient de façon considérable le travail de création d’applications .NET asynchrones et multithread.
