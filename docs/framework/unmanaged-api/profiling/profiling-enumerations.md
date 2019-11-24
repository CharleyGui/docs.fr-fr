---
title: Énumérations de profilage
ms.date: 03/30/2017
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
ms.openlocfilehash: bc90743fb348c31bd2f7487c1573ec38a43bd3af
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447447"
---
# <a name="profiling-enumerations"></a>Énumérations de profilage
Cette section décrit les énumérations non managées utilisées par l'API de profilage.  
  
## <a name="in-this-section"></a>Dans cette section  
 [COR_PRF_CLAUSE_TYPE, énumération](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)  
 Indique le type de clause d'exception où le code vient d'entrer ou qu'il vient de quitter.  
  
 [COR_PRF_CODEGEN_FLAGS, énumération](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)  
 Définit les indicateurs de génération de code qui peuvent être définis avec la méthode [ICorProfilerFunctionControl :: setcodegenflags,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) .  
  
 [COR_PRF_FINALIZER_FLAGS, énumération](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)  
 Décrit le finaliseur pour un objet.  
  
 [COR_PRF_GC_GENERATION, énumération](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)  
 Identifie une génération de récupération de mémoire.  
  
 [COR_PRF_GC_REASON, énumération](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)  
 Indique la raison pour laquelle une récupération de mémoire se produit.  
  
 [COR_PRF_GC_ROOT_FLAGS, énumération](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)  
 Indique les propriétés d'une racine de récupérateur de mémoire.  
  
 [COR_PRF_GC_ROOT_KIND, énumération](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)  
 Indique le type de racine de garbage collector qui est exposé par le rappel [ICorProfilerCallback2 :: RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) .  
  
 [COR_PRF_MODULE_FLAGS, énumération](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)  
 Fournit des indicateurs en plus de ceux figurant dans l’énumération [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) que le profileur peut spécifier à la méthode [ICorProfilerInfo5 :: SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) lors du chargement.  
  
 [COR_PRF_JIT_CACHE, énumération](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)  
 Indique le résultat de la recherche d'une fonction mise en cache.  
  
 [COR_PRF_MISC, énumération](../../../../docs/framework/unmanaged-api/profiling/cor-prf-misc-enumeration.md)  
 Contient des valeurs de constante qui spécifient des identificateurs spéciaux.  
  
 [COR_PRF_MODULE_FLAGS, énumération](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)  
 Spécifie les propriétés d'un module.  
  
 [COR_PRF_MONITOR, énumération](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 Contient des valeurs utilisées pour spécifier un comportement, des fonctionnalités ou des événements auxquels le profileur veut s'abonner.  
  
 [COR_PRF_RUNTIME_TYPE, énumération](../../../../docs/framework/unmanaged-api/profiling/cor-prf-runtime-type-enumeration.md)  
 Contient des valeurs qui indiquent la version du CLR (Common Language Runtime).  
  
 [COR_PRF_SNAPSHOT_INFO, énumération](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)  
 Spécifie la quantité de données à passer en retour avec une capture instantanée de la pile dans chaque appel à la fonction `StackSnapshotCallback` du profileur.  
  
 [COR_PRF_STATIC_TYPE, énumération](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)  
 Indique si un champ est statique et si oui, la qualité statique qui s'y applique.  
  
 [COR_PRF_SUSPEND_REASON, énumération](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)  
 Indique la raison pour laquelle le runtime a été suspendu.  
  
 [COR_PRF_TRANSITION_REASON, énumération](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)  
 Indique la raison d'une transition de code managé en code non managé, ou l'inverse.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Vue d’ensemble du profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Fonctions statiques globales de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [Structures de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
