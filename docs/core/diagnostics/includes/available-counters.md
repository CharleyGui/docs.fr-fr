---
ms.openlocfilehash: f561550d57e98a515fa3bdf56eea1dc1759b4e69
ms.sourcegitcommit: 1e6439ec4d5889fc08cf3bfb4dac2b91931eb827
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2020
ms.locfileid: "88025013"
---
## <a name="available-counters"></a>Compteurs disponibles

Dans divers packages .NET, les métriques de base sur le garbage collection (GC), juste-à-temps (JIT), les assemblys, les exceptions, les threads, la mise en réseau et les requêtes Web sont publiés à l’aide de EventCounters.

### <a name="systemruntime-counters"></a>Compteurs « System. Runtime »

Les compteurs suivants sont publiés dans le cadre du Runtime .NET et sont conservés dans le [`RuntimeEventSource.cs`](https://github.com/dotnet/coreclr/blob/master/src/System.Private.CoreLib/src/System/Diagnostics/Eventing/RuntimeEventSource.cs) .

| Compteur | Description |
|--|--|
| :::no-loc text="% Time in GC since last GC"::: (`time-in-gc`) | Pourcentage de temps dans le GC depuis le dernier GC |
| :::no-loc text="Allocation Rate"::: (`alloc-rate`) | Taux d’allocation en octets |
| :::no-loc text="CPU Usage"::: (`cpu-usage`) | Pourcentage d’utilisation du processeur |
| :::no-loc text="Exception Count"::: (`exception-count`) | Nombre d’exceptions qui se sont produites |
| :::no-loc text="GC Heap Size"::: (`gc-heap-size`) | Nombre d’octets supposés être alloués en fonction de<xref:System.GC.GetTotalMemory(System.Boolean)?displayProperty=nameWithType> |
| :::no-loc text="Gen 0 GC Count"::: (`gen-0-gc-count`) | Nombre de fois que GC s’est produit pour la génération 0 |
| :::no-loc text="Gen 0 Size"::: (`gen-0-size`) | Nombre d’octets pour GC de génération 0 |
| :::no-loc text="Gen 1 GC Count"::: (`gen-1-gc-count`) | Nombre d’occurrences du GC pour la génération 1 |
| :::no-loc text="Gen 1 Size"::: (`gen-1-size`) | Nombre d’octets pour le GC de génération 1 |
| :::no-loc text="Gen 2 GC Count"::: (`gen-2-gc-count`) | Le nombre de fois que GC s’est produit pour la génération 2 |
| :::no-loc text="Gen 2 Size"::: (`gen-2-size`) | Nombre d’octets pour le GC de génération 2 |
| :::no-loc text="LOH Size"::: (`loh-size`) | Nombre d’octets pour le GC de génération 3 |
| :::no-loc text="Monitor Lock Contention Count"::: (`monitor-lock-contention-count`) | Nombre de conflits lors de la tentative d’exécution du verrou du moniteur, en fonction de<xref:System.Threading.Monitor.LockContentionCount?displayProperty=nameWithType> |
| :::no-loc text="Number of Active Timers"::: (`active-timer-count`) | Nombre d' <xref:System.Threading.Timer> instances actuellement actives, en fonction de<xref:System.Threading.Timer.ActiveCount?displayProperty=nameWithType> |
| :::no-loc text="Number of Assemblies Loaded"::: (`assembly-count`) | Nombre d' <xref:System.Reflection.Assembly> instances chargées dans un processus à un moment donné |
| :::no-loc text="ThreadPool Completed Work Item Count"::: (`threadpool-completed-items-count`) | Nombre d’éléments de travail traités jusqu’à présent dans le<xref:System.Threading.ThreadPool> |
| :::no-loc text="ThreadPool Queue Length"::: (`threadpool-queue-length`) | Nombre d’éléments de travail actuellement en file d’attente à traiter dans le<xref:System.Threading.ThreadPool> |
| :::no-loc text="ThreadPool Thread Count"::: (`threadpool-thread-count`) | Nombre de threads de pool de threads qui existent actuellement dans le <xref:System.Threading.ThreadPool> , en fonction de<xref:System.Threading.ThreadPool.ThreadCount?displayProperty=nameWithType> |
| :::no-loc text="Working Set"::: (`working-set`) | Quantité de mémoire physique mappée au contexte de processus à un point dans le temps sur<xref:System.Environment.WorkingSet?displayProperty=nameWithType> |

### <a name="microsoftaspnetcorehosting-counters"></a>Compteurs « Microsoft. AspNetCore. Hosting »

Les compteurs suivants sont publiés dans le cadre de [ASP.net Core](/aspnet/core) et sont conservés dans [`HostingEventSource.cs`](https://github.com/dotnet/aspnetcore/blob/master/src/Hosting/Hosting/src/Internal/HostingEventSource.cs) .

| Compteur | Description |
|--|--|
| :::no-loc text="Current Requests"::: (`current-requests`) | Nombre total de requêtes démarrées, mais pas encore arrêtées |
| :::no-loc text="Failed Requests"::: (`failed-requests`) | Nombre total de demandes ayant échoué pendant la durée de vie de l’application |
| :::no-loc text="Request Rate"::: (`requests-per-second`) | Nombre de demandes qui se produisent par seconde |
| :::no-loc text="Total Requests"::: (`total-requests`) | Nombre total de demandes qui se sont produites pendant la durée de vie de l’application |

### <a name="microsoftaspnetcorehttpconnections-counters"></a>Compteurs « Microsoft. AspNetCore. http. Connections »

Les compteurs suivants sont publiés dans le cadre de [ASP.net Core signalr](/aspnet/core/signalr/introduction) et sont conservés dans [`HttpConnectionsEventSource.cs`](https://github.com/dotnet/aspnetcore/blob/master/src/SignalR/common/Http.Connections/src/Internal/HttpConnectionsEventSource.cs) .

| Compteur | Description |
|--|--|
| :::no-loc text="Average Connection Duration"::: (`connections-duration`) | Durée moyenne d’une connexion en millisecondes |
| :::no-loc text="Current Connections"::: (`current-connections`) | Le nombre de connexions actives qui ont démarré, mais qui n’ont pas encore été arrêtées |
| :::no-loc text="Total Connections Started"::: (`connections-started`) | Nombre total de connexions démarrées |
| :::no-loc text="Total Connections Stopped"::: (`connections-stopped`) | Nombre total de connexions qui ont été arrêtées |
| :::no-loc text="Total Connections Timed Out"::: (`connections-timed-out`) | Nombre total de connexions ayant expiré |

### <a name="microsoft-aspnetcore-server-kestrel-counters"></a>Compteurs « Microsoft-AspNetCore-Server-Kestrel »

Les compteurs suivants sont publiés dans le cadre du [serveur web ASP.net Core Kestrel](/aspnet/core/fundamentals/servers/kestrel) et sont conservés dans [`KestrelEventSource.cs`](https://github.com/dotnet/aspnetcore/blob/master/src/Servers/Kestrel/Core/src/Internal/Infrastructure/KestrelEventSource.cs) .

| Compteur | Description |
|--|--|
| :::no-loc text="Connection Queue Length"::: (`connection-queue-length`) | Longueur actuelle de la file d’attente de connexion |
| :::no-loc text="Connection Rate"::: (`connections-per-second`) | Nombre de connexions par seconde au serveur Web |
| :::no-loc text="Current Connections"::: (`current-connections`) | Nombre actuel de connexions actives au serveur Web |
| :::no-loc text="Current TLS Handshakes"::: (`current-tls-handshakes`) | Nombre actuel de négociations TLS |
| :::no-loc text="Current Upgraded Requests (WebSockets)"::: (`current-upgraded-requests`) | Nombre actuel de demandes mises à niveau (WebSockets) |
| :::no-loc text="Failed TLS Handshakes"::: (`failed-tls-handshakes`) | Nombre total d’échecs de négociation TLS |
| :::no-loc text="Request Queue Length"::: (`request-queue-length`) | Longueur actuelle de la file d’attente des demandes |
| :::no-loc text="TLS Handshake Rate"::: (`tls-handshakes-per-second`) | Nombre de négociations TLS par seconde |
| :::no-loc text="Total Connections"::: (`total-connections`) | Nombre total de connexions au serveur Web |
| :::no-loc text="Total TLS Handshakes"::: (`total-tls-handshakes`) | Nombre total de négociations TLS avec le serveur Web |
