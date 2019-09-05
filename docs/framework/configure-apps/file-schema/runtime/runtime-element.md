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
ms.openlocfilehash: e703b9739ea93d3c7bf08371bc264bbdcb05b716
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252327"
---
# <a name="runtime-element"></a>\<Élément > du Runtime

Fournit des informations utilisées par le common language runtime pour configurer des applications.

[ **\<configuration>** ](../configuration-element.md)  
&nbsp;&nbsp; **\<runtime>**  

## <a name="syntax"></a>Syntaxe

```xml
<runtime>
</runtime>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les éléments enfants et parents.

### <a name="attributes"></a>Attributs

Aucun.

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
|[\<CompatSortNLSVersion>](compatsortnlsversion-element.md)|Spécifie que le runtime doit utiliser le comportement de tri hérité lors de l’exécution de comparaisons de chaînes.|
|[\<developmentMode>](developmentmode-element.md)|Indique si le runtime recherche des assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.|
|[\<disableCachingBindingFailures>](disablecachingbindingfailures-element.md)|Spécifie si la mise en cache des échecs de liaison, qui est le comportement par défaut dans la .NET Framework version 2,0, est désactivée.|
|[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)|Spécifie si la pile des threads complète est validée quand un thread est démarré.|
|[\<disableFusionUpdatesFromADManager>](disablefusionupdatesfromadmanager-element.md)|Indique si le comportement par défaut, qui consiste à permettre à l’hôte du runtime de remplacer les paramètres de configuration d’un domaine d’application, est désactivé.|
|[\<EnableAmPmParseAdjustment>](enableampmparseadjustment-element.md)|Détermine si les méthodes d’analyse de la date et de l’heure utilisent un ensemble de règles ajusté pour analyser des chaînes de date qui contiennent uniquement un jour, un mois, une heure et un indicateur matin/après-midi.|
|[\<enforceFIPSPolicy>](enforcefipspolicy-element.md)|Indique s’il faut appliquer la condition de configuration d’ordinateur selon laquelle les algorithmes de chiffrement doivent être conformes aux normes FIPS (Federal Information Processing Standard).|
|[\<etwEnable>](etwenable-element.md)|Indique s’il faut activer le Suivi d’événements pour Windows (ETW) pour les événements du common language runtime.|
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](forceperformancecounteruniquesharedmemoryreads-element.md)|Indique si PerfCounter.dll utilise le paramètre de Registre CategoryOptions dans une application.NET Framework version 1.1 pour déterminer s’il faut charger des données du compteur de performance à partir de la mémoire globale ou de la mémoire partagée propre à la catégorie.|
|[\<gcAllowVeryLargeObjects>](gcallowverylargeobjects-element.md)|Sur les plateformes 64 bits, autorise les tableaux dont la taille totale est supérieure à 2 gigaoctets (Go).|
|[\<gcConcurrent>](gcconcurrent-element.md)|Spécifie si l’common language runtime s’exécute garbage collection simultanément.|
|[\<GCCpuGroup>](gccpugroup-element.md)|Indique si le garbage collection prend en charge plusieurs groupes de processeurs.|
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
|[\<shadowCopyVerifyByTimeStamp>](shadowcopyverifybytimestamp-element.md)|Spécifie si les clichés instantanés utilisent le comportement de démarrage par défaut introduit dans le .NET Framework 4, ou repassent au comportement de démarrage des versions antérieures du .NET Framework.|
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

Les éléments enfants de la [ \<section > du Runtime](runtime-element.md) d’un fichier de configuration sont utilisés par le Common Language Runtime pour configurer le mode d’exécution d’une application. Par exemple, l' [ \<élément gcServer >](gcserver-element.md) détermine si le garbage collector utilise des garbage collection de station de travail ou de serveur garbage collection, l’élément de [ \<> UseRandomizedStringHashAlgorithm](userandomizedstringhashalgorithm-element.md) détermine si le Common Language Runtime calcule des codes de hachage pour une chaîne par application ou par domaine d’application, et l’élément permet `AppContextSwitchOverrides` aux utilisateurs de la bibliothèque d’accepter ou de refuser les fonctionnalités modifiées fournies par une bibliothèque.

Les éléments de la [ \<section > du Runtime](runtime-element.md) sont lus automatiquement par le Common Language Runtime au démarrage de l’application. Vous pouvez également définir le fichier de configuration pour un domaine d’application non défini par défaut en fournissant son nom <xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType> à la propriété ; ses paramètres sont lus automatiquement lorsque le domaine d’application est chargé. Vous devriez rarement, voire jamais, avoir besoin de lire directement les paramètres dans la [ \<section > du Runtime](runtime-element.md) dans le fichier de configuration de votre application.

## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
