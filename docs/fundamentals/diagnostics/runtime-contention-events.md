---
title: Surveiller les événements d’exécution de contention de verrouillage
description: Consultez événements ETW qui collectent des informations spécifiques aux conflits de verrouillage de l’analyse.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- monitor lock contention events (CoreCLR)
- ETW, EventPipe, LTTng contention events (CoreCLR)
ms.openlocfilehash: 38e5f493d4b223b4839dbd6f814cf656722189b2
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "96588606"
---
# <a name="net-runtime-contention-events"></a>Événements de conflit du Runtime .NET

Ces événements de Runtime capturent des informations sur les conflits de verrous du moniteur tels que avec `Monitor.Enter` ou le mot clé C# lock. Pour plus d’informations sur l’utilisation de ces événements à des fins de diagnostic, consultez [journalisation et traçage d’applications .net](../../core/diagnostics/logging-tracing.md)

## <a name="contentionstart_v1-event"></a>Événement ContentionStart_V1

Cet événement est émis au démarrage d’une contention de verrouillage du moniteur.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`ContentionKeyword` (0x4000)|Informatif (4)|

 Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|81|Un conflit de verrouillage du moniteur démarre.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`Flags`|`win:UInt8`|`0` pour managé ; `1` pour le mode natif.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="contentionstop_v1-event"></a>Événement ContentionStop_V1

Cet événement est émis à la fin d’une contention de verrouillage du moniteur.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`ContentionKeyword` (0x4000)|Informatif (4)|

 Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`ContentionStop_V1`|91|Une contention de verrouillage du moniteur se termine.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`Flags`|`win:UInt8`|`0` pour managé ; `1` pour le mode natif.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|
|`DurationNs`|`win:Double`|Durée de la contention en nanosecondes.|
