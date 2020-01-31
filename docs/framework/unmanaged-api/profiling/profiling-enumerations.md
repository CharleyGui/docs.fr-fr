---
title: Énumérations de profilage
ms.date: 03/30/2017
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
ms.openlocfilehash: 1a9781fa1b4b608152faa7d5edc80bd4866f0c81
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868133"
---
# <a name="profiling-enumerations"></a>Énumérations de profilage
Cette section décrit les énumérations non managées utilisées par l'API de profilage.  
  
## <a name="in-this-section"></a>Dans cette section  
 [COR_PRF_CLAUSE_TYPE, énumération](cor-prf-clause-type-enumeration.md)  
 Indique le type de clause d'exception où le code vient d'entrer ou qu'il vient de quitter.  
  
 [COR_PRF_CODEGEN_FLAGS, énumération](cor-prf-codegen-flags-enumeration.md)  
 Définit les indicateurs de génération de code qui peuvent être définis avec la méthode [ICorProfilerFunctionControl :: setcodegenflags,](icorprofilerfunctioncontrol-setcodegenflags-method.md) .  
  
 [COR_PRF_FINALIZER_FLAGS, énumération](cor-prf-finalizer-flags-enumeration.md)  
 Décrit le finaliseur pour un objet.  
  
 [COR_PRF_GC_GENERATION, énumération](cor-prf-gc-generation-enumeration.md)  
 Identifie une génération de récupération de mémoire.  
  
 [COR_PRF_GC_REASON, énumération](cor-prf-gc-reason-enumeration.md)  
 Indique la raison pour laquelle une récupération de mémoire se produit.  
  
 [COR_PRF_GC_ROOT_FLAGS, énumération](cor-prf-gc-root-flags-enumeration.md)  
 Indique les propriétés d'une racine de récupérateur de mémoire.  
  
 [COR_PRF_GC_ROOT_KIND, énumération](cor-prf-gc-root-kind-enumeration.md)  
 Indique le type de racine de garbage collector qui est exposé par le rappel [ICorProfilerCallback2 :: RootReferences2](icorprofilercallback2-rootreferences2-method.md) .  
  
 [COR_PRF_MODULE_FLAGS, énumération](cor-prf-high-monitor-enumeration.md)  
 Fournit des indicateurs en plus de ceux figurant dans l’énumération [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) que le profileur peut spécifier à la méthode [ICorProfilerInfo5 :: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) lors du chargement.  
  
 [COR_PRF_JIT_CACHE, énumération](cor-prf-jit-cache-enumeration.md)  
 Indique le résultat de la recherche d'une fonction mise en cache.  
  
 [COR_PRF_MISC, énumération](cor-prf-misc-enumeration.md)  
 Contient des valeurs de constante qui spécifient des identificateurs spéciaux.  
  
 [COR_PRF_MODULE_FLAGS, énumération](cor-prf-module-flags-enumeration.md)  
 Spécifie les propriétés d'un module.  
  
 [COR_PRF_MONITOR, énumération](cor-prf-monitor-enumeration.md)  
 Contient des valeurs utilisées pour spécifier un comportement, des fonctionnalités ou des événements auxquels le profileur veut s'abonner.  
  
 [COR_PRF_RUNTIME_TYPE, énumération](cor-prf-runtime-type-enumeration.md)  
 Contient des valeurs qui indiquent la version du CLR (Common Language Runtime).  
  
 [COR_PRF_SNAPSHOT_INFO, énumération](cor-prf-snapshot-info-enumeration.md)  
 Spécifie la quantité de données à passer en retour avec une capture instantanée de la pile dans chaque appel à la fonction `StackSnapshotCallback` du profileur.  
  
 [COR_PRF_STATIC_TYPE, énumération](cor-prf-static-type-enumeration.md)  
 Indique si un champ est statique et si oui, la qualité statique qui s'y applique.  
  
 [COR_PRF_SUSPEND_REASON, énumération](cor-prf-suspend-reason-enumeration.md)  
 Indique la raison pour laquelle le runtime a été suspendu.  
  
 [COR_PRF_TRANSITION_REASON, énumération](cor-prf-transition-reason-enumeration.md)  
 Indique la raison d'une transition de code managé en code non managé, ou l'inverse.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Vue d’ensemble du profilage](profiling-overview.md)  
  
 [Interfaces de profilage](profiling-interfaces.md)  
  
 [Fonctions statiques globales de profilage](profiling-global-static-functions.md)  
  
 [Structures de profilage](profiling-structures.md)
