---
title: Éléments fondamentaux du threading managé
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
ms.openlocfilehash: 4d2a96619fd1c48c79b5590efdb52c307d29710c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291004"
---
# <a name="managed-threading-basics"></a>Éléments fondamentaux du threading managé

Les cinq premières rubriques de cette section sont conçues pour vous aider à déterminer quand utiliser le threading managé et pour expliquer des fonctionnalités de base. Pour plus d’informations sur les classes qui fournissent des fonctionnalités supplémentaires, consultez [Fonctionnalités et objets de Threading](threading-objects-and-features.md) et [Vue d’ensemble des Primitives de synchronisation](overview-of-synchronization-primitives.md).  
  
 Le reste des rubriques de cette section traitent des sujets avancés, y compris l’interaction du threading managé avec le système d’exploitation Windows.  
  
> [!NOTE]
> Dans .NET Framework 4, la bibliothèque parallèle de tâches et PLINQ fournissent des API pour le parallélisme des tâches et des données dans les programmes multithreads. Pour plus d’informations, consultez [programmation parallèle](../parallel-programming/index.md).  
  
## <a name="in-this-section"></a>Dans cette section

 [Threads et threads](threads-and-threading.md)  
 Explique les avantages et les inconvénients de plusieurs threads et présente les scénarios dans lesquels vous pouvez créer des threads ou utiliser des threads du pool de threads.  
  
 [Exceptions dans les threads managés](exceptions-in-managed-threads.md)  
 Décrit le comportement des exceptions non prises en charge dans les threads pour différentes versions de .NET Framework, notamment lorsqu’elles entraînent l’arrêt de l’application.  
  
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
 Décrit la bibliothèque parallèle de tâches et PLINQ, qui simplifient considérablement le travail de création d’applications .NET Framework asynchrones et multithreads.
