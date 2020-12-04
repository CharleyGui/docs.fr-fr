---
title: Événements d’exécution
description: Passez en revue les événements de diagnostic émis par le Runtime .NET (CoreCLR) qui peuvent être utilisés avec ETW, LTTng ou EventPipe.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- runtime events (CoreCLR)
- ETW, EventPipe runtime events (CoreCLR)
ms.openlocfilehash: 33fa7275ce40934ce043b4d0dba5749c37515755
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "96588605"
---
# <a name="net-runtime-events"></a>Événements du Runtime .NET

Le Runtime .NET (CoreCLR) émet différents événements qui peuvent être utilisés pour diagnostiquer les problèmes liés à votre application .NET qui peuvent être consommés via différents mécanismes tels que `ETW` , `LTTng` et `EventPipe` .

Ce document sert de référence sur les événements déclenchés par le Runtime .NET Core.

Pour les événements de Runtime dans .NET Framework, consultez [événements ETW du CLR](../../framework/performance/clr-etw-events.md).

## <a name="in-this-section"></a>Dans cette section

[Événements de conflit](runtime-contention-events.md)\
Ces événements collectent des informations sur les conflits de verrous du moniteur.

[Événements de garbage collection](runtime-garbage-collection-events.md)\
Ces événements collectent des informations relatives au garbage collection. Ils facilitent le diagnostic et le débogage, notamment la détermination du nombre de fois que garbage collection a été effectué, la quantité de mémoire libérée pendant la garbage collection, etc.

[Événements d’exception](runtime-exception-events.md)\
Ces événements de Runtime capturent des informations sur les exceptions levées.

[Événements d’interopérabilité](runtime-interop-events.md)\
Ces événements de Runtime capturent des informations sur la génération du stub Common Intermediate Language (CIL).

[Événements de chargeur et de Binder](runtime-loader-binder-events.md)\
Ces événements recueillent des informations concernant le chargement et le déchargement des assemblys et des modules.

[Événements de méthode](runtime-method-events.md)\
Ces événements collectent des informations spécifiques aux méthodes. La charge utile de ces événements est requise pour la résolution des symboles. De plus, ces événements fournissent des informations utiles telles que le nombre de fois qu'une méthode a été appelée.

[Événements de thread](runtime-thread-events.md)\
Ces événements collectent des informations sur les threads de travail et d'E/S.

[Événements de type](runtime-type-events.md)\
Ces événements collectent des informations sur le système de type.
