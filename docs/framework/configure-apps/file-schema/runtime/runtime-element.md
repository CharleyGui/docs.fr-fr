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
ms.openlocfilehash: aca5a161e0b2b913951a689620f8975f5c70f19f
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489389"
---
# <a name="runtime-element"></a>\<runtime > élément
Fournit des informations utilisées par le common language runtime pour configurer des applications.  
  
 \<configuration>  
\<runtime>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<runtime>  
</runtime>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent les éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<alwaysFlowImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)|Spécifie que l’identité Windows est toujours transmise entre des points asynchrones, indépendamment du mode d’emprunt d’identité.|  
|[\<AppContextSwitchOverrides>](../../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)|Définit un ou plusieurs commutateurs utilisés par la classe <xref:System.AppContext> pour fournir un mécanisme d’annulation d’abonnement aux nouvelles fonctionnalités.|  
|[\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)|Spécifie l’assembly qui fournit le Gestionnaire du domaine d’application par défaut du processus.|  
|[\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)|Spécifie le type qui sert de Gestionnaire de domaine d’application au domaine d’application par défaut.|  
|[\<appDomainResourceMonitoring>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)|Demande au runtime de collecter des statistiques sur tous les domaines d’application du processus sur toute sa durée.|  
|[\<assemblyBinding>](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)|Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.|  
|[\<bypassTrustedAppStrongNames>](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)|Indique s’il faut ignorer la vérification de nom fort pour les assemblys de confiance.|  
|[\<CompatSortNLSVersion>](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)|Spécifie que le runtime doit utiliser le comportement de tri hérité lors des comparaisons de chaînes.|  
|[\<developmentMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)|Indique si le runtime recherche des assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.|  
|[\<disableCachingBindingFailures>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)|Spécifie si la mise en cache des échecs de liaison, qui est le comportement par défaut dans le .NET Framework version 2.0, est désactivé.|  
|[\<disableCommitThreadStack>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)|Spécifie si la pile des threads complète est validée quand un thread est démarré.|  
|[\<disableFusionUpdatesFromADManager>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)|Indique si le comportement par défaut, qui consiste à permettre à l’hôte du runtime de remplacer les paramètres de configuration d’un domaine d’application, est désactivé.|  
|[\<EnableAmPmParseAdjustment>](../../../../../docs/framework/configure-apps/file-schema/runtime/enableampmparseadjustment-element.md)|Détermine si les méthodes d’analyse de la date et de l’heure utilisent un ensemble de règles ajusté pour analyser des chaînes de date qui contiennent uniquement un jour, un mois, une heure et un indicateur matin/après-midi.|  
|[\<enforceFIPSPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)|Indique s’il faut appliquer la condition de configuration d’ordinateur selon laquelle les algorithmes de chiffrement doivent être conformes aux normes FIPS (Federal Information Processing Standard).|  
|[\<etwEnable>](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)|Indique s’il faut activer le Suivi d’événements pour Windows (ETW) pour les événements du common language runtime.|  
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)|Indique si PerfCounter.dll utilise le paramètre de Registre CategoryOptions dans une application.NET Framework version 1.1 pour déterminer s’il faut charger des données du compteur de performance à partir de la mémoire globale ou de la mémoire partagée propre à la catégorie.|  
|[\<gcAllowVeryLargeObjects>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)|Sur les plateformes 64 bits, autorise les tableaux dont la taille totale est supérieure à 2 gigaoctets (Go).|  
|[\<gcConcurrent>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)|Spécifie si le common language runtime exécute le garbage collection simultanément.|  
|[\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)|Indique si le garbage collection prend en charge plusieurs groupes de processeurs.|  
|[\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)|Spécifie si le common language runtime exécute le garbage collection côté serveur.|  
|[\<generatePublisherEvidence>](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)|Indique si le runtime utilise la stratégie d’éditeur de sécurité d’accès du code (CAS).|  
|[\<legacyCorruptedStateExceptionsPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)|Indique si le runtime permet au code managé d’intercepter les violations d’accès et d’autres exceptions d’état endommagé.|  
|[\<legacyImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)|Spécifie que l’identité Windows n’est pas transmise entre des points asynchrones, indépendamment des paramètres de flux du contexte d’exécution sur le thread actif.|  
|[\<loadfromRemoteSources>](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)|Indique si les assemblys de sources distantes sont chargés avec une confiance totale.|  
|[<NetFx40_LegacySecurityPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)|Indique si le runtime utilise la stratégie héritée de sécurité d’accès du code (CAS).|  
|[<NetFx40_PInvokeStackResilience>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)|Indique si le runtime corrige automatiquement les déclarations incorrectes d’appel de code non managé à l’exécution, au prix de transitions plus lentes entre le code managé et le code non managé.|  
|[<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)|Spécifie si le runtime utilise une quantité de mémoire fixe pour calculer les codes de hachage pour la méthode <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> .|  
|[\<PreferComInsteadOfRemoting>](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)|Spécifie que le runtime utilisera COM Interop au lieu de la communication à distance au-delà des limites du domaine d’application.|  
|[\<relativeBindForResources>](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)|Optimise la sonde pour les assemblys satellites.|  
|[\<shadowCopyVerifyByTimeStamp>](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)|Spécifie si les copies fantômes utilisent le comportement de démarrage par défaut introduit dans le .NET Framework 4 ou rétablit le comportement de démarrage des versions antérieures du .NET Framework.|  
|[\<supportPortability>](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)|Spécifie qu’une application peut référencer le même assembly dans deux implémentations différentes du .NET Framework, en désactivant le comportement par défaut qui traite les assemblys de façon équivalente à des fins de portabilité des applications.|  
|[\<system.runtime.caching>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|Fournit des informations de configuration pour le cache d’objets en mémoire par défaut.|  
|[<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)|Indique si le runtime distribue les threads managés entre tous les groupes de processeurs.|  
|[\<ThrowUnobservedTaskExceptions>](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)|Indique si les exceptions de tâches non gérées doivent arrêter un processus en cours d’exécution.|  
|[<TimeSpan_LegacyFormatMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/timespan-legacyformatmode-element.md)|Indique si le runtime utilise la mise en forme héritée pour les valeurs <xref:System.TimeSpan>.|  
|[\<useLegacyJit>](../../../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)|Détermine si le common language runtime utilise le compilateur JIT 64 bits hérité pour la compilation juste-à-temps.|  
|[\<UseRandomizedStringHashAlgorithm>](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)|Indique si le runtime calcule les codes de hachage des chaînes domaine d’application par domaine d’application.|  
|[\<UseSmallInternalThreadStacks>](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)|Demande que le runtime utilise des tailles de pile explicites lorsqu’il crée certains threads utilisés en interne, plutôt que la taille de pile par défaut.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
  
## <a name="remarks"></a>Notes  
 Les éléments enfants dans le [ \<runtime >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section d’un fichier de configuration sont utilisés par le common language runtime pour configurer la façon dont une application s’exécute. Par exemple, le [ \<< gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) élément détermine si le garbage collector utilise le garbage collection de station de travail ou de garbage collection côté serveur, le [ \< UseRandomizedStringHashAlgorithm >](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md) élément détermine si le common language runtime calcule les codes de hachage pour la chaîne par application ou par domaine d’application et le `AppContextSwitchOverrides` élément permet aux utilisateurs de bibliothèque pour accepter ou refuser la fonctionnalité modifiée fournie par une bibliothèque.  
  
 Les éléments dans le [ \<runtime >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section sont lus automatiquement par le common language runtime au démarrage de l’application. Vous pouvez également définir le fichier de configuration pour un domaine d’application non-par défaut en fournissant son nom par le <xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType> propriété ; ses paramètres sont lus automatiquement lorsque le domaine d’application est chargé. Vous devez rarement, voire jamais, ont besoin de lire directement les paramètres dans le [ \<runtime >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section dans le fichier de configuration de votre application.  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)
