---
title: Énumérations d'hébergement
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged enumerations [.NET Framework], hosting
- enumerations [.NET Framework hosting]
- hosting enumerations [.NET Framework]
ms.assetid: e09131eb-1f7d-4f52-ae42-7393e9b62ef6
ms.openlocfilehash: 8edace3191ee4477b19f199d5db6c891c993dcd5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504301"
---
# <a name="hosting-enumerations"></a>Énumérations d'hébergement
Cette section décrit les énumérations non managées utilisées par l’API d’hébergement.  
  
## <a name="in-this-section"></a>Dans cette section  
 [CLSID_RESOLUTION_FLAGS, énumération](clsid-resolution-flags-enumeration.md)  
 Contient des valeurs qui indiquent comment le common language runtime (CLR) doit résoudre un `CLSID` .  
  
 [COR_GC_STAT_TYPES (énumération)](cor-gc-stat-types-enumeration.md)  
 Spécifie les statistiques à enregistrer pour un garbage collection.  
  
 [COR_GC_THREAD_STATS_TYPES (énumération)](cor-gc-thread-stats-types-enumeration.md)  
 Indique les statistiques de garbage collection d’un thread.  
  
 [EApiCategories, énumération](eapicategories-enumeration.md)  
 Décrit les catégories de fonctionnalités que l’hôte peut empêcher de s’exécuter dans du code de confiance partielle.  
  
 [EBindPolicyLevels, énumération](ebindpolicylevels-enumeration.md)  
 Fournit des indicateurs qui spécifient le niveau auquel appliquer ou modifier la stratégie d’assembly.  
  
 [ECLRAssemblyIdentityFlags, énumération](eclrassemblyidentityflags-enumeration.md)  
 Indique le type de l’identité d’un assembly.  
  
 [EClrEvent, énumération](eclrevent-enumeration.md)  
 Décrit les événements CLR pour lesquels l’hôte peut inscrire des rappels.  
  
 [EClrFailure, énumération](eclrfailure-enumeration.md)  
 Décrit l’ensemble des échecs pour lesquels un hôte peut définir des actions de stratégie.  
  
 [EClrOperation, énumération](eclroperation-enumeration.md)  
 Décrit l’ensemble des opérations pour lesquelles un hôte peut appliquer des actions de stratégie.  
  
 [EClrUnhandledException, énumération](eclrunhandledexception-enumeration.md)  
 Décrit les options disponibles pour gérer les exceptions qui ne sont pas gérées dans le code utilisateur.  
  
 [EContextType, énumération](econtexttype-enumeration.md)  
 Décrit le contexte de sécurité du thread en cours d’exécution.  
  
 [ECustomDumpFlavor, énumération](ecustomdumpflavor-enumeration.md)  
 Contient des valeurs qui indiquent les éléments à inclure dans un sous-ensemble personnalisé d’un dump de tas lors du signalement d’erreurs.  
  
 [ECustomDumpItemKind, énumération](ecustomdumpitemkind-enumeration.md)  
 Réservé pour une extension future de la structure de la [structure CustomDumpItem](customdumpitem-structure.md) .  
  
 [EHostApplicationPolicy, énumération](ehostapplicationpolicy-enumeration.md)  
 Indique comment modifier un objet d’interface d' [interface IHostAssemblyManager](ihostassemblymanager-interface.md) . Cette énumération a été dépréciée.  
  
 [EHostBindingPolicyModifyFlags, énumération](ehostbindingpolicymodifyflags-enumeration.md)  
 Permet à l’hôte de spécifier le type de redirection que le CLR doit effectuer lors de l’application des modifications de stratégie d’un assembly source à un assembly cible.  
  
 [EInitializeNewDomainFlags, énumération](einitializenewdomainflags-enumeration.md)  
 Permet à l’hôte de fournir au runtime des informations sur l’initialisation d’un domaine d’application.  
  
 [EMemoryAvailable, énumération](ememoryavailable-enumeration.md)  
 Contient des valeurs qui indiquent la quantité de mémoire physique disponible sur l’ordinateur.  
  
 [EMemoryCriticalLevel, énumération](ememorycriticallevel-enumeration.md)  
 Contient des valeurs qui indiquent l’impact d’un échec lorsqu’une allocation de mémoire spécifique a été demandée, mais ne peut pas être satisfaite.  
  
 [EPolicyAction, énumération](epolicyaction-enumeration.md)  
 Décrit les actions de stratégie que l’hôte peut définir pour les opérations décrites par l' [énumération EClrOperation](eclroperation-enumeration.md) et les échecs décrits par l' [énumération EClrFailure](eclrfailure-enumeration.md).  
  
 [ESymbolReadingPolicy, énumération](esymbolreadingpolicy-enumeration.md)  
 Contient des valeurs qui définissent la stratégie de lecture des fichiers de base de données du programme (PDB).  
  
 [ETaskType, énumération](etasktype-enumeration.md)  
 Contient des valeurs qui indiquent le type de tâche représenté par une [interface ICLRTask](iclrtask-interface.md) ou une interface d' [interface IHostTask](ihosttask-interface.md) .  
  
 [HOST_TYPE, énumération](host-type-enumeration.md)  
 Contient des valeurs qui spécifient le type d’hôte qui lance une application.  
  
 [MALLOC_TYPE, énumération](malloc-type-enumeration.md)  
 Contient des valeurs qui spécifient les caractéristiques de la mémoire qui est allouée.  
  
 [METAHOST_CONFIG_FLAGS, énumération](metahost-config-flags-enumeration.md)  
 Décrit les indicateurs possibles retournés dans le `pdwConfigFlags` paramètre de la méthode [ICLRMetaHostPolicy :: GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) .  
  
 [METAHOST_POLICY_FLAGS, énumération](metahost-policy-flags-enumeration.md)  
 Fournit des stratégies de liaison communes à la plupart des hôtes de Runtime.  
  
 [RUNTIME_INFO_FLAGS, énumération](runtime-info-flags-enumeration.md)  
 Contient des valeurs qui indiquent quelles informations sur le CLR doivent être retournées.  
  
 [StackOverflowType, énumération](stackoverflowtype-enumeration.md)  
 Contient des valeurs qui indiquent la cause sous-jacente d’un événement de dépassement de capacité de la pile.  
  
 [STARTUP_FLAGS, énumération](startup-flags-enumeration.md)  
 Contient des valeurs qui indiquent le comportement de démarrage du CLR.  
  
 [ValidatorFlags, énumération](validatorflags-enumeration.md)  
 Contient des valeurs qui indiquent le type de validation qui doit être effectuée dans un appel à la [méthode Validate](iclrvalidator-validate-method.md).  
  
 [WAIT_OPTION, énumération](wait-option-enumeration.md)  
 Indique l’action qu’un hôte doit effectuer si une opération demandée par le CLR est bloquée.  
  
## <a name="related-sections"></a>Sections connexes  
 [Hébergement des coclasses](hosting-coclasses.md)  
  
 [Interfaces d'hébergement](hosting-interfaces.md)  
  
 [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)  
  
 [Structures d'hébergement](hosting-structures.md)
