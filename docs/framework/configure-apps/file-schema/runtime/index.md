---
title: Schéma des paramètres d'exécution
ms.date: 03/30/2017
helpviewer_keywords:
- schema runtime settings
- configuration schema [.NET Framework], runtime settings
- runtime settings schema
ms.assetid: f04816ab-110d-4e28-9283-845d6d9a4a68
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: caef2a1d1230f020389c6b86015702075b9fc582
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489457"
---
# <a name="runtime-settings-schema"></a>Schéma des paramètres d'exécution
Les paramètres d’exécution sont utilisés par le common language runtime pour configurer les applications qui ciblent le .NET Framework.  

## <a name="the-runtime-section-and-its-parent-and-child-elements"></a>Le \<runtime > section et ses éléments parents et enfants
  
[\<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
&nbsp;&nbsp;[\<runtime>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<alwaysFlowImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<AppContextSwitchOverrides>](../../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainResourceMonitoring>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<assemblyBinding>](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<dependentAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<assemblyIdentity>](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblyidentity-element-for-runtime.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<bindingRedirect>](../../../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<codeBase>](../../../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<probing>](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<publisherPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<qualifyAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<bypassTrustedAppStrongNames>](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<CompatSortNLSVersion>](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<developmentMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableCachingBindingFailures>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableCommitThreadStack>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableFusionUpdatesFromADManager>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<EnableAmPmParseAdjustment>](../../../../../docs/framework/configure-apps/file-schema/runtime/enableampmparseadjustment-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<enforceFIPSPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<etwEnable>](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcAllowVeryLargeObjects>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcConcurrent>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<generatePublisherEvidence>](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<legacyCorruptedStateExceptionsPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<legacyImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<loadfromRemoteSources>](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[<NetFx40_LegacySecurityPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[<NetFx40_PInvokeStackResilience>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<PreferComInsteadOfManagedRemoting>](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<relativeBindForResources>](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<shadowCopyVerifyByTimeStamp>](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<supportPortability>](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<system.runtime.caching>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<memoryCache>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<add>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clear>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<remove>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<ThrowUnobservedTaskExceptions>](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[<TimeSpan_LegacyFormatMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<useLegacyJit>](../../../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<UseRandomizedStringHashAlgorithm>](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<UseSmallInternalThreadStacks>](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)  
&nbsp;&nbsp;\<\runtime>  
\<\configuration>

## <a name="alphabetical-list-of-runtime-elements"></a>Liste alphabétique des \<runtime > éléments

|Élément|Description|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|Ajoute un cache nommé à la collection `namedCaches` d’un cache mémoire.|  
|[\<alwaysFlowImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)|Spécifie que l’identité Windows est toujours transmise entre des points asynchrones, indépendamment du mode d’emprunt d’identité.|  
|[\<AppContextSwitchOverrides>](../../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)|Définit un ou plusieurs commutateurs utilisés par la classe <xref:System.AppContext> pour fournir un mécanisme d’annulation d’abonnement aux nouvelles fonctionnalités.|  
|[\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)|Spécifie l’assembly qui fournit le Gestionnaire du domaine d’application par défaut du processus.|  
|[\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)|Spécifie le type qui sert de Gestionnaire de domaine d’application au domaine d’application par défaut.|  
|[\<appDomainResourceMonitoring>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)|Demande au runtime de collecter des statistiques sur tous les domaines d’application du processus sur toute sa durée.|  
|[\<assemblyBinding>](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)|Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.|  
|[\<assemblyIdentity>](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblyidentity-element-for-runtime.md)|Contient les informations d’identification d’un assembly.|  
|[\<bindingRedirect>](../../../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)|Redirige une version d'assembly vers une autre.|  
|[\<bypassTrustedAppStrongNames>](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)|Indique s’il faut ignorer la vérification de nom fort pour les assemblys de confiance.|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|Efface la collection `namedCaches` pour un cache mémoire.|  
|[\<codeBase>](../../../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)|Spécifie l’endroit où le runtime peut trouver un assembly.|  
|[\<CompatSortNLSVersion>](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)|Spécifie que le runtime doit utiliser un comportement de tri hérité lors des comparaisons de chaînes.|  
|[\<dependentAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)|Encapsule la stratégie de liaisons et l’emplacement de chaque assembly.|  
|[\<developmentMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)|Indique si le runtime recherche des assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.|  
|[\<disableCachingBindingFailures>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)|Indique si la mise en cache des échecs de liaison, comportement par défaut dans [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)], est désactivée.|  
|[\<disableCommitThreadStack>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)|Indique si la totalité de la pile des threads est validée au démarrage d’un thread.|  
|[\<disableFusionUpdatesFromADManager>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)|Indique si le comportement par défaut, qui consiste à permettre à l’hôte du runtime de remplacer les paramètres de configuration d’un domaine d’application, est désactivé.|  
|[\<EnableAmPmParseAdjustment>](../../../../../docs/framework/configure-apps/file-schema/runtime/enableampmparseadjustment-element.md)|Détermine si les méthodes d’analyse de la date et de l’heure utilisent un ensemble de règles ajusté pour analyser des chaînes de date qui contiennent uniquement un jour, un mois, une heure et un indicateur matin/après-midi.|  
|[\<enforceFIPSPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)|Indique s’il faut appliquer la condition de configuration d’ordinateur selon laquelle les algorithmes de chiffrement doivent être conformes aux normes FIPS (Federal Information Processing Standard).|  
|[\<etwEnable>](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)|Indique s’il faut activer le Suivi d’événements pour Windows (ETW) pour les événements du common language runtime.|  
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)|Indique si PerfCounter.dll utilise le paramètre de Registre CategoryOptions dans une application.NET Framework version 1.1 pour déterminer s’il faut charger des données du compteur de performance à partir de la mémoire globale ou de la mémoire partagée propre à la catégorie.|  
|[\<gcAllowVeryLargeObjects>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)|Sur les plateformes 64 bits, autorise les tableaux dont la taille totale est supérieure à 2 gigaoctets (Go).|  
|[\<gcConcurrent>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)|Spécifie si le runtime exécute l’opération garbage collection simultanément.|  
|[\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)|Indique si le garbage collection prend en charge plusieurs groupes de processeurs.|  
|[\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)|Spécifie si le common language runtime exécute le garbage collection côté serveur.|  
|[\<generatePublisherEvidence>](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)|Indique si le runtime utilise la stratégie d’éditeur de sécurité d’accès du code (CAS).|  
|[\<legacyCorruptedStateExceptionsPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)|Indique si le runtime permet au code managé d’intercepter les violations d’accès et d’autres exceptions d’état endommagé.|  
|[\<legacyImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)|Spécifie que l’identité Windows n’est pas transmise entre des points asynchrones, indépendamment des paramètres de flux du contexte d’exécution sur le thread actif.|  
|[\<loadfromRemoteSources>](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)|Indique si les assemblys de sources distantes sont chargés avec une confiance totale.|  
|[\<memoryCache>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|Définit un élément qui est utilisé pour configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache>.|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Contient une collection de paramètres de configuration pour l’instance `namedCache` .|  
|[<NetFx40_LegacySecurityPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)|Indique si le runtime utilise la stratégie héritée de sécurité d’accès du code (CAS).|  
|[<NetFx40_PInvokeStackResilience>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)|Indique si le runtime corrige automatiquement les déclarations incorrectes d’appel de code non managé à l’exécution, au prix de transitions plus lentes entre le code managé et le code non managé.|  
|[<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)|Spécifie si le runtime utilise une quantité de mémoire fixe pour calculer les codes de hachage pour la méthode <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>.|  
|[\<PreferComInsteadOfManagedRemoting>](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)|Spécifie que le runtime utilisera COM Interop au lieu de la communication à distance au-delà des limites du domaine d’application.|  
|[\<probing>](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)|Spécifie les sous-répertoires interrogés par le runtime lors du chargement des assemblys.|  
|[\<publisherPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)|Spécifie si le runtime applique la stratégie de l'éditeur.|  
|[\<qualifyAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)|Spécifie le nom complet de l'assembly qui doit être chargé dynamiquement quand un nom partiel est utilisé.|  
|[\<relativeBindForResources>](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)|Optimise la sonde pour les assemblys satellites.|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|Supprime une entité de cache nommé de la collection `namedCaches` d’un cache mémoire.|  
|[\<runtime>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)|Contient des informations sur les liaisons d’assembly et le comportement du garbage collection.|  
|[\<shadowCopyTimeStampVerification>](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)|Spécifie si les copies fantômes utilisent le comportement de démarrage par défaut introduit dans le .NET Framework 4 ou rétablit le comportement de démarrage des versions antérieures du .NET Framework.|  
|[\<supportPortability>](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)|Spécifie qu’une application peut référencer le même assembly dans deux implémentations différentes du .NET Framework, en désactivant le comportement par défaut qui traite les assemblys de façon équivalente à des fins de portabilité des applications.|  
|[\<system.runtime.caching>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|Fournit des informations de configuration pour le cache d’objets en mémoire par défaut.|  
|[<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)|Indique si le runtime distribue les threads managés entre tous les groupes de processeurs.|  
|[\<ThrowUnobservedTaskExceptions>](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)|Indique si les exceptions de tâches non gérées doivent arrêter un processus en cours d’exécution.|  
|[<TimeSpan_LegacyFormatMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)|Indique si le runtime utilise la mise en forme héritée pour les valeurs <xref:System.TimeSpan>.|  
|[\<useLegacyJit>](../../../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)|Détermine si le common language runtime utilise le compilateur JIT 64 bits hérité pour la compilation juste-à-temps.|  
|[\<UseRandomizedStringHashAlgorithm>](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)|Indique si le runtime calcule les codes de hachage des chaînes domaine d’application par domaine d’application.|  
|[\<UseSmallInternalThreadStacks>](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)|Demande que le runtime utilise des tailles de pile explicites lorsqu’il crée certains threads utilisés en interne, plutôt que la taille de pile par défaut.|  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Pour désactiver le garbage collection simultané](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [Redirection des versions d'assemblys](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
