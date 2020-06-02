---
title: Modes de latence
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
ms.openlocfilehash: ee45fe5e8016c7507bc3a873e615fd8379810a8e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286013"
---
# <a name="latency-modes"></a>Modes de latence

Pour récupérer des objets, le garbage collector (GC) doit arrêter tous les threads en cours d’exécution dans une application. La durée pendant laquelle le garbage collector est actif est appelée « *latence*».

Dans certaines situations, par exemple, quand une application récupère des données ou affiche du contenu, un garbage collection complet peut se produire à un moment critique et nuire aux performances. Vous pouvez ajuster le niveau d'intrusion du garbage collector en définissant la propriété <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> sur l'une des valeurs<xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>.

## <a name="low-latency-settings"></a>Paramètres de latence faible

L’utilisation d’un paramètre de latence « faible » signifie que le garbage collector est à l’abri d’une baisse de votre application. Le garbage collection est plus prudent en ce qui concerne la récupération de la mémoire.

L'énumération <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> fournit deux paramètres de latence faible :

- [GCLatencyMode. LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) supprime les collections de génération 2 et effectue uniquement des collections de génération 0 et 1. Elle ne peut être utilisée que pour de courtes durées. Sur des périodes plus longues, si le système connaît une sollicitation de mémoire importante, le garbage collector déclenchera une collection, qui pourra brièvement suspendre l'application et interrompre une opération critique. Ce paramètre est disponible uniquement pour le garbage collection des stations de travail.

- [GCLatencyMode. SustainedLowLatency](xref:System.Runtime.GCLatencyMode.SustainedLowLatency) supprime les collections de 2e génération 2 et exécute uniquement les collections de génération 0, 1 et d’arrière-plan 2. Il peut être utilisé pour de longues périodes et est disponible à la fois pour le garbage collection des stations de travail et des serveurs. Ce paramètre ne peut pas être utilisé si la garbage collection d’arrière-plan est désactivée.

Pendant les périodes de faible latence, les collections de génération 2 sont empêchées, sauf dans les cas suivants :

- Le système reçoit une notification de mémoire insuffisante du système d'exploitation.

- Le code d’application induit une collection en appelant la <xref:System.GC.Collect%2A?displayProperty=nameWithType> méthode et en spécifiant 2 pour le `generation` paramètre.

## <a name="scenarios"></a>Scénarios

Le tableau suivant répertorie les scénarios d’application pour l’utilisation des <xref:System.Runtime.GCLatencyMode> valeurs :

|Mode de latence|Scénarios d’application|
|------------------|---------------------------|
|<xref:System.Runtime.GCLatencyMode.Batch>|Pour les applications qui n’ont pas d’interface utilisateur ou d’opérations côté serveur.<br /><br />Lorsque la garbage collection d’arrière-plan est désactivée, il s’agit du mode par défaut pour les garbage collection de station de travail et de serveur. <xref:System.Runtime.GCLatencyMode.Batch>le mode remplace également le paramètre [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) , autrement dit, il empêche les collections en arrière-plan ou simultanées.|
|<xref:System.Runtime.GCLatencyMode.Interactive>|Pour la plupart des applications qui ont une interface utilisateur.<br /><br />Il s’agit du mode par défaut pour les garbage collection de station de travail et de serveur. Toutefois, si une application est hébergée, les paramètres du garbage collector du processus d’hébergement sont prioritaires.|
|<xref:System.Runtime.GCLatencyMode.LowLatency>|Pour les applications qui ont des opérations de courte durée pour lesquelles le temps est important, et durant lesquelles les interruptions du garbage collector pourraient provoquer des perturbations. Par exemple, les applications qui restituent des animations ou des fonctions d’acquisition de données.|
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|Pour les applications qui ont des opérations pour lesquelles le temps est important, pendant une durée définie mais potentiellement longue durant laquelle les interruptions du garbage collector pourraient provoquer des perturbations. Par exemple, les applications nécessitant des temps de réponse rapides en raison du changement des données de marché pendant les heures de négociation.<br /><br />Ce mode augmente davantage la taille du tas managé que les autres modes. Parce qu'il ne compacte pas le tas managé, une fragmentation plus importante est possible. Assurez-vous que suffisamment de mémoire est disponible.|

## <a name="guidelines-for-using-low-latency"></a>Instructions pour l’utilisation de la faible latence

Lorsque vous utilisez le mode [GCLatencyMode. LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) , tenez compte des instructions suivantes :

- Choisissez une période aussi courte que possible pour la faible latence.

- Évitez d'allouer de grandes quantités de mémoire pendant les périodes de faible latence. Vous pouvez recevoir des notifications de mémoire insuffisante, car le garbage collection récupère moins d'objets.

- En mode de latence faible, réduisez le nombre de nouvelles allocations, en particulier les allocations sur le tas d’objets volumineux et les objets épinglés.

- N'oubliez pas les threads qui peuvent être à l'origine d'allocations. Étant donné que le <xref:System.Runtime.GCSettings.LatencyMode%2A> paramètre de propriété est à l’ensemble du processus, des <xref:System.OutOfMemoryException> exceptions peuvent être générées sur tout thread qui alloue.

- Encapsulez le code de latence faible dans les régions d’exécution limitée. Pour plus d’informations, consultez [régions d’exécution restreinte](../../framework/performance/constrained-execution-regions.md).

- Vous pouvez forcer les collections de génération 2 pendant une période de latence basse en appelant la méthode <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType>.

## <a name="see-also"></a>Voir aussi

- <xref:System.GC?displayProperty=nameWithType>
- [Collections induites](induced.md)
- [Garbage collection](index.md)
