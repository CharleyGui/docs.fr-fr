---
title: Événements ETW dans la bibliothèque parallèle de tâches et PLINQ
description: En savoir plus sur les événements ETW dans la bibliothèque parallèle de tâches et PLINQ. Utilisez ces événements pour profiler et dépanner des applications.
ms.date: 03/30/2017
helpviewer_keywords:
- tasks, ETW events
ms.assetid: 87a9cff5-d86f-4e44-a06e-d12764d0dce2
ms.openlocfilehash: 4cb4967ea704064ae08d09311ff33720e3871e19
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263644"
---
# <a name="etw-events-in-task-parallel-library-and-plinq"></a>Événements ETW dans la bibliothèque parallèle de tâches et PLINQ

La bibliothèque parallèle de tâches et PLINQ génèrent les événements de suivi d’événements pour Windows (ETW) que vous pouvez utiliser pour profiler et dépanner des applications à l’aide d’outils tels que Windows Performance Analyzer. Toutefois, dans la plupart des scénarios, la meilleure façon de profiler du code d’application parallèle consiste à utiliser le [visualiseur concurrentiel](/visualstudio/profiling/concurrency-visualizer) dans Visual Studio.

## <a name="task-parallel-library-etw-events"></a>Événements ETW de la bibliothèque parallèle de tâches

Dans la structure EVENT_HEADER, le GUID ProviderId pour les événements générés par <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> est :

`0x2e5dba47, 0xa3d2, 0x4d16, 0x8e, 0xe0, 0x66, 0x71, 0xff, 0xdc, 0xd7, 0xb5`

### <a name="parallel-loop-begin"></a>Début de la boucle parallèle

EVENT_DESCRIPTOR.Task = 1

EVENT_DESCRIPTOR.Id = 1

#### <a name="user-data"></a>Données utilisateur

|**Nom**|**Type**|**Description**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID du TaskScheduler qui a démarré la boucle.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID de la tâche qui a démarré la boucle.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Identificateur unique utilisé pour indiquer l’imbrication et les paires pour les événements comportant des sémantiques de bifurcation/jonction.|
|OperationType|<xref:System.Int32?displayProperty=nameWithType>|Indique le type de boucle :<br /><br /> 1 = ParallelInvoke<br /><br /> 2 = ParallelFor<br /><br /> 3 = ParallelForEach|
|InclusiveFrom|<xref:System.Int64?displayProperty=nameWithType>|Valeur de départ du compteur de boucles|
|ExclusiveTo|<xref:System.Int64?displayProperty=nameWithType>|Valeur de fin du compteur de boucles|

### <a name="parallel-loop-end"></a>Fin de la boucle parallèle

 EVENT_DESCRIPTOR.Task = 2

 EVENT_DESCRIPTOR.Id = 2

#### <a name="user-data"></a>Données utilisateur

|**Nom**|**Type**|**Description**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID du TaskScheduler qui a démarré la boucle.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID de la tâche qui a démarré la boucle.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Identificateur unique utilisé pour indiquer l’imbrication et les paires pour les événements comportant des sémantiques de bifurcation/jonction.|
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Nombre total d’itérations|

### <a name="parallel-invoke-begin"></a>Début de l’appel parallèle

 EVENT_DESCRIPTOR.Task = 3

 EVENT_DESCRIPTOR.Id = 3

#### <a name="user-data"></a>Données utilisateur

|**Nom**|**Type**|**Description**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID du TaskScheduler qui a démarré la boucle.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID de la tâche qui a démarré la boucle.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Identificateur unique utilisé pour indiquer l’imbrication et les paires pour les événements comportant des sémantiques de bifurcation/jonction.|
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Nombre total d’itérations|
|operationType|<xref:System.Int32?displayProperty=nameWithType>|Indique le type de boucle :<br /><br /> 1 = ParallelInvoke<br /><br /> 2 = ParallelFor<br /><br /> 3 = ParallelForEach|
|ActionCount|<xref:System.Int32?displayProperty=nameWithType>|Nombre d’actions qui seront exécutées dans l’appel parallèle.|

### <a name="parallel-invoke-end"></a>Fin de l’appel parallèle

 EVENT_DESCRIPTOR.Task = 4

 EVENT_DESCRIPTOR.Id = 4

#### <a name="user-data"></a>Données utilisateur

|**Nom**|**Type**|**Description**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID du TaskScheduler qui a démarré la boucle.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID de la tâche qui a démarré la boucle.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Identificateur unique utilisé pour indiquer l’imbrication et les paires pour les événements comportant des sémantiques de bifurcation/jonction.|

## <a name="plinq-etw-events"></a>Événements ETW de PLINQ

 Le GUID EVENT_HEADER.ProviderId pour PLINQ est :

`0x159eeeec, 0x4a14, 0x4418, 0xa8, 0xfe, 0xfa, 0xab, 0xcd, 0x98, 0x78, 0x87`

### <a name="parallel-query-begin"></a>Début de requête parallèle

 EVENT_DESCRIPTOR.Task = 1

 EVENT_DESCRIPTOR.Id = 1

#### <a name="user-data"></a>Données utilisateur

|**Nom**|**Type**|**Description**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID du TaskScheduler qui a démarré la boucle.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID de la tâche qui a démarré la boucle.|
|QueryID|<xref:System.Int32?displayProperty=nameWithType>|Identificateur de requête unique.|

### <a name="parallel-query-end"></a>Fin de requête parallèle

 EVENT_DESCRIPTOR.Task = 2

 EVENT_DESCRIPTOR.Id = 2

#### <a name="user-data"></a>Données utilisateur

|**Nom**|**Type**|**Description**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID du TaskScheduler qui a démarré la boucle.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID de la tâche qui a démarré la boucle.|
|QueryID|<xref:System.Int32?displayProperty=nameWithType>|Identificateur de requête unique.|

## <a name="see-also"></a>Voir aussi

- [Événements ETW dans le .NET Framework](etw-events.md)
- [Bibliothèque parallèle de tâches](../../standard/parallel-programming/task-parallel-library-tpl.md)
- [Parallel LINQ (PLINQ)](../../standard/parallel-programming/introduction-to-plinq.md)
