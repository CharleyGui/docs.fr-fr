---
title: Interfaces d'hébergement du CLR
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
ms.openlocfilehash: 66fdd97d101f5ea53a96b996a2a60e5ed65a2701
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131971"
---
# <a name="clr-hosting-interfaces"></a>Interfaces d'hébergement du CLR
Cette section décrit les interfaces que les hôtes non managés peuvent utiliser pour intégrer le common language runtime (CLR) dans leurs applications. Les informations se rapportent à la version 2,0 de .NET Framework et aux versions ultérieures. Ces interfaces permettent à l’hôte de contrôler beaucoup plus d’aspects du runtime que ce qui était possible dans les versions 1,0 et 1,1, et offrent une intégration plus étroite entre le CLR et le modèle d’exécution de l’hôte.  
  
 Dans les versions 1,0 et 1,1 de .NET Framework, le modèle d’hébergement permettait à un hôte non géré de charger le CLR dans un processus, de configurer certains paramètres et de recevoir des notifications d’événements. Toutefois, en général, l’hôte et le CLR s’exécutaient indépendamment dans ce processus. Dans la .NET Framework version 2,0 et les versions ultérieures, les nouvelles couches d’abstraction permettent à l’hôte de fournir un grand nombre des ressources actuellement fournies par les types dans l’assembly Win32, et d’étendre l’ensemble de fonctionnalités que l’hôte peut configurer.  
  
## <a name="in-this-section"></a>Dans cette section  
 [IActionOnCLREvent, interface](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 Fournit une méthode qui exécute un rappel pour un événement inscrit.  
  
 [IApartmentCallback, interface](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 Fournit des méthodes pour effectuer des rappels dans un cloisonnement.  
  
 [IAppDomainBinding, interface](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 Fournit des méthodes pour définir la configuration au moment de l’exécution.  
  
 [ICatalogServices, interface](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 Fournit des méthodes pour les services de catalogage. (Cette interface prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement à partir de votre code.)  
  
 [ICLRAssemblyIdentityManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 Fournit des méthodes qui prennent en charge la communication entre l’hôte et le CLR sur les assemblys.  
  
 [ICLRAssemblyReferenceList, interface](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 Gère une liste d’assemblys qui sont chargés par le CLR et non par l’hôte.  
  
 [ICLRControl, interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 Fournit des méthodes pour que l’hôte ait accès à et configure divers aspects de, le CLR.  
  
 [ICLRDebugManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 Fournit des méthodes qui permettent à un hôte d’associer un ensemble de tâches à un identificateur et un nom convivial.  
  
 [ICLRErrorReportingManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 Fournit des méthodes qui permettent à l’hôte de configurer des dumps de tas personnalisés pour le rapport d’erreurs.  
  
 [ICLRGCManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 Fournit des méthodes qui permettent à un hôte d’interagir avec le système de garbage collection du CLR.  
  
 [ICLRHostBindingPolicyManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 Fournit des méthodes pour que l’hôte évalue et communique les modifications apportées aux informations de stratégie pour les assemblys.  
  
 [ICLRHostProtectionManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 Permet à l’hôte de bloquer des classes, des méthodes, des propriétés et des champs managés spécifiques de s’exécuter dans du code de confiance partielle.  
  
 [ICLRIoCompletionManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 Implémente une méthode de rappel qui permet à l’hôte de notifier le CLR de l’état des demandes d’e/s spécifiées.  
  
 [ICLRMemoryNotificationCallback, interface](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 Permet à l’hôte de signaler des conditions de sollicitation de la mémoire à l’aide d’une approche similaire à celle de la fonction `CreateMemoryResourceNotification` Win32.  
  
 [ICLROnEventManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 Fournit des méthodes qui permettent à l’hôte d’inscrire et d’annuler l’enregistrement des rappels pour les événements CLR.  
  
 [ICLRPolicyManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 Fournit des méthodes qui permettent à l’hôte de spécifier des actions de stratégie à prendre en cas d’échecs et de délais d’attente.  
  
 [ICLRProbingAssemblyEnum, interface](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 Fournit des méthodes qui permettent à l’hôte d’accéder aux identités de détection d’un assembly à l’aide des informations d’identité de l’assembly qui sont internes au CLR, sans avoir à créer ou à comprendre cette identité.  
  
 [ICLRReferenceAssemblyEnum, interface](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 Fournit des méthodes qui permettent à l’hôte de manipuler l’ensemble d’assemblys référencés par un fichier ou un flux à l’aide de données d’identité d’assembly qui sont internes au CLR, sans avoir à créer ou à comprendre ces identités.  
  
 [ICLRRuntimeHost, interface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 Fournit des fonctionnalités similaires à [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), avec une méthode supplémentaire pour définir l’interface de contrôle hôte.  
  
 [ICLRSyncManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 Fournit des méthodes permettant à l’hôte d’obtenir des informations sur les tâches demandées et de détecter les interblocages dans son implémentation de synchronisation.  
  
 [ICLRTask, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 Fournit des méthodes qui permettent à l’hôte d’effectuer des demandes du CLR ou de fournir une notification au CLR sur la tâche associée.  
  
 [ICLRTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 Fournit des méthodes qui permettent à l’hôte de demander explicitement que le CLR crée une nouvelle tâche, d’obtenir la tâche en cours d’exécution et de définir la langue géographique et la culture de la tâche.  
  
 [ICLRValidator, interface](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 Fournit des méthodes pour valider des images exécutables portables (PE) et des erreurs de validation de rapport.  
  
 [ICorConfiguration, interface](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 Fournit des méthodes pour configurer le CLR.  
  
 [ICorThreadpool, interface](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 Fournit des méthodes pour accéder au pool de threads.  
  
 [IDebuggerInfo, interface](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 Fournit des méthodes pour obtenir des informations sur l’état des services de débogage.  
  
 [IDebuggerThreadControl, interface](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 Fournit des méthodes pour notifier l’hôte concernant le blocage et le déblocage de threads par les services de débogage.  
  
 [IGCHost, interface](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 Fournit des méthodes pour obtenir des informations sur le système de garbage collection et pour contrôler certains aspects de garbage collection.  
  
 [IGCHost2, interface](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 Fournit la méthode [setgcstartuplimitsex,](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) qui permet à un hôte de définir la taille du segment garbage collection et la taille maximale du zéro de la génération du système garbage collection sur des valeurs supérieures à `DWORD`.  
  
 [IGCHostControl, interface](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 Fournit une méthode qui permet au garbage collector de demander à l’hôte de modifier les limites de la mémoire virtuelle.  
  
 [IGCThreadControl, interface](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 Fournit des méthodes pour participer à la planification des threads qui seraient sinon bloqués pour garbage collection.  
  
 [IHostAssemblyManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 Fournit des méthodes qui permettent à un hôte de spécifier des jeux d’assemblys qui doivent être chargés par le CLR ou par l’hôte.  
  
 [IHostAssemblyStore, interface](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 Fournit des méthodes qui permettent à un hôte de charger des assemblys et des modules indépendamment du CLR.  
  
 [IHostAutoEvent, interface](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 Fournit une représentation d’un événement de réinitialisation automatique implémenté par l’hôte.  
  
 [IHostControl, interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 Fournit des méthodes pour la configuration du chargement des assemblys et pour déterminer les interfaces d’hébergement que l’hôte prend en charge.  
  
 [IHostCrst, interface](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 Sert de représentation de l’hôte d’une section critique pour le Threading.  
  
 [IHostGCManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 Fournit des méthodes qui notifient l’hôte d’événements dans le mécanisme de garbage collection implémenté par le CLR.  
  
 [IHostIoCompletionManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 Fournit des méthodes qui permettent au CLR d’interagir avec les ports de terminaison d’e/s fournis par l’hôte.  
  
 [IHostMalloc, interface](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 Fournit des méthodes pour que le CLR demande des allocations affinées à partir du tas par le biais de l’hôte.  
  
 [IHostManualEvent, interface](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 Fournit l’implémentation de l’hôte d’une représentation d’un événement de réinitialisation manuelle.  
  
 [IHostMemoryManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 Fournit des méthodes pour que le CLR effectue des demandes de mémoire virtuelle par le biais de l’hôte, au lieu d’utiliser les fonctions de mémoire virtuelle Win32 standard.  
  
 [IHostPolicyManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 Fournit des méthodes qui notifient l’hôte des actions exécutées par le CLR en cas d’abandons, de délais d’attente ou d’échecs.  
  
 [IHostSecurityContext, interface](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 Permet au CLR de conserver les informations de contexte de sécurité implémentées par l’hôte.  
  
 [IHostSecurityManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 Fournit des méthodes qui permettent d’accéder au contexte de sécurité du thread en cours d’exécution et de le contrôler.  
  
 [IHostSemaphore, interface](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 Fournit une représentation d’un sémaphore implémenté par l’hôte.  
  
 [IHostSyncManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 Fournit des méthodes pour que le CLR crée des primitives de synchronisation en appelant l’hôte, au lieu d’utiliser les fonctions de synchronisation Win32.  
  
 [IHostTask, interface](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 Fournit des méthodes qui permettent au CLR de communiquer avec l’hôte pour gérer des tâches.  
  
 [IHostTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 Fournit des méthodes qui permettent au CLR d’utiliser des tâches via l’hôte au lieu d’utiliser le thread de système d’exploitation standard ou les fonctions Fiber.  
  
 [IHostThreadPoolManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 Fournit des méthodes permettant au CLR de configurer le pool de threads et de mettre en file d’attente des éléments de travail dans le pool de threads.  
  
 [IManagedObject, interface](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 Fournit des méthodes pour contrôler un objet managé.  
  
 IObjectHandle  
 Fournit une méthode pour désencapsuler les objets marshalés par valeur à partir de l’indirection.  
  
 [ITypeName, interface](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 Fournit des méthodes pour obtenir des informations de nom de type. (Cette interface prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement à partir de votre code.)  
  
 [ITypeNameBuilder, interface](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 Fournit des méthodes pour la génération d’un nom de type. (Cette interface prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement à partir de votre code.)  
  
 [ITypeNameFactory, interface](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 Fournit des méthodes pour décomposer un nom de type. (Cette interface prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement à partir de votre code.)  
  
 IValidator  
 Fournit des méthodes pour valider des images exécutables portables (PE) et des erreurs de validation de rapport.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Coclasses et interfaces d’hébergement CLR dépréciées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 Contient des rubriques qui décrivent les interfaces d’hébergement fournies dans le .NET Framework version 1,0 et 1,1.  
  
 [Interfaces d’hébergement CLR ajoutées dans .NET Framework 4 et 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 Contient des rubriques qui décrivent les interfaces d’hébergement fournies dans le .NET Framework 4.
