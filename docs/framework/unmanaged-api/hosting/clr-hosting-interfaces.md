---
title: Interfaces d'hébergement du CLR
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
ms.openlocfilehash: e6913e18a4ff6e616f357a4ef43fb8b892264943
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616838"
---
# <a name="clr-hosting-interfaces"></a>Interfaces d'hébergement du CLR
Cette section décrit les interfaces que les hôtes non managés peuvent utiliser pour intégrer le common language runtime (CLR) dans leurs applications. Les informations se rapportent à la version 2,0 de .NET Framework et aux versions ultérieures. Ces interfaces permettent à l’hôte de contrôler beaucoup plus d’aspects du runtime que ce qui était possible dans les versions 1,0 et 1,1, et offrent une intégration plus étroite entre le CLR et le modèle d’exécution de l’hôte.  
  
 Dans les versions 1,0 et 1,1 de .NET Framework, le modèle d’hébergement permettait à un hôte non géré de charger le CLR dans un processus, de configurer certains paramètres et de recevoir des notifications d’événements. Toutefois, en général, l’hôte et le CLR s’exécutaient indépendamment dans ce processus. Dans la .NET Framework version 2,0 et les versions ultérieures, les nouvelles couches d’abstraction permettent à l’hôte de fournir un grand nombre des ressources actuellement fournies par les types dans l’assembly Win32, et d’étendre l’ensemble de fonctionnalités que l’hôte peut configurer.  
  
## <a name="in-this-section"></a>Dans cette section  
 [IActionOnCLREvent, interface](iactiononclrevent-interface.md)  
 Fournit une méthode qui exécute un rappel pour un événement inscrit.  
  
 [IApartmentCallback, interface](iapartmentcallback-interface.md)  
 Fournit des méthodes pour effectuer des rappels dans un cloisonnement.  
  
 [IAppDomainBinding, interface](iappdomainbinding-interface.md)  
 Fournit des méthodes pour définir la configuration au moment de l’exécution.  
  
 [ICatalogServices, interface](icatalogservices-interface.md)  
 Fournit des méthodes pour les services de catalogage. (Cette interface prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement à partir de votre code.)  
  
 [ICLRAssemblyIdentityManager, interface](iclrassemblyidentitymanager-interface.md)  
 Fournit des méthodes qui prennent en charge la communication entre l’hôte et le CLR sur les assemblys.  
  
 [ICLRAssemblyReferenceList, interface](iclrassemblyreferencelist-interface.md)  
 Gère une liste d’assemblys qui sont chargés par le CLR et non par l’hôte.  
  
 [ICLRControl, interface](iclrcontrol-interface.md)  
 Fournit des méthodes pour que l’hôte ait accès à et configure divers aspects de, le CLR.  
  
 [ICLRDebugManager, interface](iclrdebugmanager-interface.md)  
 Fournit des méthodes qui permettent à un hôte d’associer un ensemble de tâches à un identificateur et un nom convivial.  
  
 [ICLRErrorReportingManager, interface](iclrerrorreportingmanager-interface.md)  
 Fournit des méthodes qui permettent à l’hôte de configurer des dumps de tas personnalisés pour le rapport d’erreurs.  
  
 [ICLRGCManager, interface](iclrgcmanager-interface.md)  
 Fournit des méthodes qui permettent à un hôte d’interagir avec le système de garbage collection du CLR.  
  
 [ICLRHostBindingPolicyManager, interface](iclrhostbindingpolicymanager-interface.md)  
 Fournit des méthodes pour que l’hôte évalue et communique les modifications apportées aux informations de stratégie pour les assemblys.  
  
 [ICLRHostProtectionManager, interface](iclrhostprotectionmanager-interface.md)  
 Permet à l’hôte de bloquer des classes, des méthodes, des propriétés et des champs managés spécifiques de s’exécuter dans du code de confiance partielle.  
  
 [ICLRIoCompletionManager, interface](iclriocompletionmanager-interface.md)  
 Implémente une méthode de rappel qui permet à l’hôte de notifier le CLR de l’état des demandes d’e/s spécifiées.  
  
 [ICLRMemoryNotificationCallback, interface](iclrmemorynotificationcallback-interface.md)  
 Permet à l’hôte de signaler des conditions de sollicitation de la mémoire à l’aide d’une approche similaire à celle de la `CreateMemoryResourceNotification` fonction Win32.  
  
 [ICLROnEventManager, interface](iclroneventmanager-interface.md)  
 Fournit des méthodes qui permettent à l’hôte d’inscrire et d’annuler l’enregistrement des rappels pour les événements CLR.  
  
 [ICLRPolicyManager, interface](iclrpolicymanager-interface.md)  
 Fournit des méthodes qui permettent à l’hôte de spécifier des actions de stratégie à prendre en cas d’échecs et de délais d’attente.  
  
 [ICLRProbingAssemblyEnum, interface](iclrprobingassemblyenum-interface.md)  
 Fournit des méthodes qui permettent à l’hôte d’accéder aux identités de détection d’un assembly à l’aide des informations d’identité de l’assembly qui sont internes au CLR, sans avoir à créer ou à comprendre cette identité.  
  
 [ICLRReferenceAssemblyEnum, interface](iclrreferenceassemblyenum-interface.md)  
 Fournit des méthodes qui permettent à l’hôte de manipuler l’ensemble d’assemblys référencés par un fichier ou un flux à l’aide de données d’identité d’assembly qui sont internes au CLR, sans avoir à créer ou à comprendre ces identités.  
  
 [ICLRRuntimeHost, interface](iclrruntimehost-interface.md)  
 Fournit des fonctionnalités similaires à [ICorRuntimeHost](icorruntimehost-interface.md), avec une méthode supplémentaire pour définir l’interface de contrôle hôte.  
  
 [ICLRSyncManager, interface](iclrsyncmanager-interface.md)  
 Fournit des méthodes permettant à l’hôte d’obtenir des informations sur les tâches demandées et de détecter les interblocages dans son implémentation de synchronisation.  
  
 [ICLRTask, interface](iclrtask-interface.md)  
 Fournit des méthodes qui permettent à l’hôte d’effectuer des demandes du CLR ou de fournir une notification au CLR sur la tâche associée.  
  
 [ICLRTaskManager, interface](iclrtaskmanager-interface.md)  
 Fournit des méthodes qui permettent à l’hôte de demander explicitement que le CLR crée une nouvelle tâche, d’obtenir la tâche en cours d’exécution et de définir la langue géographique et la culture de la tâche.  
  
 [ICLRValidator, interface](iclrvalidator-interface.md)  
 Fournit des méthodes pour valider des images exécutables portables (PE) et des erreurs de validation de rapport.  
  
 [ICorConfiguration, interface](icorconfiguration-interface.md)  
 Fournit des méthodes pour configurer le CLR.  
  
 [ICorThreadpool, interface](icorthreadpool-interface.md)  
 Fournit des méthodes pour accéder au pool de threads.  
  
 [IDebuggerInfo, interface](idebuggerinfo-interface.md)  
 Fournit des méthodes pour obtenir des informations sur l’état des services de débogage.  
  
 [IDebuggerThreadControl, interface](idebuggerthreadcontrol-interface.md)  
 Fournit des méthodes pour notifier l’hôte concernant le blocage et le déblocage de threads par les services de débogage.  
  
 [IGCHost, interface](igchost-interface.md)  
 Fournit des méthodes pour obtenir des informations sur le système de garbage collection et pour contrôler certains aspects de garbage collection.  
  
 [IGCHost2, interface](igchost2-interface.md)  
 Fournit la méthode [setgcstartuplimitsex,](igchost2-setgcstartuplimitsex-method.md) qui permet à un hôte de définir la taille du segment garbage collection et la taille maximale de la génération zéro du système garbage collection sur des valeurs supérieures à `DWORD` .  
  
 [IGCHostControl, interface](igchostcontrol-interface.md)  
 Fournit une méthode qui permet au garbage collector de demander à l’hôte de modifier les limites de la mémoire virtuelle.  
  
 [IGCThreadControl, interface](igcthreadcontrol-interface.md)  
 Fournit des méthodes pour participer à la planification des threads qui seraient sinon bloqués pour garbage collection.  
  
 [IHostAssemblyManager, interface](ihostassemblymanager-interface.md)  
 Fournit des méthodes qui permettent à un hôte de spécifier des jeux d’assemblys qui doivent être chargés par le CLR ou par l’hôte.  
  
 [IHostAssemblyStore, interface](ihostassemblystore-interface.md)  
 Fournit des méthodes qui permettent à un hôte de charger des assemblys et des modules indépendamment du CLR.  
  
 [IHostAutoEvent, interface](ihostautoevent-interface.md)  
 Fournit une représentation d’un événement de réinitialisation automatique implémenté par l’hôte.  
  
 [IHostControl, interface](ihostcontrol-interface.md)  
 Fournit des méthodes pour la configuration du chargement des assemblys et pour déterminer les interfaces d’hébergement que l’hôte prend en charge.  
  
 [IHostCrst, interface](ihostcrst-interface.md)  
 Sert de représentation de l’hôte d’une section critique pour le Threading.  
  
 [IHostGCManager, interface](ihostgcmanager-interface.md)  
 Fournit des méthodes qui notifient l’hôte d’événements dans le mécanisme de garbage collection implémenté par le CLR.  
  
 [IHostIoCompletionManager, interface](ihostiocompletionmanager-interface.md)  
 Fournit des méthodes qui permettent au CLR d’interagir avec les ports de terminaison d’e/s fournis par l’hôte.  
  
 [IHostMalloc, interface](ihostmalloc-interface.md)  
 Fournit des méthodes pour que le CLR demande des allocations affinées à partir du tas par le biais de l’hôte.  
  
 [IHostManualEvent, interface](ihostmanualevent-interface.md)  
 Fournit l’implémentation de l’hôte d’une représentation d’un événement de réinitialisation manuelle.  
  
 [IHostMemoryManager, interface](ihostmemorymanager-interface.md)  
 Fournit des méthodes pour que le CLR effectue des demandes de mémoire virtuelle par le biais de l’hôte, au lieu d’utiliser les fonctions de mémoire virtuelle Win32 standard.  
  
 [IHostPolicyManager, interface](ihostpolicymanager-interface.md)  
 Fournit des méthodes qui notifient l’hôte des actions exécutées par le CLR en cas d’abandons, de délais d’attente ou d’échecs.  
  
 [IHostSecurityContext, interface](ihostsecuritycontext-interface.md)  
 Permet au CLR de conserver les informations de contexte de sécurité implémentées par l’hôte.  
  
 [IHostSecurityManager, interface](ihostsecuritymanager-interface.md)  
 Fournit des méthodes qui permettent d’accéder au contexte de sécurité du thread en cours d’exécution et de le contrôler.  
  
 [IHostSemaphore, interface](ihostsemaphore-interface.md)  
 Fournit une représentation d’un sémaphore implémenté par l’hôte.  
  
 [IHostSyncManager, interface](ihostsyncmanager-interface.md)  
 Fournit des méthodes pour que le CLR crée des primitives de synchronisation en appelant l’hôte, au lieu d’utiliser les fonctions de synchronisation Win32.  
  
 [IHostTask, interface](ihosttask-interface.md)  
 Fournit des méthodes qui permettent au CLR de communiquer avec l’hôte pour gérer des tâches.  
  
 [IHostTaskManager, interface](ihosttaskmanager-interface.md)  
 Fournit des méthodes qui permettent au CLR d’utiliser des tâches via l’hôte au lieu d’utiliser le thread de système d’exploitation standard ou les fonctions Fiber.  
  
 [IHostThreadPoolManager, interface](ihostthreadpoolmanager-interface.md)  
 Fournit des méthodes permettant au CLR de configurer le pool de threads et de mettre en file d’attente des éléments de travail dans le pool de threads.  
  
 [IManagedObject, interface](imanagedobject-interface.md)  
 Fournit des méthodes pour contrôler un objet managé.  
  
 IObjectHandle  
 Fournit une méthode pour désencapsuler les objets marshalés par valeur à partir de l’indirection.  
  
 [ITypeName, interface](itypename-interface.md)  
 Fournit des méthodes pour obtenir des informations de nom de type. (Cette interface prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement à partir de votre code.)  
  
 [ITypeNameBuilder, interface](itypenamebuilder-interface.md)  
 Fournit des méthodes pour la génération d’un nom de type. (Cette interface prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement à partir de votre code.)  
  
 [ITypeNameFactory, interface](itypenamefactory-interface.md)  
 Fournit des méthodes pour décomposer un nom de type. (Cette interface prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement à partir de votre code.)  
  
 IValidator  
 Fournit des méthodes pour valider des images exécutables portables (PE) et des erreurs de validation de rapport.  
  
## <a name="related-sections"></a>Sections connexes  
 [Interfaces d'hébergement du CLR et coclasses déconseillées](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 Contient des rubriques qui décrivent les interfaces d’hébergement fournies dans le .NET Framework version 1,0 et 1,1.  
  
 [Interfaces d'hébergement du CLR ajoutées dans .NET Framework 4 et 4.5](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 Contient des rubriques qui décrivent les interfaces d’hébergement fournies dans le .NET Framework 4.
