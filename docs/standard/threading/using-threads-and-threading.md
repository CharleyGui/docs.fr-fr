---
title: Utilisation des threads et du threading
description: En savoir plus sur l’utilisation des threads et du Threading dans .NET, vous pouvez écrire des applications pour effectuer de nombreuses opérations en même temps (multithreading).
ms.date: 08/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
ms.openlocfilehash: 127ea9e28d9ce303270512bf86bf4eecf2f86437
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188703"
---
# <a name="using-threads-and-threading"></a>Utilisation des threads et du threading

Avec .NET, vous pouvez écrire des applications qui effectuent plusieurs opérations en même temps. Les opérations présentant le risque d’accaparer les ressources d’autres opérations peuvent s’exécuter sur des threads distincts : ce processus est appelé *multithreading* ou *threading libre* .  
  
Les applications qui utilisent le multithreading sont plus réactives aux entrées utilisateur, car l’interface utilisateur reste active pendant que les tâches sollicitant beaucoup le processeur s’exécutent sur des threads distincts. Le multithreading est également utile quand vous créez des applications scalables, car vous pouvez ajouter des threads au fil de l’augmentation de la charge de travail.

> [!NOTE]
> Si vous avez besoin de plus de contrôle sur le comportement des threads de l’application, vous pouvez gérer vous-même les threads. Toutefois, la programmation multithread est considérablement simplifiée avec les <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classes et, [Parallel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md), les classes de collection simultanée dans l' <xref:System.Collections.Concurrent?displayProperty=nameWithType> espace de noms et un modèle de programmation basé sur le concept de tâches plutôt que sur les threads. Pour plus d’informations, consultez [Programmation parallèle](../parallel-programming/index.md) et [Bibliothèque parallèle de tâches (TPL)](../parallel-programming/task-parallel-library-tpl.md).

## <a name="how-to-create-and-start-a-new-thread"></a>Comment créer et démarrer un nouveau thread

Pour créer un thread, vous devez créer une instance de la classe <xref:System.Threading.Thread?displayProperty=nameWithType> et fournir au constructeur le nom de la méthode que vous souhaitez exécuter sur un nouveau thread. Pour démarrer un thread créé, appelez la méthode <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>. Pour plus d’informations et pour obtenir des exemples, consultez l’article [Création de threads et passage de données au démarrage](creating-threads-and-passing-data-at-start-time.md) et la référence de l’API <xref:System.Threading.Thread>.

## <a name="how-to-stop-a-thread"></a>Comment arrêter un thread

Pour mettre fin à l’exécution d’un thread, utilisez <xref:System.Threading.CancellationToken?displayProperty=nameWithType> . Il offre un moyen unifié d’arrêter les threads de manière coopérative. Pour plus d’informations, consultez [Annulation dans les threads managés](cancellation-in-managed-threads.md).

Parfois, il n’est pas possible d’arrêter un thread de manière coopérative, car il exécute du code tiers non conçu pour l’annulation coopérative. Dans ce cas, vous souhaiterez peut-être mettre fin à l’exécution de force. Pour mettre fin à l’exécution d’un thread de force, dans .NET Framework vous pouvez utiliser la <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> méthode. Cette méthode lève une <xref:System.Threading.ThreadAbortException> sur le thread sur lequel elle est appelée. Pour plus d’informations, consultez [Destruction de threads](destroying-threads.md). La <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> méthode n’est pas prise en charge dans .net core. Si vous devez mettre fin à l’exécution de code tiers de force dans .NET Core, exécutez-le dans le processus distinct et utilisez <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType> .

Le <xref:System.Threading.CancellationToken?displayProperty=nameWithType> n’est pas disponible avant le .NET Framework 4. Pour arrêter un thread dans les anciennes versions de .NET Framework, implémentez manuellement l’annulation coopérative à l’aide des techniques de synchronisation de threads. Par exemple, vous pouvez créer le champ booléen volatile `shouldStop` et l’utiliser pour demander l’arrêt du code exécuté par le thread. Pour plus d’informations, consultez [volatile](../../csharp/language-reference/keywords/volatile.md) in C# Reference et <xref:System.Threading.Volatile?displayProperty=nameWithType> .

Utilisez la <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> méthode pour que le thread appelant attende la fin du thread en cours d’arrêt.

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
- [Threads et threading](threads-and-threading.md)
- [Programmation parallèle](../parallel-programming/index.md)
