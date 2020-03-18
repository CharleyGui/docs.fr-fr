---
title: Modes de latence
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
ms.openlocfilehash: a8eaf0c80aa32978eead80c51a905cbcd66a537b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74283592"
---
# <a name="latency-modes"></a>Modes de latence

Pour récupérer des objets, le collecteur d’ordures (GC) doit arrêter tous les fils d’exécution dans une application. La période pendant laquelle le éboueur est actif est appelée sa *latence.*

Dans certaines situations, par exemple, quand une application récupère des données ou affiche du contenu, un garbage collection complet peut se produire à un moment critique et nuire aux performances. Vous pouvez ajuster le niveau d'intrusion du garbage collector en définissant la propriété <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> sur l'une des valeurs<xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>.

## <a name="low-latency-settings"></a>Paramètres de latence faible

L’utilisation d’un réglage de latence « faible » signifie que le collecteur d’ordures empiète moins dans votre application. La collecte des ordures est plus conservatrice au sujet de la récupération de la mémoire.

L'énumération <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> fournit deux paramètres de latence faible :

- [GCLatencyMode.LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) supprime les collections de génération 2 et n’exécute que des collections de génération 0 et 1. Elle ne peut être utilisée que pour de courtes durées. Sur des périodes plus longues, si le système connaît une sollicitation de mémoire importante, le garbage collector déclenchera une collection, qui pourra brièvement suspendre l'application et interrompre une opération critique. Ce paramètre est disponible uniquement pour le garbage collection des stations de travail.

- [GCLatencyMode.SustainedLowLatency](xref:System.Runtime.GCLatencyMode.SustainedLowLatency) supprime les collections de première génération 2 et n’exécute que des collections de génération 0, 1 et de la génération 2. Il peut être utilisé pour de longues périodes et est disponible à la fois pour le garbage collection des stations de travail et des serveurs. Ce paramètre ne peut pas être utilisé si la collecte des ordures de fond est désactivée.

Pendant les périodes de faible latence, les collections de génération 2 sont empêchées, sauf dans les cas suivants :

- Le système reçoit une notification de mémoire insuffisante du système d'exploitation.

- Le code d’application induit <xref:System.GC.Collect%2A?displayProperty=nameWithType> une collection en appelant `generation` la méthode et en spécifiant 2 pour le paramètre.

## <a name="scenarios"></a>Scénarios

Le tableau suivant répertorie <xref:System.Runtime.GCLatencyMode> les scénarios d’application pour l’utilisation des valeurs :

|Mode de latence|Scénarios d’application|
|------------------|---------------------------|
|<xref:System.Runtime.GCLatencyMode.Batch>|Pour les applications qui n’ont pas d’interface utilisateur (interface utilisateur) ou d’opérations côté serveur.<br /><br />Lorsque la collecte des ordures de fond est désactivée, c’est le mode par défaut pour la collecte des ordures de poste de travail et de serveur. <xref:System.Runtime.GCLatencyMode.Batch>le mode remplace également le paramètre [gcConcurrent,](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) c’est-à-dire qu’il empêche les collections de fond ou simultanées.|
|<xref:System.Runtime.GCLatencyMode.Interactive>|Pour la plupart des applications qui ont une interface utilisateur.<br /><br />Il s’agit du mode par défaut pour le poste de travail et la collecte des ordures serveur. Toutefois, si une application est hébergée, les paramètres de collecteur d’ordures du processus d’hébergement priment.|
|<xref:System.Runtime.GCLatencyMode.LowLatency>|Pour les applications qui ont des opérations de courte durée pour lesquelles le temps est important, et durant lesquelles les interruptions du garbage collector pourraient provoquer des perturbations. Par exemple, les applications qui rendent des animations ou des fonctions d’acquisition de données.|
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|Pour les applications qui ont des opérations pour lesquelles le temps est important, pendant une durée définie mais potentiellement longue durant laquelle les interruptions du garbage collector pourraient provoquer des perturbations. Par exemple, les applications nécessitant des temps de réponse rapides en raison du changement des données de marché pendant les heures de négociation.<br /><br />Ce mode augmente davantage la taille du tas managé que les autres modes. Parce qu'il ne compacte pas le tas managé, une fragmentation plus importante est possible. Assurez-vous que suffisamment de mémoire est disponible.|

## <a name="guidelines-for-using-low-latency"></a>Lignes directrices pour l’utilisation d’une faible latence

Lorsque vous utilisez le mode [GCLatencyMode.LowLatency,](xref:System.Runtime.GCLatencyMode.LowLatency) tenez compte des lignes directrices suivantes :

- Choisissez une période aussi courte que possible pour la faible latence.

- Évitez d'allouer de grandes quantités de mémoire pendant les périodes de faible latence. Vous pouvez recevoir des notifications de mémoire insuffisante, car le garbage collection récupère moins d'objets.

- En mode de latence, minimisez le nombre de nouvelles allocations, en particulier les allocations sur le tas de gros objets et les objets épinglés.

- N'oubliez pas les threads qui peuvent être à l'origine d'allocations. Étant <xref:System.Runtime.GCSettings.LatencyMode%2A> donné que le paramètre de propriété est à l’échelle du processus, <xref:System.OutOfMemoryException> des exceptions peuvent être générées sur n’importe quel thread qui est alloué.

- Enveloppez le code de latence faible dans les régions d’exécution limitées. Pour plus d’informations, voir [Régions d’exécution contrainte](../../../docs/framework/performance/constrained-execution-regions.md).

- Vous pouvez forcer les collections de génération 2 pendant une période de latence basse en appelant la méthode <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType>.

## <a name="see-also"></a>Voir aussi

- <xref:System.GC?displayProperty=nameWithType>
- [Collections forcées](../../../docs/standard/garbage-collection/induced.md)
- [Garbage collection](../../../docs/standard/garbage-collection/index.md)
