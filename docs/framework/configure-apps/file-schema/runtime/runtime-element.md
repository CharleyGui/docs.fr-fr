---
title: Élément <runtime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#runtime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime
helpviewer_keywords:
- <runtime> element
- runtime element
- container tags, <runtime> element
ms.assetid: 1eb2fae3-de4b-45b6-852f-517c39b751bd
ms.openlocfilehash: 3825ae7c3e35193cb835981600fe1ef83097cd2d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430461"
---
# <a name="runtime-element"></a>\<runtime> Element

Provides information used by the common language runtime to configure applications.

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;\<runtime>

## <a name="syntax"></a>Syntaxe

```xml
<runtime>
</runtime>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

The following sections describe child elements and parent elements.

### <a name="attributes"></a>Attributs

Aucun(e).

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[\<alwaysFlowImpersonationPolicy>](alwaysflowimpersonationpolicy-element.md)|Spécifie que l’identité Windows est toujours transmise entre des points asynchrones, indépendamment du mode d’emprunt d’identité.|
|[\<AppContextSwitchOverrides>](appcontextswitchoverrides-element.md)|Définit un ou plusieurs commutateurs utilisés par la classe <xref:System.AppContext> pour fournir un mécanisme d’annulation d’abonnement aux nouvelles fonctionnalités.|
|[\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md)|Spécifie l’assembly qui fournit le Gestionnaire du domaine d’application par défaut du processus.|
|[\<appDomainManagerType>](appdomainmanagertype-element.md)|Spécifie le type qui sert de Gestionnaire de domaine d’application au domaine d’application par défaut.|
|[\<appDomainResourceMonitoring>](appdomainresourcemonitoring-element.md)|Demande au runtime de collecter des statistiques sur tous les domaines d’application du processus sur toute sa durée.|
|[\<assemblyBinding>](assemblybinding-element-for-runtime.md)|Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.|
|[\<bypassTrustedAppStrongNames>](bypasstrustedappstrongnames-element.md)|Indique s’il faut ignorer la vérification de nom fort pour les assemblys de confiance.|
|[\<CompatSortNLSVersion>](compatsortnlsversion-element.md)|Specifies that the runtime should use legacy sorting behavior when performing string comparisons.|
|[\<developmentMode>](developmentmode-element.md)|Indique si le runtime recherche des assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.|
|[\<disableCachingBindingFailures>](disablecachingbindingfailures-element.md)|Specifies whether the caching of binding failures, which is the default behavior in the .NET Framework version 2.0, is disabled.|
|[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)|Spécifie si la pile des threads complète est validée quand un thread est démarré.|
|[\<disableFusionUpdatesFromADManager>](disablefusionupdatesfromadmanager-element.md)|Indique si le comportement par défaut, qui consiste à permettre à l’hôte du runtime de remplacer les paramètres de configuration d’un domaine d’application, est désactivé.|
|[\<EnableAmPmParseAdjustment>](enableampmparseadjustment-element.md)|Détermine si les méthodes d’analyse de la date et de l’heure utilisent un ensemble de règles ajusté pour analyser des chaînes de date qui contiennent uniquement un jour, un mois, une heure et un indicateur matin/après-midi.|
|[\<enforceFIPSPolicy>](enforcefipspolicy-element.md)|Indique s’il faut appliquer la condition de configuration d’ordinateur selon laquelle les algorithmes de chiffrement doivent être conformes aux normes FIPS (Federal Information Processing Standard).|
|[\<etwEnable>](etwenable-element.md)|Indique s’il faut activer le Suivi d’événements pour Windows (ETW) pour les événements du common language runtime.|
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](forceperformancecounteruniquesharedmemoryreads-element.md)|Indique si PerfCounter.dll utilise le paramètre de Registre CategoryOptions dans une application.NET Framework version 1.1 pour déterminer s’il faut charger des données du compteur de performance à partir de la mémoire globale ou de la mémoire partagée propre à la catégorie.|
|[\<gcAllowVeryLargeObjects>](gcallowverylargeobjects-element.md)|Sur les plateformes 64 bits, autorise les tableaux dont la taille totale est supérieure à 2 gigaoctets (Go).|
|[\<gcConcurrent>](gcconcurrent-element.md)|Specifies whether the common language runtime runs garbage collection concurrently.|
|[\<GCCpuGroup>](gccpugroup-element.md)|Indique si le garbage collection prend en charge plusieurs groupes de processeurs.|
|[\<GCHeapAffinitizeMask>](gcheapaffinitizemask-element.md)|Defines the affinity between garbage collection heaps and individual processors.|
|[\<GCHeapCount>](gcheapcount-element.md)|Specifies the number of heaps/threads to use for server garbage collection.|
|[\<GCLOHThreshold>](gclohthreshold-element.md)|Specifies the threshold size that causes the garbage collector to put objects on the large object heap.|
|[\<GCNoAffinitize>](gcnoaffinitize-element.md)|Specifies whether or not to affinitize server garbage collection threads with CPUs.|
|[\<gcServer>](gcserver-element.md)|Spécifie si le common language runtime exécute le garbage collection côté serveur.|
|[\<generatePublisherEvidence>](generatepublisherevidence-element.md)|Indique si le runtime utilise la stratégie d’éditeur de sécurité d’accès du code (CAS).|
|[\<legacyCorruptedStateExceptionsPolicy>](legacycorruptedstateexceptionspolicy-element.md)|Indique si le runtime permet au code managé d’intercepter les violations d’accès et d’autres exceptions d’état endommagé.|
|[\<legacyImpersonationPolicy>](legacyimpersonationpolicy-element.md)|Spécifie que l’identité Windows n’est pas transmise entre des points asynchrones, indépendamment des paramètres de flux du contexte d’exécution sur le thread actif.|
|[\<loadfromRemoteSources>](loadfromremotesources-element.md)|Indique si les assemblys de sources distantes sont chargés avec une confiance totale.|
|[\<NetFx40_LegacySecurityPolicy>](netfx40-legacysecuritypolicy-element.md)|Indique si le runtime utilise la stratégie héritée de sécurité d’accès du code (CAS).|
|[\<NetFx40_PInvokeStackResilience>](netfx40-pinvokestackresilience-element.md)|Indique si le runtime corrige automatiquement les déclarations incorrectes d’appel de code non managé à l’exécution, au prix de transitions plus lentes entre le code managé et le code non managé.|
|[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](netfx45-cultureawarecomparergethashcode-longstrings-element.md)|Spécifie si le runtime utilise une quantité de mémoire fixe pour calculer les codes de hachage pour la méthode <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> .|
|[\<PreferComInsteadOfRemoting>](prefercominsteadofmanagedremoting-element.md)|Spécifie que le runtime utilisera COM Interop au lieu de la communication à distance au-delà des limites du domaine d’application.|
|[\<relativeBindForResources>](relativebindforresources-element.md)|Optimise la sonde pour les assemblys satellites.|
|[\<shadowCopyVerifyByTimeStamp>](shadowcopyverifybytimestamp-element.md)|Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.|
|[\<supportPortability>](supportportability-element.md)|Spécifie qu’une application peut référencer le même assembly dans deux implémentations différentes du .NET Framework, en désactivant le comportement par défaut qui traite les assemblys de façon équivalente à des fins de portabilité des applications.|
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|Fournit des informations de configuration pour le cache d’objets en mémoire par défaut.|
|[\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md)|Indique si le runtime distribue les threads managés entre tous les groupes de processeurs.|
|[\<ThrowUnobservedTaskExceptions>](throwunobservedtaskexceptions-element.md)|Indique si les exceptions de tâches non gérées doivent arrêter un processus en cours d’exécution.|
|[\<TimeSpan_LegacyFormatMode>](timespan-legacyformatmode-element.md)|Indique si le runtime utilise la mise en forme héritée pour les valeurs <xref:System.TimeSpan>.|
|[\<useLegacyJit>](uselegacyjit-element.md)|Détermine si le common language runtime utilise le compilateur JIT 64 bits hérité pour la compilation juste-à-temps.|
|[\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md)|Indique si le runtime calcule les codes de hachage des chaînes domaine d’application par domaine d’application.|
|[\<UseSmallInternalThreadStacks>](usesmallinternalthreadstacks-element.md)|Demande que le runtime utilise des tailles de pile explicites lorsqu’il crée certains threads utilisés en interne, plutôt que la taille de pile par défaut.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|

## <a name="remarks"></a>Notes

The child elements in the [\<runtime>](runtime-element.md) section of a configuration file are used by the common language runtime to configure how an application executes. For example, the [\<gcServer>](gcserver-element.md) element determines whether the garbage collector uses workstation garbage collection or server garbage collection, the [\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md) element determines whether the common language runtime calculates hash codes for string on a per-application or a per-application domain basis, and the `AppContextSwitchOverrides` element allows library users to opt in or opt out of changed  functionality provided by a library.

The elements in the [\<runtime>](runtime-element.md) section are read automatically by the common language runtime at application startup. You can also define the configuration file for a non-default application domain by supplying its name to the <xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType> property; its settings are read automatically when the application domain is loaded. You should rarely, if ever, have a need to directly read the settings in the [\<runtime>](runtime-element.md) section in your application's configuration file.

## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
