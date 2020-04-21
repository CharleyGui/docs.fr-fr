---
title: Vue d’ensemble des primitives de synchronisation
description: En savoir plus sur les primitives de synchronisation de thread .NET utilisées pour synchroniser l’accès à une ressource partagée ou contrôler l’interaction des threads
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET],synchronizing threads
- managed threading
ms.assetid: b782bcb8-da6a-4c6a-805f-2eb46d504309
ms.openlocfilehash: 7347c9b40f150febc6a163ae3aa3267123ea0e9d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739372"
---
# <a name="overview-of-synchronization-primitives"></a>Vue d’ensemble des primitives de synchronisation

.NET fournit un éventail de types que vous pouvez utiliser pour synchroniser l’accès à une ressource partagée ou coordonner l’interaction des threads.

> [!IMPORTANT]
> Utilisez la même instance de primitives de synchronisation pour protéger l’accès à une ressource partagée. Si vous utilisez différentes instances de primitives de synchronisation pour protéger la même ressource, vous contournerez la protection fournie par une primitive de synchronisation.

## <a name="waithandle-class-and-lightweight-synchronization-types"></a>Classe WaitHandle et types de synchronisation légers

Plusieurs primitives de synchronisation .NET dérivent la classe <xref:System.Threading.WaitHandle?displayProperty=nameWithType>, qui encapsule un descripteur de synchronisation du système d’exploitation natif et utilise un mécanisme de signalisation pour l’interaction des threads. Ces classes incluent :

- <xref:System.Threading.Mutex?displayProperty=nameWithType>, qui accorde un accès exclusif à une ressource partagée. L’état d’un mutex est signalé si aucun thread ne le possède.
- <xref:System.Threading.Semaphore?displayProperty=nameWithType>, qui limite le nombre de threads qui peuvent accéder simultanément à une ressource partagée ou à un pool de ressources. L’état d’un sémaphore est défini sur « signalé » quand son nombre est supérieur à zéro et sur « non signalé » quand son nombre est égal à zéro.
- <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>, qui représente un événement de synchronisation de thread et peut être dans un état signalé ou non signalé.
- <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType>, qui est dérivé de <xref:System.Threading.EventWaitHandle> et, quand il est signalé, se réinitialise automatiquement à un état non signalé après avoir libéré un seul thread en attente.
- <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>, qui est dérivé à son <xref:System.Threading.EventWaitHandle> et, quand il est signalé, reste dans un état signalé jusqu'à ce que la méthode <xref:System.Threading.EventWaitHandle.Reset%2A> soit appelée.

Dans .NET Framework, comme <xref:System.Threading.WaitHandle> est dérivé de <xref:System.MarshalByRefObject?displayProperty=nameWithType>, ces types peuvent être utilisés pour synchroniser les activités des threads au-delà des limites des domaines d’application.

Dans .NET Framework et .NET Core, certains de ces types peuvent représenter des descripteurs de synchronisation système nommés, qui sont visibles dans tout le système d’exploitation et peuvent être utilisés pour la synchronisation entre les processus suivants :

- <xref:System.Threading.Mutex> (.NET Framework et .NET Core),
- <xref:System.Threading.Semaphore> (.NET Framework et .NET Core sur Windows),
- <xref:System.Threading.EventWaitHandle> (.NET Framework et .NET Core sur Windows).

Pour plus d'informations, consultez la référence d’API <xref:System.Threading.WaitHandle>.

Les types de synchronisation légers ne s’appuient pas sur les descripteurs de système d’exploitation sous-jacents et fournissent généralement de meilleures performances. Toutefois, ils ne peuvent pas être utilisés pour la synchronisation entre processus. Utilisez ces types pour la synchronisation de threads dans une même application.

Certains de ces types sont des alternatives aux types dérivés de <xref:System.Threading.WaitHandle>. Par exemple, <xref:System.Threading.SemaphoreSlim> est une alternative légère à <xref:System.Threading.Semaphore>.

## <a name="synchronization-of-access-to-a-shared-resource"></a>Synchronisation de l'accès à une ressource partagée

.NET fournit une plage de primitives de synchronisation pour contrôler l’accès à une ressource partagée par plusieurs threads.

### <a name="monitor-class"></a>Monitor (classe)

La classe <xref:System.Threading.Monitor?displayProperty=nameWithType> accorde l’accès mutuellement exclusif à une ressource partagée par l’acquisition ou la libération d’un verrou sur l’objet qui identifie la ressource. Tant qu’un verrou est maintenu, le thread qui contient le verrou peut à nouveau obtenir et libérer le verrou. Tout autre thread se voit bloquer l’acquisition du verrou et la méthode <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> attend que ce dernier soit libéré. La méthode <xref:System.Threading.Monitor.Enter%2A> acquiert un verrou libéré. Vous pouvez également utiliser la méthode <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> pour spécifier la quantité de temps pendant lequel un thread tente d’acquérir un verrou. Étant donné que la classe <xref:System.Threading.Monitor> possède l’affinité de thread, le thread qui a acquis un verrou doit le libérer en appelant la méthode <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>.

Vous pouvez coordonner l’interaction des threads qui acquièrent un verrou sur le même objet à l’aide des méthodes <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> et <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType>.

Pour plus d'informations, consultez la référence d’API <xref:System.Threading.Monitor>.

> [!NOTE]
> Utilisez l’instruction [lock](../../csharp/language-reference/keywords/lock-statement.md) dans C# et l’instruction [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) dans Visual Basic pour synchroniser l’accès à une ressource partagée au lieu d’utiliser la classe <xref:System.Threading.Monitor> directement. Ces instructions sont implémentées à l’aide des méthodes <xref:System.Threading.Monitor.Enter%2A> et <xref:System.Threading.Monitor.Exit%2A> et d’un bloc `try…finally` pour garantir que le verrou acquis est toujours libéré.

### <a name="mutex-class"></a>Mutex (classe)

La classe <xref:System.Threading.Mutex?displayProperty=nameWithType>, telle que <xref:System.Threading.Monitor>, accorde un accès exclusif à une ressource partagée. Utilisez une des surcharges de méthode [Mutex.WaitOne](<xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>) pour demander la propriété d’un mutex. Comme <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> possède l’affinité de thread et le thread qui a acquis un mutex doit le libérer en appelant la méthode <xref:System.Threading.Mutex.ReleaseMutex%2A?displayProperty=nameWithType>.

Contrairement à <xref:System.Threading.Monitor>, la classe <xref:System.Threading.Mutex> peut être utilisée pour la synchronisation entre processus. Pour ce faire, utilisez un mutex nommé, qui est visible dans tout le système d’exploitation. Pour créer une instance de mutex nommé, utilisez un [constructeur de mutex](<xref:System.Threading.Mutex.%23ctor%2A>) qui spécifie un nom. Vous pouvez également <xref:System.Threading.Mutex.OpenExisting%2A?displayProperty=nameWithType> appeler la méthode pour ouvrir un système existant appelé mutex.
  
Pour plus d’informations, consultez l’article [Mutex](mutexes.md) et la référence d’API <xref:System.Threading.Mutex>.

### <a name="spinlock-structure"></a>Structure SpinLock

La structure <xref:System.Threading.SpinLock?displayProperty=nameWithType>, comme <xref:System.Threading.Monitor>, accorde un accès exclusif à une ressource partagée, basée sur la disponibilité d’un verrou. Lorsque <xref:System.Threading.SpinLock> tente d’acquérir un verrou qui n’est pas disponible, il est conservé dans une boucle et effectue des vérifications à plusieurs reprises jusqu'à ce que le verrou devienne disponible.

Pour plus d’informations sur les avantages et les inconvénients de l’utilisation de verrou de rotation, consultez l’article [SpinLock](spinlock.md) et la référence d’API <xref:System.Threading.SpinLock>.

### <a name="readerwriterlockslim-class"></a>Classe ReaderWriterLockSlim

La classe <xref:System.Threading.ReaderWriterLockSlim?displayProperty=nameWithType> accorde un accès exclusif à une ressource partagée pour l’écriture et permet à plusieurs threads d’accéder à la ressource simultanément pour la lecture. Vous souhaiterez peut-être utiliser <xref:System.Threading.ReaderWriterLockSlim> pour synchroniser l’accès à une structure de données partagée qui prend en charge les opérations de lecture thread-safe, mais nécessite un accès exclusif pour effectuer l’opération d’écriture. Quand un thread demande un accès exclusif (par exemple, en appelant la méthode <xref:System.Threading.ReaderWriterLockSlim.EnterWriteLock%2A?displayProperty=nameWithType>), les demandes suivantes des lecteurs et enregistreurs sont bloquées jusqu’à ce que tous les lecteurs existants aient quitté le verrou et que l’enregistreur soit entré et sorti du verrou.
  
Pour plus d'informations, consultez la référence d’API <xref:System.Threading.ReaderWriterLockSlim>.

### <a name="semaphore-and-semaphoreslim-classes"></a>Classes Sémaphore et SemaphoreSlim

Les classes <xref:System.Threading.Semaphore?displayProperty=nameWithType> et <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> limitent le nombre de threads pouvant accéder simultanément à une ressource partagée ou à un pool de ressources. Les autres threads qui demandent la ressource attendent qu’un thread libère le sémaphore. Étant donné que le sémaphore n’a pas d’affinité de thread, un thread peut acquérir le sémaphore et un autre peut le libérer.

<xref:System.Threading.SemaphoreSlim> est une alternative légère à <xref:System.Threading.Semaphore> et ne peut être utilisé que pour la synchronisation dans une limite de processus unique.

Sur Windows, vous pouvez utiliser <xref:System.Threading.Semaphore> pour la synchronisation entre processus. Pour ce faire, créez une instance <xref:System.Threading.Semaphore> qui représente un sémaphore système nommé à l’aide d’un des [constructeurs de sémaphores](<xref:System.Threading.Semaphore.%23ctor%2A>) qui spécifient un nom ou de la méthode <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType>. <xref:System.Threading.SemaphoreSlim> ne prend pas en charge les sémaphores système nommés.

Pour plus d’informations, consultez l’article [Sémaphore et SemaphoreSlim](semaphore-and-semaphoreslim.md) et la référence d’API <xref:System.Threading.Semaphore> ou <xref:System.Threading.SemaphoreSlim>.

## <a name="thread-interaction-or-signaling"></a>Interaction des threads ou signalisation

Interaction des threads (ou signalisation des threads) signifie qu’un thread doit attendre la notification ou un signal d’un ou de plusieurs threads pour pouvoir continuer. Par exemple, si le thread A appelle la méthode <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> du thread B, le thread A est bloqué jusqu'à ce que le thread B soit terminé. Les primitives de synchronisation décrites dans la section précédente fournissent un mécanisme différent pour la signalisation : en libérant un verrou, un thread indique à un autre thread qu’il peut poursuivre en acquérant le verrou.

Cette section décrit des constructions de signalisation supplémentaires fournies par .NET.

### <a name="eventwaithandle-autoresetevent-manualresetevent-and-manualreseteventslim-classes"></a>Classes EventWaitHandle, AutoResetEvent, ManualResetEvent et ManualResetEventSlim

La classe <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> représente un événement de synchronisation de threads.

Un événement de synchronisation peut être dans un état non signalé ou signalé. Lorsque l’état d’un événement est non signalé, un thread qui appelle la surcharge <xref:System.Threading.WaitHandle.WaitOne%2A?> de l’événement est bloqué jusqu'à ce qu’un événement soit signalé. La méthode <xref:System.Threading.EventWaitHandle.Set%2A?displayProperty=nameWithType> définit l’état d’un événement sur « signalé ».

Le comportement d’un <xref:System.Threading.EventWaitHandle> qui a été signalé dépend de son mode de réinitialisation :

- Un <xref:System.Threading.EventWaitHandle> créé avec l’indicateur <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> se réinitialise automatiquement après avoir libéré un seul thread en attente. C'est comme un tourniquet qui ne laisse passer qu'un seul thread à chaque fois qu'il est signalé. La classe <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType>, qui est dérivée de <xref:System.Threading.EventWaitHandle>, représente ce comportement.
- Un <xref:System.Threading.EventWaitHandle> créé avec l’indicateur <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> reste signalé jusqu'à ce que la méthode <xref:System.Threading.EventWaitHandle.Reset%2A> soit appelée. C’est comme une barrière qui reste fermée jusqu'au signalement, puis ouverte jusqu'à ce que quelqu'un la ferme. La classe <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>, qui est dérivée de <xref:System.Threading.EventWaitHandle>, représente ce comportement. La classe <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> est une alternative légère à <xref:System.Threading.ManualResetEvent>.

Sur Windows, vous pouvez utiliser <xref:System.Threading.EventWaitHandle> pour la synchronisation entre processus. Pour ce faire, créez une instance <xref:System.Threading.EventWaitHandle> qui représente un événement de synchronisation système nommé à l’aide d’un des [constructeurs EventWaitHandle](<xref:System.Threading.EventWaitHandle.%23ctor%2A>) qui spécifient un nom ou de la méthode <xref:System.Threading.EventWaitHandle.OpenExisting%2A?displayProperty=nameWithType>.

Pour plus d’informations, consultez l’article [EventWaitHandle](eventwaithandle.md). Pour la référence d’API, consultez <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.AutoResetEvent>, <xref:System.Threading.ManualResetEvent> et <xref:System.Threading.ManualResetEventSlim>.

### <a name="countdownevent-class"></a>Classe CountdownEvent

La classe <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> représente un événement défini quand son nombre est égal à zéro. Bien que <xref:System.Threading.CountdownEvent.CurrentCount?displayProperty=nameWithType> soit supérieure à zéro, un thread qui appelle <xref:System.Threading.CountdownEvent.Wait%2A?displayProperty=nameWithType> est bloqué. Appelez <xref:System.Threading.CountdownEvent.Signal%2A?displayProperty=nameWithType> pour décrémenter le nombre d’événements.

Contrairement à <xref:System.Threading.ManualResetEvent> ou à <xref:System.Threading.ManualResetEventSlim>, que vous pouvez utiliser pour débloquer plusieurs threads avec un signal d’un thread, vous pouvez utiliser <xref:System.Threading.CountdownEvent> pour débloquer un ou plusieurs threads avec des signaux de plusieurs threads.

Pour plus d’informations, consultez l’article [CountdownEvent](countdownevent.md) et la référence d’API <xref:System.Threading.CountdownEvent>.

### <a name="barrier-class"></a>Classe de cloisonnement

La classe <xref:System.Threading.Barrier?displayProperty=nameWithType> représente une barrière de l’exécution du thread. Un thread qui appelle la méthode <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> signale qu’il a atteint le cloisonnement et attend que d’autres threads participants atteignent également le cloisonnement. Lorsque tous les threads participants atteignent le cloisonnement, ils continuent. La barrière est réinitialisée et peut être à nouveau utilisée.

Vous pouvez utiliser <xref:System.Threading.Barrier> quand un ou plusieurs threads requièrent les résultats d’autres threads avant de passer à la phase de calcul suivante.

Pour plus d’informations, consultez l’article [Cloisonnement](barrier.md) et la référence d’API <xref:System.Threading.Barrier>.

## <a name="interlocked-class"></a>Interlocked (classe)

La classe <xref:System.Threading.Interlocked?displayProperty=nameWithType> fournit des méthodes statiques qui effectuent des opérations atomiques simples sur une variable. Ces opérations atomiques incluent l'addition, l’incrémentation et la décrémentation, l’échange et l’échange conditionnel en fonction d'une comparaison, ainsi qu’une opération de lecture d’une valeur entière 64 bits.

Pour plus d'informations, consultez la référence d’API <xref:System.Threading.Interlocked>.

## <a name="spinwait-structure"></a>Structure SpinWait

La structure <xref:System.Threading.SpinWait?displayProperty=nameWithType> prend en charge l'attente basée sur les spins. Vous voudrez peut-être l’utiliser quand un thread doit attendre le signalement d'un événement ou la satisfaction d'une condition, mais que le temps d'attente réel est supposé être inférieur à la latence requise, en utilisant un descripteur d'attente ou en bloquant le thread. À l'aide de <xref:System.Threading.SpinWait>, vous pouvez spécifier une courte période de rotation pendant l'attente, puis générer (par exemple, en attente ou en veille) uniquement si la condition n'a pas été remplie dans le délai spécifié.

Pour plus d’informations, consultez l’article [SpinWait](spinwait.md) et la référence d’API <xref:System.Threading.SpinWait>.

## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Collections thread-safe](../collections/thread-safe/index.md)
- [Fonctionnalités et objets de threading](threading-objects-and-features.md)
