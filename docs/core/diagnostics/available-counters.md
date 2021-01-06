---
title: EventCounters bien connus dans .NET
description: Passez en revue les EventCounters publiés par le runtime et les bibliothèques .NET.
ms.topic: reference
ms.date: 12/17/2020
ms.openlocfilehash: 8bd14c7caf004cefe73d5b0676b9fa3280840442
ms.sourcegitcommit: c3093e9d106d8ca87cc86eef1f2ae4ecfb392118
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97737292"
---
# <a name="well-known-eventcounters-in-net"></a>EventCounters bien connus dans .NET

Le runtime et les bibliothèques .NET implémentent et publient plusieurs [`EventCounter`](./event-counters.md) qui peuvent être utilisés pour identifier et diagnostiquer divers problèmes de performances. Ce document est une référence sur les fournisseurs qui peuvent être utilisés pour surveiller ces informations `EventCounters` et leurs descriptions.

## <a name="systemruntime-counters"></a>Compteurs System. Runtime

Les compteurs suivants sont publiés dans le cadre du Runtime .NET (CoreCLR) et sont conservés dans le [`RuntimeEventSource.cs`](https://github.com/dotnet/coreclr/blob/master/src/System.Private.CoreLib/src/System/Diagnostics/Eventing/RuntimeEventSource.cs) .

| Compteur | Description |
|--|--|
| :::no-loc text="% Time in GC since last GC"::: (`time-in-gc`) | Pourcentage de temps dans le GC depuis le dernier GC |
| :::no-loc text="Allocation Rate"::: (`alloc-rate`) | Nombre d’octets alloués par intervalle de mise à jour |
| :::no-loc text="CPU Usage"::: (`cpu-usage`) | Pourcentage de l’utilisation du processeur du processus par rapport à toutes les ressources processeur du système |
| :::no-loc text="Exception Count"::: (`exception-count`) | Nombre d’exceptions qui se sont produites |
| :::no-loc text="GC Heap Size"::: (`gc-heap-size`) | Nombre d’octets supposés être alloués en fonction de <xref:System.GC.GetTotalMemory(System.Boolean)?displayProperty=nameWithType> |
| :::no-loc text="Gen 0 GC Count"::: (`gen-0-gc-count`) | Nombre de fois que GC s’est produit pour la génération 0 par intervalle de mise à jour |
| :::no-loc text="Gen 0 Size"::: (`gen-0-size`) | Nombre d’octets pour GC de génération 0 |
| :::no-loc text="Gen 1 GC Count"::: (`gen-1-gc-count`) | Nombre d’occurrences du GC pour la génération 1 par intervalle de mise à jour |
| :::no-loc text="Gen 1 Size"::: (`gen-1-size`) | Nombre d’octets pour le GC de génération 1 |
| :::no-loc text="Gen 2 GC Count"::: (`gen-2-gc-count`) | Nombre de fois que GC s’est produit pour la génération 2 par intervalle de mise à jour |
| :::no-loc text="Gen 2 Size"::: (`gen-2-size`) | Nombre d’octets pour le GC de génération 2 |
| :::no-loc text="LOH Size"::: (`loh-size`) | Nombre d’octets pour le tas d’objets volumineux |
| :::no-loc text="POH Size"::: (`poh-size`) | Nombre d’octets pour le tas d’objets épinglés (disponible sur .NET 5 et versions ultérieures) |
| :::no-loc text="GC Fragmentation"::: (`gc-fragmentation`) | Fragmentation du tas GC (disponible sur .NET 5 et versions ultérieures) |
| :::no-loc text="Monitor Lock Contention Count"::: (`monitor-lock-contention-count`) | Nombre de conflits lors de la tentative d’exécution du verrou du moniteur, en fonction de <xref:System.Threading.Monitor.LockContentionCount?displayProperty=nameWithType> |
| :::no-loc text="Number of Active Timers"::: (`active-timer-count`) | Nombre d' <xref:System.Threading.Timer> instances actuellement actives, en fonction de <xref:System.Threading.Timer.ActiveCount?displayProperty=nameWithType> |
| :::no-loc text="Number of Assemblies Loaded"::: (`assembly-count`) | Nombre d' <xref:System.Reflection.Assembly> instances chargées dans un processus à un moment donné |
| :::no-loc text="ThreadPool Completed Work Item Count"::: (`threadpool-completed-items-count`) | Nombre d’éléments de travail traités jusqu’à présent dans le <xref:System.Threading.ThreadPool> |
| :::no-loc text="ThreadPool Queue Length"::: (`threadpool-queue-length`) | Nombre d’éléments de travail actuellement en file d’attente à traiter dans le <xref:System.Threading.ThreadPool> |
| :::no-loc text="ThreadPool Thread Count"::: (`threadpool-thread-count`) | Nombre de threads de pool de threads qui existent actuellement dans le <xref:System.Threading.ThreadPool> , en fonction de <xref:System.Threading.ThreadPool.ThreadCount?displayProperty=nameWithType> |
| :::no-loc text="Working Set"::: (`working-set`) | Quantité de mémoire physique mappée au contexte de processus à un point dans le temps sur <xref:System.Environment.WorkingSet?displayProperty=nameWithType> |
| :::no-loc text="IL Bytes Jitted"::: (`il-bytes-jitted`) | Taille totale des ILs qui sont compilés juste-à-temps, en octets (disponible sur .NET 5 et versions ultérieures) |
| :::no-loc text="Method Jitted Count"::: (`method-jitted-count`) | Nombre de méthodes qui sont compilées juste-à-temps (disponibles sur .NET 5 et versions ultérieures) |

## <a name="microsoftaspnetcorehosting-counters"></a>Compteurs « Microsoft. AspNetCore. Hosting »

Les compteurs suivants sont publiés dans le cadre de [ASP.net Core](/aspnet/core) et sont conservés dans [`HostingEventSource.cs`](https://github.com/dotnet/aspnetcore/blob/master/src/Hosting/Hosting/src/Internal/HostingEventSource.cs) .

| Compteur | Description |
|--|--|
| :::no-loc text="Current Requests"::: (`current-requests`) | Nombre total de demandes qui ont démarré, mais qui n’ont pas encore été arrêtées |
| :::no-loc text="Failed Requests"::: (`failed-requests`) | Nombre total de demandes ayant échoué pendant la durée de vie de l’application |
| :::no-loc text="Request Rate"::: (`requests-per-second`) | Nombre de demandes qui se produisent par intervalle de mise à jour |
| :::no-loc text="Total Requests"::: (`total-requests`) | Nombre total de demandes qui se sont produites pendant la durée de vie de l’application |

## <a name="microsoftaspnetcorehttpconnections-counters"></a>Compteurs « Microsoft. AspNetCore. http. Connections »

Les compteurs suivants sont publiés dans le cadre de [ASP.net Core signalr](/aspnet/core/signalr/introduction) et sont conservés dans [`HttpConnectionsEventSource.cs`](https://github.com/dotnet/aspnetcore/blob/master/src/SignalR/common/Http.Connections/src/Internal/HttpConnectionsEventSource.cs) .

| Compteur | Description |
|--|--|
| :::no-loc text="Average Connection Duration"::: (`connections-duration`) | Durée moyenne d’une connexion en millisecondes |
| :::no-loc text="Current Connections"::: (`current-connections`) | Le nombre de connexions actives qui ont démarré, mais qui n’ont pas encore été arrêtées |
| :::no-loc text="Total Connections Started"::: (`connections-started`) | Nombre total de connexions démarrées |
| :::no-loc text="Total Connections Stopped"::: (`connections-stopped`) | Nombre total de connexions qui ont été arrêtées |
| :::no-loc text="Total Connections Timed Out"::: (`connections-timed-out`) | Nombre total de connexions ayant expiré |

## <a name="microsoft-aspnetcore-server-kestrel-counters"></a>Compteurs « Microsoft-AspNetCore-Server-Kestrel »

Les compteurs suivants sont publiés dans le cadre du [serveur web ASP.net Core Kestrel](/aspnet/core/fundamentals/servers/kestrel) et sont conservés dans [`KestrelEventSource.cs`](https://github.com/dotnet/aspnetcore/blob/master/src/Servers/Kestrel/Core/src/Internal/Infrastructure/KestrelEventSource.cs) .

| Compteur | Description |
|--|--|
| :::no-loc text="Connection Queue Length"::: (`connection-queue-length`) | Longueur actuelle de la file d’attente de connexion |
| :::no-loc text="Connection Rate"::: (`connections-per-second`) | Nombre de connexions par intervalle de mise à jour au serveur Web |
| :::no-loc text="Current Connections"::: (`current-connections`) | Nombre actuel de connexions actives au serveur Web |
| :::no-loc text="Current TLS Handshakes"::: (`current-tls-handshakes`) | Nombre actuel de négociations TLS |
| :::no-loc text="Current Upgraded Requests (WebSockets)"::: (`current-upgraded-requests`) | Nombre actuel de demandes mises à niveau (WebSockets) |
| :::no-loc text="Failed TLS Handshakes"::: (`failed-tls-handshakes`) | Nombre total d’échecs de négociation TLS |
| :::no-loc text="Request Queue Length"::: (`request-queue-length`) | Longueur actuelle de la file d’attente des demandes |
| :::no-loc text="TLS Handshake Rate"::: (`tls-handshakes-per-second`) | Nombre de négociations TLS par intervalle de mise à jour |
| :::no-loc text="Total Connections"::: (`total-connections`) | Nombre total de connexions au serveur Web |
| :::no-loc text="Total TLS Handshakes"::: (`total-tls-handshakes`) | Nombre total de négociations TLS avec le serveur Web |

## <a name="systemnethttp-counters"></a>Compteurs « System .net. http »

Les compteurs suivants sont publiés par la pile HTTP.  Ces compteurs sont disponibles uniquement sur .NET 5 et versions ultérieures.

| Compteur | Description |
|--|--|
| :::no-loc text="Requests Started"::: (`requests-started`) | Nombre de requêtes démarrées depuis le démarrage du processus |
| :::no-loc text="Requests Started Rate"::: (`requests-started-rate`) | Nombre de requêtes démarrées par intervalle de mise à jour |
| :::no-loc text="Requests Failed"::: (`requests-failed`) | Nombre de demandes ayant échoué depuis le démarrage du processus |
| :::no-loc text="Requests Failed Rate"::: (`requests-failed-rate`) | Nombre de demandes ayant échoué par intervalle de mise à jour |
| :::no-loc text="Current Requests"::: (`current-requests`) | Nombre actuel de requêtes HTTP actives qui ont démarré mais qui ne sont pas encore terminées ou qui ont échoué |
| :::no-loc text="Current HTTP 1.1 Connections"::: (`http11-connections-current-total`) | Nombre actuel de connexions HTTP 1,1 qui ont démarré mais qui ne sont pas encore terminées ou qui ont échoué |
| :::no-loc text="Current HTTP 2.0 Connections"::: (`http20-connections-current-total`) | Nombre actuel de connexions HTTP 2,0 qui ont démarré mais qui ne sont pas encore terminées ou qui ont échoué |
| :::no-loc text="HTTP 1.1 Requests Queue Duration"::: (`http11-requests-queue-duration`) | Durée moyenne des requêtes HTTP 1,1 passées dans la file d’attente des demandes |
| :::no-loc text="HTTP 2.0 Requests Queue Duration"::: (`http20-requests-queue-duration`) | Durée moyenne des requêtes HTTP 2,0 passées dans la file d’attente des demandes |

## <a name="systemnetnameresolution-counters"></a>Compteurs « System .net. NameResolution »

Les compteurs suivants effectuent le suivi des mesures relatives aux recherches DNS. Ces compteurs sont disponibles uniquement sur .NET 5 et versions ultérieures.

| Compteur | Description |
|--|--|
| :::no-loc text="DNS Lookups Requested"::: (`dns-lookups-requested`) | Nombre de recherches DNS demandées depuis le démarrage du processus |
| :::no-loc text="Average DNS Lookup Duration"::: (`dns-lookups-duration`) | Temps moyen nécessaire pour une recherche DNS |

## <a name="systemnetsecurity-counters"></a>Compteurs « System .net. Security »

Les compteurs suivants effectuent le suivi des mesures relatives au protocole TLS (Transport Layer Security).  Ces compteurs sont disponibles uniquement sur .NET 5 et versions ultérieures.

| Compteur | Description |
|--|--|
| :::no-loc text="TLS handshakes completed"::: (`tls-handshake-rate`) | Nombre de négociations TLS effectuées par intervalle de mise à jour |
| :::no-loc text="Total TLS handshakes completed"::: (`total-tls-handshakes`) | Nombre total de négociations TLS terminées depuis le démarrage du processus |
| :::no-loc text="Current TLS handshakes"::: (`current-tls-handshakes`) | Nombre actuel de négociations TLS démarrées mais pas encore terminées |
| :::no-loc text="Total TLS handshakes failed"::: (`failed-tls-handshakes`) | Nombre total d’échecs de négociation TLS depuis le démarrage du processus |
| :::no-loc text="All TLS Sessions Active"::: (`all-tls-sessions-open`) | Nombre de sessions TLS actives de toute version |
| :::no-loc text="TLS 1.0 Sessions Active"::: (`tls10-sessions-open`) | Nombre de sessions TLS 1,0 actives |
| :::no-loc text="TLS 1.1 Sessions Active"::: (`tls11-sessions-open`) | Nombre de sessions TLS 1,1 actives |
| :::no-loc text="TLS 1.2 Sessions Active"::: (`tls12-sessions-open`) | Nombre de sessions TLS 1,2 actives |
| :::no-loc text="TLS 1.3 Sessions Active"::: (`tls13-sessions-open`) | Nombre de sessions TLS 1,3 actives |
| :::no-loc text="TLS Handshake Duration"::: (`all-tls-handshake-duration`) | Durée moyenne de toutes les négociations TLS |
| :::no-loc text="TLS 1.0 Handshake Duration"::: (`tls10-handshake-duration`) | Durée moyenne des négociations TLS 1,0 |
| :::no-loc text="TLS 1.1 Handshake Duration"::: (`tls11-handshake-duration`) | Durée moyenne des négociations TLS 1,1 |
| :::no-loc text="TLS 1.2 Handshake Duration"::: (`tls12-handshake-duration`) | Durée moyenne des négociations TLS 1,2 |
| :::no-loc text="TLS 1.3 Handshake Duration"::: (`tls13-handshake-duration`) | Durée moyenne des négociations TLS 1,3 |

## <a name="systemnetsockets-counters-available-on-net-5-and-later-versions"></a>Compteurs « System .net. Sockets » (disponibles sur .NET 5 et versions ultérieures)

Les compteurs suivants effectuent le suivi des mesures relatives à <xref:System.Net.Sockets.Socket> .

| Compteur | Description |
|--|--|
| :::no-loc text="Outgoing Connections Established"::: (`outgoing-connections-established`) | Nombre total de connexions sortantes établies depuis le démarrage du processus |
| :::no-loc text="Incoming Connections Established"::: (`incoming-connections-established`) | Nombre total de connexions entrantes établies depuis le démarrage du processus |
| :::no-loc text="Bytes Received"::: (`bytes-received`) | Nombre total d’octets reçus depuis le démarrage du processus |
| :::no-loc text="Bytes Sent"::: (`bytes-sent`) | Nombre total d’octets envoyés depuis le démarrage du processus |
| :::no-loc text="Datagrams Received"::: (`datagrams-received`) | Nombre total de datagrammes reçus depuis le démarrage du processus |
| :::no-loc text="Datagrams Sent"::: (`datagrams-sent`) | Nombre total de datagrammes envoyés depuis le démarrage du processus |
