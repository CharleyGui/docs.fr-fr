---
title: Analyse de ressource de domaine d'application
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- monitoring managed memory use by application domain
- application domains, memory use
- memory use, monitoring
- application domains, resource monitoring
ms.assetid: 318bedf8-7f35-4f00-b34a-2b7b8e3fa315
ms.openlocfilehash: 54e300bef1818fd08f27d7920eec68ee1f2c45bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141381"
---
# <a name="application-domain-resource-monitoring"></a>Analyse de ressource de domaine d'application

L'analyse de ressource de domaine d'application (ARM) permet aux hôtes de contrôler l'utilisation de l'UC et de la mémoire par domaine d'application. Il est utile pour les ordinateurs hôtes comme ASP.NET qui utilisent de nombreux domaines d’application dans un processus à long terme. L'hôte peut décharger le domaine d'application d'une application qui affecte de façon défavorable les performances de l'ensemble du processus, mais uniquement s'il peut identifier l'application problématique. ARM fournit des informations qui peuvent être utilisées pour faciliter la prise de telles décisions.

Par exemple, un service d’hébergement peut avoir de nombreuses applications s’exécutant sur un serveur ASP.NET. Si une application du processus commence à consommer trop de mémoire ou trop de temps processeur, le service d'hébergement peut utiliser ARM pour identifier le domaine d'application qui provoque le problème.

ARM est suffisamment léger pour être utilisé dans des applications actives. Vous pouvez accéder aux informations à l’aide du suivi d’événements pour Windows (ETW) ou directement via des API managées ou natives.

## <a name="enabling-resource-monitoring"></a>Activation de l’analyse des ressources

ARM peut être activé de quatre façons : en fournissant un fichier de configuration lorsque le Common Language Runtime (CLR) est démarré, en utilisant une API d'hébergement non managée, en utilisant du code managé ou en écoutant des événements ETW ARM.

Dès que ARM est activé, il commence à collecter des données sur tous les domaines d'application du processus. Si un domaine d'application a été créé avant l'activation de ARM, les données cumulatives démarrent avec l'activation de ARM, pas au moment de la création du domaine d'application. Une fois activé, ARM ne peut pas être désactivé.

- Vous pouvez activer ARM à la startup CLR en ajoutant [ \<l’appDomainResourceMonitoring](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)>`true`élément au fichier de configuration, et en définissant l’attribut `enabled` à . La valeur `false` (valeur par défaut) signifie uniquement que ARM n'est pas activé au démarrage. Vous pouvez l'activer ultérieurement à l'aide de l'un des autres mécanismes d'activation.

- L’hôte peut activer ARM en demandant l’interface d’hébergement [ICLRAppDomainResourceMonitor](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md). Une fois cette interface obtenue avec succès, ARM est activé.

- Un code managé peut activer ARM en définissant la propriété statique (`Shared` en Visual Basic) <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> sur `true`. Une fois la propriété définie, ARM est activé.

- Vous pouvez activer ARM après le démarrage en écoutant les événements ETW. ARM est activé et commence à déclencher des événements pour tous les domaines d'application lorsque vous activez le fournisseur public `Microsoft-Windows-DotNETRuntime` à l’aide du mot clé `AppDomainResourceManagementKeyword`. Pour mettre en corrélation des données avec les domaines d'application et les threads, vous devez également activer le fournisseur `Microsoft-Windows-DotNETRuntimeRundown` à l’aide du mot clé `ThreadingKeyword`.

## <a name="using-arm"></a>Utilisation d’ARM

ARM fournit le temps processeur total utilisé par un domaine d’application ainsi que trois types d’informations concernant l’utilisation de la mémoire.

- **Temps processeur total pour un domaine d'application, en secondes** : calculé en additionnant les temps de thread signalés par le système d'exploitation pour tous les threads qui ont passé du temps à s'exécuter dans le domaine d'application pendant leur durée de vie. Les threads bloqués ou en veille n'utilisent pas de temps processeur. Lorsqu'un thread appelle en code natif, le temps que le thread passe en code natif est inclus dans le nombre pour le domaine d'application où l'appel a été passé.

  - API managée : propriété <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>.

  - API d’hébergement : méthode [ICLRAppDomainResourceMonitor::GetCurrentCpuTime](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md).

  - Événements ETW : événements `ThreadCreated`, `ThreadAppDomainEnter` et `ThreadTerminated`. Pour plus d’informations sur les fournisseurs et les mots clés, consultez « Événements de contrôle des ressources AppDomain » dans [Événements ETW du CLR](../../../docs/framework/performance/clr-etw-events.md).

- **Allocations managées totales faites par un domaine d'application pendant sa durée de vie, en octets** : les allocations totales ne reflètent pas toujours l'utilisation de la mémoire par un domaine d'application, car les objets alloués peuvent être éphémères. Toutefois, si une application alloue et libère de grandes quantités d'objets, le coût des allocations peut être significatif.

  - API managée : propriété <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>.

  - API d’hébergement : méthode [ICLRAppDomainResourceMonitor::GetCurrentAllocated](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md).

  - Événements ETW : événement `AppDomainMemAllocated`, champ `Allocated`.

- **Mémoire managée, en octets, qui est référencée par un domaine d'application et qui a survécu à la collecte bloquante complète la plus récente** : ce nombre est exact uniquement après une collecte bloquante complète. (Cela contraste avec les collections simultanées, qui se produisent en arrière-plan et ne bloquent pas l’application.) Par exemple, <xref:System.GC.Collect?displayProperty=nameWithType> la surcharge de méthode provoque une collecte complète de blocage.

  - API managée : propriété <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>.

  - API d’hébergement : méthode [ICLRAppDomainResourceMonitor::GetCurrentSurvived](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md), paramètre `pAppDomainBytesSurvived`.

  - Événements ETW : événement `AppDomainMemSurvived`, champ `Survived`.

- **Mémoire managée totale, en octets, qui est référencée par le processus et qui a survécu à la collecte bloquante complète la plus récente** : la mémoire ayant survécu des domaines d'application individuels peut être comparée à ce nombre.

  - API managée : propriété <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>.

  - API d’hébergement : méthode [ICLRAppDomainResourceMonitor::GetCurrentSurvived](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md), paramètre `pTotalBytesSurvived`.

  - Événements ETW : événement `AppDomainMemSurvived`, champ `ProcessSurvived`.

### <a name="determining-when-a-full-blocking-collection-occurs"></a>Détermination d'une collecte bloquante complète

Pour déterminer quand la quantité de mémoire ayant survécu est exacte, vous devez savoir quand une collecte bloquante complète s'est produite. La méthode utilisée pour cela dépend de l'API que vous utilisez pour examiner les statistiques ARM.

#### <a name="managed-api"></a>API gérée

Si vous utilisez les propriétés de la classe <xref:System.AppDomain>, vous pouvez utiliser la méthode <xref:System.GC.RegisterForFullGCNotification%2A?displayProperty=nameWithType> afin de vous inscrire pour la notification des collectes complètes. Le seuil que vous utilisez n'est pas important, car vous attendez l'achèvement d'une collecte plutôt que l'approche d'une collecte. Vous pouvez ensuite appeler la méthode <xref:System.GC.WaitForFullGCComplete%2A?displayProperty=nameWithType>, qui se bloque jusqu'à ce qu'une collecte complète soit terminée. Vous pouvez créer un thread qui appelle la méthode dans une boucle et effectue toutes les analyses nécessaires chaque fois que la méthode est retournée.

Sinon, vous pouvez appeler la méthode <xref:System.GC.CollectionCount%2A?displayProperty=nameWithType> périodiquement pour voir si le nombre de collectes de génération 2 a augmenté. En fonction de la fréquence d'interrogation, cette technique peut ne pas fournir une indication exacte de l'occurrence d'une collecte complète.

#### <a name="hosting-api"></a>API d’hébergement

Si vous utilisez l'API d'hébergement non managée, votre hôte doit passer une implémentation de l'interface [IHostGCManager](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md) au CLR. Le CLR appelle la méthode [IHostGCManager::SuspensionEnding](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) lorsqu'il reprend l'exécution des threads suspendus pendant une collecte. Le CLR passe la génération de la collecte terminée comme un paramètre de la méthode, donc l'hôte peut déterminer si la collecte était complète ou partielle. Votre implémentation de la méthode [IHostGCManager::SuspensionEnding](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) peut lancer une requête de la mémoire ayant survécu, afin de vérifier que les nombres sont extraits dès qu'ils sont mis à jour.

## <a name="see-also"></a>Voir aussi

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [ICLRAppDomainResourceMonitor, interface](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [\<appDomainResourceMonitoring>](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [Événements ETW du CLR](../../../docs/framework/performance/clr-etw-events.md)
