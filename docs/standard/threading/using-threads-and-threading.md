---
title: Utilisation des threads et du threading
ms.date: 08/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
ms.openlocfilehash: 14159ff9a6ca39108aec14b0ad46004e95fa3cf2
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588427"
---
# <a name="using-threads-and-threading"></a>Utilisation des threads et du threading

Avec .NET, vous pouvez écrire des applications qui effectuent plusieurs opérations en même temps. Les opérations présentant le risque d’accaparer les ressources d’autres opérations peuvent s’exécuter sur des threads distincts : ce processus est appelé *multithreading* ou *threading libre*.  
  
Les applications qui utilisent le multithreading sont plus réactives aux entrées utilisateur, car l’interface utilisateur reste active pendant que les tâches sollicitant beaucoup le processeur s’exécutent sur des threads distincts. Le multithreading est également utile quand vous créez des applications scalables, car vous pouvez ajouter des threads au fil de l’augmentation de la charge de travail.

> [!NOTE]
> Si vous avez besoin de plus de contrôle sur le comportement des threads de l’application, vous pouvez gérer vous-même les threads. Toutefois, à compter de .NET Framework 4, la programmation multithread est considérablement simplifiée avec les classes <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, [Parallel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md), de nouvelles classes de collections simultanées dans l’espace de noms <xref:System.Collections.Concurrent?displayProperty=nameWithType>, et un nouveau modèle de programmation basé sur le concept de tâches plutôt que de threads. Pour plus d’informations, consultez [Programmation parallèle](../parallel-programming/index.md) et [Bibliothèque parallèle de tâches (TPL)](../parallel-programming/task-parallel-library-tpl.md).

## <a name="how-to-create-and-start-a-new-thread"></a>Comment créer et démarrer un nouveau thread

Pour créer un thread, vous devez créer une instance de la classe <xref:System.Threading.Thread?displayProperty=nameWithType> et fournir au constructeur le nom de la méthode que vous souhaitez exécuter sur un nouveau thread. Pour démarrer un thread créé, appelez la méthode <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>. Pour plus d’informations et pour obtenir des exemples, consultez l’article [Création de threads et passage de données au démarrage](creating-threads-and-passing-data-at-start-time.md) et la référence de l’API <xref:System.Threading.Thread>.

## <a name="how-to-stop-a-thread"></a>Comment arrêter un thread

Pour mettre fin à l’exécution d’un thread, utilisez le <xref:System.Threading.CancellationToken?displayProperty=nameWithType>. Il fournit un moyen unifié d’arrêter les fils en coopération. Pour plus d’informations, consultez [Annulation dans les threads managés](cancellation-in-managed-threads.md).

Parfois, il n’est pas possible d’arrêter un thread en coopération, car il exécute un code tiers non conçu pour l’annulation coopérative. Dans ce cas, vous voudrez peut-être mettre fin à son exécution de force. Pour mettre fin à l’exécution d’un thread <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> de force, dans .NET Framework vous pouvez utiliser la méthode. Cette méthode lève une <xref:System.Threading.ThreadAbortException> sur le thread sur lequel elle est appelée. Pour plus d’informations, consultez [Destruction de threads](destroying-threads.md). La <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> méthode n’est pas prise en charge dans .NET Core. Si vous avez besoin de mettre fin à l’exécution du code tiers <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>de force dans .NET Core, l’exécuter dans le processus séparé et l’utiliser .

Le <xref:System.Threading.CancellationToken?displayProperty=nameWithType> n’est pas disponible avant .NET Framework 4. Pour arrêter un thread dans les anciennes versions .NET Framework, vous devez implémenter l’annulation coopérative manuellement en utilisant les techniques de synchronisation des threads. Par exemple, vous pouvez créer `shouldStop` le champ boolean volatil et l’utiliser pour demander le code exécuté par le thread pour s’arrêter. Pour plus d’informations, voir <xref:System.Threading.Volatile?displayProperty=nameWithType> [volatile](../../csharp/language-reference/keywords/volatile.md) dans C Référence et .

Utilisez <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> la méthode pour faire attendre le fil d’appel pour la fin du fil arrêté.

## <a name="how-to-pause-or-interrupt-a-thread"></a>Comment suspendre ou interrompre un thread

Vous utilisez la méthode <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> pour suspendre le thread actif pendant un certain laps de temps. Vous pouvez interrompre un thread bloqué en appelant la méthode <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>. Pour plus d’informations, consultez [Suspension et interruption de threads](pausing-and-resuming-threads.md).

## <a name="thread-properties"></a>Propriétés du thread

Le tableau suivant présente certaines des propriétés de <xref:System.Threading.Thread> :  
  
|Propriété|Description|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|Retourne `true` si un thread a été démarré et ne s’est pas encore arrêté normalement ou n’a pas été abandonné.|  
|<xref:System.Threading.Thread.IsBackground%2A>|Obtient ou définit une valeur booléenne qui indique si un thread est un thread d’arrière-plan. Les threads d’arrière-plan ressemblent aux threads de premier plan, mais un thread d’arrière-plan n’empêche pas un processus de s’arrêter. Une fois que tous les threads de premier plan appartenant à un processus sont arrêtés, le common language runtime met fin au processus en appelant la méthode <xref:System.Threading.Thread.Abort%2A> sur les threads d’arrière-plan encore actifs. Pour plus d’informations, consultez [Threads de premier plan et d’arrière-plan](foreground-and-background-threads.md).|  
|<xref:System.Threading.Thread.Name%2A>|Obtient ou définit le nom d’un thread. Généralement utilisé pour découvrir des threads individuels lors du débogage.|  
|<xref:System.Threading.Thread.Priority%2A>|Obtient ou définit une valeur <xref:System.Threading.ThreadPriority> utilisée par le système d’exploitation pour classer par priorité la planification des threads. Pour plus d’informations, consultez [Planification des threads](scheduling-threads.md) et la référence de <xref:System.Threading.ThreadPriority>.|  
|<xref:System.Threading.Thread.ThreadState%2A>|Obtient une valeur <xref:System.Threading.ThreadState> contenant les états actuels d’un thread.|  

## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Thread?displayProperty=nameWithType>
- [Fils et threading](threads-and-threading.md)
- [Programmation parallèle](../parallel-programming/index.md)
