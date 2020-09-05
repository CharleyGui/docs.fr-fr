---
title: Schéma des paramètres d'exécution
ms.date: 03/30/2017
helpviewer_keywords:
- schema runtime settings
- configuration schema [.NET Framework], runtime settings
- runtime settings schema
ms.assetid: f04816ab-110d-4e28-9283-845d6d9a4a68
ms.openlocfilehash: 1797afe3e6347da1aef916d13be7678b7b8d4acf
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89495171"
---
# <a name="run-time-settings-schema"></a>Schéma des paramètres d’exécution

Les paramètres d’exécution sont utilisés par le common language runtime pour configurer les applications qui ciblent le .NET Framework.

## <a name="the-runtime-section-and-its-parent-and-child-elements"></a>La \<runtime> section et ses éléments parents et enfants

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<alwaysFlowImpersonationPolicy>](alwaysflowimpersonationpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<AppContextSwitchOverrides>](appcontextswitchoverrides-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainManagerType>](appdomainmanagertype-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainResourceMonitoring>](appdomainresourcemonitoring-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<assemblyBinding>](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<dependentAssembly>](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<assemblyIdentity>](assemblyidentity-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<bindingRedirect>](bindingredirect-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<codeBase>](codebase-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<publisherPolicy>](publisherpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<probing>](probing-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<qualifyAssembly>](qualifyassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<supportPortability>](supportportability-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<bypassTrustedAppStrongNames>](bypasstrustedappstrongnames-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<CompatSortNLSVersion>](compatsortnlsversion-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<developmentMode>](developmentmode-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableCachingBindingFailures>](disablecachingbindingfailures-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableFusionUpdatesFromADManager>](disablefusionupdatesfromadmanager-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<EnableAmPmParseAdjustment>](enableampmparseadjustment-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<enforceFIPSPolicy>](enforcefipspolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<etwEnable>](etwenable-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<forcePerformanceCounterUniqueSharedMemoryReads>](forceperformancecounteruniquesharedmemoryreads-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcAllowVeryLargeObjects>](gcallowverylargeobjects-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcConcurrent>](gcconcurrent-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCCpuGroup>](gccpugroup-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCHeapAffinitizeMask>](gcheapaffinitizemask-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCHeapCount>](gcheapcount-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCLOHThreshold>](gclohthreshold-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCNoAffinitize>](gcnoaffinitize-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcServer>](gcserver-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<generatePublisherEvidence>](generatepublisherevidence-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<legacyCorruptedStateExceptionsPolicy>](legacycorruptedstateexceptionspolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<legacyImpersonationPolicy>](legacyimpersonationpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<loadfromRemoteSources>](loadfromremotesources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx40_LegacySecurityPolicy>](netfx40-legacysecuritypolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx40_PInvokeStackResilience>](netfx40-pinvokestackresilience-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](netfx45-cultureawarecomparergethashcode-longstrings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<PreferComInsteadOfManagedRemoting>](prefercominsteadofmanagedremoting-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<relativeBindForResources>](relativebindforresources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<shadowCopyVerifyByTimeStamp>](shadowcopyverifybytimestamp-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<ThrowUnobservedTaskExceptions>](throwunobservedtaskexceptions-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<TimeSpan_LegacyFormatMode>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<useLegacyJit>](uselegacyjit-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<UseSmallInternalThreadStacks>](usesmallinternalthreadstacks-element.md)\
&nbsp;&nbsp;[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<memoryCache>](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<namedCaches>](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<add>](add-element-for-namedcaches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clear>](clear-element-for-namedcaches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<remove>](remove-element-for-namedcaches.md)

## <a name="alphabetical-list-of-runtime-elements"></a>Liste alphabétique des \<runtime> éléments

|Élément|Description|
|-------------|-----------------|
|[\<add>](add-element-for-namedcaches.md)|Ajoute un cache nommé à la collection `namedCaches` d’un cache mémoire.|
|[\<alwaysFlowImpersonationPolicy>](alwaysflowimpersonationpolicy-element.md)|Spécifie que l’identité Windows est toujours transmise entre des points asynchrones, indépendamment du mode d’emprunt d’identité.|
|[\<AppContextSwitchOverrides>](appcontextswitchoverrides-element.md)|Définit un ou plusieurs commutateurs utilisés par la classe <xref:System.AppContext> pour fournir un mécanisme d’annulation d’abonnement aux nouvelles fonctionnalités.|
|[\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md)|Spécifie l’assembly qui fournit le Gestionnaire du domaine d’application par défaut du processus.|
|[\<appDomainManagerType>](appdomainmanagertype-element.md)|Spécifie le type qui sert de Gestionnaire de domaine d’application au domaine d’application par défaut.|
|[\<appDomainResourceMonitoring>](appdomainresourcemonitoring-element.md)|Demande au runtime de collecter des statistiques sur tous les domaines d’application du processus sur toute sa durée.|
|[\<assemblyBinding>](assemblybinding-element-for-runtime.md)|Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.|
|[\<assemblyIdentity>](assemblyidentity-element-for-runtime.md)|Contient les informations d’identification d’un assembly.|
|[\<bindingRedirect>](bindingredirect-element.md)|Redirige une version d'assembly vers une autre.|
|[\<bypassTrustedAppStrongNames>](bypasstrustedappstrongnames-element.md)|Indique s’il faut ignorer la vérification de nom fort pour les assemblys de confiance.|
|[\<clear>](clear-element-for-namedcaches.md)|Efface la collection `namedCaches` pour un cache mémoire.|
|[\<codeBase>](codebase-element.md)|Spécifie l’endroit où le runtime peut trouver un assembly.|
|[\<CompatSortNLSVersion>](compatsortnlsversion-element.md)|Spécifie que le runtime doit utiliser un comportement de tri hérité lors des comparaisons de chaînes.|
|[\<dependentAssembly>](dependentassembly-element.md)|Encapsule la stratégie de liaisons et l’emplacement de chaque assembly.|
|[\<developmentMode>](developmentmode-element.md)|Indique si le runtime recherche des assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.|
|[\<disableCachingBindingFailures>](disablecachingbindingfailures-element.md)|Spécifie si la mise en cache des échecs de liaison, qui est le comportement par défaut dans la .NET Framework 2,0, est désactivée.|
|[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)|Indique si la totalité de la pile des threads est validée au démarrage d’un thread.|
|[\<disableFusionUpdatesFromADManager>](disablefusionupdatesfromadmanager-element.md)|Indique si le comportement par défaut, qui consiste à permettre à l’hôte du runtime de remplacer les paramètres de configuration d’un domaine d’application, est désactivé.|
|[\<EnableAmPmParseAdjustment>](enableampmparseadjustment-element.md)|Détermine si les méthodes d’analyse de la date et de l’heure utilisent un ensemble de règles ajusté pour analyser des chaînes de date qui contiennent uniquement un jour, un mois, une heure et un indicateur matin/après-midi.|
|[\<enforceFIPSPolicy>](enforcefipspolicy-element.md)|Indique s’il faut appliquer la condition de configuration d’ordinateur selon laquelle les algorithmes de chiffrement doivent être conformes aux normes FIPS (Federal Information Processing Standard).|
|[\<etwEnable>](etwenable-element.md)|Indique s’il faut activer le Suivi d’événements pour Windows (ETW) pour les événements du common language runtime.|
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](forceperformancecounteruniquesharedmemoryreads-element.md)|Indique si PerfCounter.dll utilise le paramètre de Registre CategoryOptions dans une application.NET Framework version 1.1 pour déterminer s’il faut charger des données du compteur de performance à partir de la mémoire globale ou de la mémoire partagée propre à la catégorie.|
|[\<gcAllowVeryLargeObjects>](gcallowverylargeobjects-element.md)|Sur les plateformes 64 bits, autorise les tableaux dont la taille totale est supérieure à 2 gigaoctets (Go).|
|[\<gcConcurrent>](gcconcurrent-element.md)|Spécifie si le runtime exécute l’opération garbage collection simultanément.|
|[\<GCCpuGroup>](gccpugroup-element.md)|Indique si le garbage collection prend en charge plusieurs groupes de processeurs.|
|[\<GCHeapAffinitizeMask>](gcheapaffinitizemask-element.md)|Définit l’affinité entre les tas GC et les processeurs individuels.|
|[\<GCHeapCount>](gcheapcount-element.md)|Spécifie le nombre de segments/threads à utiliser pour le garbage collection serveur.  |
|[\<GCLOHThreshold>](gclohthreshold-element.md)|Spécifie la taille du seuil qui amène les objets sur le tas d’objets volumineux (LOH).|
|[\<GCNoAffinitize>](gcnoaffinitize-element.md)|Spécifie s’il faut ou non affinité les threads GC du serveur avec des processeurs.|
|[\<gcServer>](gcserver-element.md)|Spécifie si le common language runtime exécute le garbage collection côté serveur.|
|[\<generatePublisherEvidence>](generatepublisherevidence-element.md)|Indique si le runtime utilise la stratégie d’éditeur de sécurité d’accès du code (CAS).|
|[\<legacyCorruptedStateExceptionsPolicy>](legacycorruptedstateexceptionspolicy-element.md)|Indique si le runtime permet au code managé d’intercepter les violations d’accès et d’autres exceptions d’état endommagé.|
|[\<legacyImpersonationPolicy>](legacyimpersonationpolicy-element.md)|Spécifie que l’identité Windows n’est pas transmise entre des points asynchrones, indépendamment des paramètres de flux du contexte d’exécution sur le thread actif.|
|[\<loadfromRemoteSources>](loadfromremotesources-element.md)|Indique si les assemblys de sources distantes sont chargés avec une confiance totale.|
|[\<memoryCache>](memorycache-element-cache-settings.md)|Définit un élément qui est utilisé pour configurer un cache basé sur la classe <xref:System.Runtime.Caching.MemoryCache> .|
|[\<namedCaches>](namedcaches-element-cache-settings.md)|Contient une collection de paramètres de configuration pour l’instance `namedCache` .|
|[\<NetFx40_LegacySecurityPolicy>](netfx40-legacysecuritypolicy-element.md)|Indique si le runtime utilise la stratégie héritée de sécurité d’accès du code (CAS).|
|[\<NetFx40_PInvokeStackResilience>](netfx40-pinvokestackresilience-element.md)|Indique si le runtime corrige automatiquement les déclarations incorrectes d’appel de code non managé à l’exécution, au prix de transitions plus lentes entre le code managé et le code non managé.|
|[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](netfx45-cultureawarecomparergethashcode-longstrings-element.md)|Spécifie si le runtime utilise une quantité de mémoire fixe pour calculer les codes de hachage pour la méthode <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> .|
|[\<PreferComInsteadOfManagedRemoting>](prefercominsteadofmanagedremoting-element.md)|Spécifie que le runtime utilisera COM Interop au lieu de la communication à distance au-delà des limites du domaine d’application.|
|[\<probing>](probing-element.md)|Spécifie les sous-répertoires interrogés par le runtime lors du chargement des assemblys.|
|[\<publisherPolicy>](publisherpolicy-element.md)|Spécifie si le runtime applique la stratégie de l'éditeur.|
|[\<qualifyAssembly>](qualifyassembly-element.md)|Spécifie le nom complet de l'assembly qui doit être chargé dynamiquement quand un nom partiel est utilisé.|
|[\<relativeBindForResources>](relativebindforresources-element.md)|Optimise la sonde pour les assemblys satellites.|
|[\<remove>](remove-element-for-namedcaches.md)|Supprime une entité de cache nommé de la collection `namedCaches` d’un cache mémoire.|
|[\<runtime>](runtime-element.md)|Contient des informations sur les liaisons d’assembly et le comportement du garbage collection.|
|[\<shadowCopyTimeStampVerification>](shadowcopyverifybytimestamp-element.md)|Spécifie si les clichés instantanés utilisent le comportement de démarrage par défaut introduit dans le .NET Framework 4, ou repassent au comportement de démarrage des versions antérieures du .NET Framework.|
|[\<supportPortability>](supportportability-element.md)|Spécifie qu’une application peut référencer le même assembly dans deux implémentations différentes du .NET Framework, en désactivant le comportement par défaut qui traite les assemblys de façon équivalente à des fins de portabilité des applications.|
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|Fournit des informations de configuration pour le cache d’objets en mémoire par défaut.|
|[\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md)|Indique si le runtime distribue les threads managés entre tous les groupes de processeurs.|
|[\<ThrowUnobservedTaskExceptions>](throwunobservedtaskexceptions-element.md)|Indique si les exceptions de tâches non gérées doivent arrêter un processus en cours d’exécution.|
|[\<TimeSpan_LegacyFormatMode>](runtime-element.md)|Indique si le runtime utilise la mise en forme héritée pour les valeurs <xref:System.TimeSpan>.|
|[\<useLegacyJit>](uselegacyjit-element.md)|Détermine si le common language runtime utilise le compilateur JIT 64 bits hérité pour la compilation juste-à-temps.|
|[\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md)|Indique si le runtime calcule les codes de hachage des chaînes domaine d’application par domaine d’application.|
|[\<UseSmallInternalThreadStacks>](usesmallinternalthreadstacks-element.md)|Demande que le runtime utilise des tailles de pile explicites lorsqu’il crée certains threads utilisés en interne, plutôt que la taille de pile par défaut.|

## <a name="see-also"></a>Voir aussi

- [Schéma des fichiers de configuration](../index.md)
- [Pour désactiver les garbage collection simultanées](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [Redirection des versions d'assemblys](../../redirect-assembly-versions.md)
