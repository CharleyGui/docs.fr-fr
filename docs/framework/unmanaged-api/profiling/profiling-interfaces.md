---
title: Interfaces de profilage
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
ms.openlocfilehash: dd6999e9f9e16264bde3cf62ce3a888841347607
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727469"
---
# <a name="profiling-interfaces"></a>Interfaces de profilage

Cette section décrit les interfaces non managées qui vous permettent de profiler un programme exécuté par le CLR (Common Language Runtime).  
  
## <a name="in-this-section"></a>Dans cette section  

 [ICLRProfiling, interface](iclrprofiling-interface.md)  
 Fournit la méthode [AttachProfiler](iclrprofiling-attachprofiler-method.md) , qui permet à un profileur de s’attacher à un processus en cours d’exécution.  
  
 [ICorProfilerAssemblyReferenceProvider, interface](icorprofilerassemblyreferenceprovider-interface.md)  
 Permet au profileur d’informer le CLR des références d’assembly que le profileur ajoutera dans le rappel de [ICorProfilerCallback :: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) .  
  
 [ICorProfilerCallback, interface](icorprofilercallback-interface.md)  
 Fournit des méthodes qui sont utilisées par le CLR pour envoyer des notifications à un profileur de code quand les événements auxquels le profileur s'est abonné se produisent.  
  
 [ICorProfilerCallback2, interface](icorprofilercallback2-interface.md)  
 Étend l'interface `ICorProfilerCallback` avec des rappels pris en charge dans .NET Framework 2.0 et ultérieur.  
  
 [ICorProfilerCallback3, interface](icorprofilercallback3-interface.md)  
 Fournit des méthodes de rappel que le CLR utilise pour communiquer au profileur des informations d'état d'attachement et de détachement.  
  
 [ICorProfilerCallback4, interface](icorprofilercallback4-interface.md)  
 Fournit des méthodes de rappel que le CLR utilise pour communiquer des informations au profileur.  
  
 [ICorProfilerCallback5, interface](icorprofilercallback5-interface.md)  
 Fournit une méthode qui identifie la fermeture transitive d’objets référencés par des racines de récupération de mémoire.  
  
 [ICorProfilerCallback6, interface](icorprofilercallback6-interface.md)  
 Fournit une méthode de rappel utilisée par le CLR pour envoyer une notification à un profileur quand un assembly est en cours de chargement.  
  
 [Interface ICorProfilerCallback7](icorprofilercallback7-interface.md)  
 Fournit une méthode de rappel que le common language runtime utilise pour informer le profileur que le flux de symboles associé à un module en mémoire est mis à jour.  

[ICorProfilerCallback8, interface](icorprofilercallback8-interface.md)  
Fournit des méthodes de rappel que le common language runtime utilise pour informer le profileur que la compilation JIT d’une méthode dynamique a démarré et se termine.

[ICorProfilerCallback9, interface](icorprofilercallback9-interface.md)  
Fournit une méthode de rappel que le common language runtime utilise pour informer le profileur qu’une méthode dynamique est récupérée par le garbage collector et déchargée par la suite.

 [ICorProfilerFunctionControl, interface](icorprofilerfunctioncontrol-interface.md)  
 Fournit des méthodes qui permettent à un profileur de code de communiquer avec le CLR (Common Language Runtime) pour contrôler comment le compilateur juste-à-temps doit générer du code lors de la recompilation d'une méthode spécifique.  
  
 [ICorProfilerFunctionEnum, interface](icorprofilerfunctionenum-interface.md)  
 Fournit des méthodes pour boucler séquentiellement dans une collection de fonctions dans le CLR.  
  
 [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)  
 Fournit des méthodes utilisées par les profileurs de code pour communiquer avec le CLR pour contrôler la surveillance des événements et demander des informations.  
  
 [ICorProfilerInfo2, interface](icorprofilerinfo2-interface.md)  
 Étend l'interface `ICorProfilerInfo` avec des méthodes prises en charge dans .NET Framework 2.0 et ultérieur.  
  
 [ICorProfilerInfo3, interface](icorprofilerinfo3-interface.md)  
 Étend l' `ICorProfilerInfo2` interface avec des méthodes prises en charge dans le .NET Framework 4 et versions ultérieures.  
  
 [ICorProfilerInfo4, interface](icorprofilerinfo4-interface.md)  
 Fournit des méthodes utilisées par les profileurs de code pour communiquer avec le CLR pour contrôler la surveillance des événements et demander des informations.  
  
 [ICorProfilerInfo5, interface](icorprofilerinfo5-interface.md)  
 Fournit des méthodes utilisées par les profileurs de code pour communiquer avec le CLR pour contrôler la surveillance des événements.  
  
 [ICorProfilerInfo6, interface](icorprofilerinfo6-interface.md)  
 Fournit un énumérateur à toutes les méthodes qui appartiennent à un module NGen donné et qui sont inline dans le corps d’une méthode donnée.  
  
 [ICorProfilerInfo7, interface](icorprofilerinfo7-interface.md)  
 Fournit une méthode pour appliquer des métadonnées nouvellement définies à un module et qui fournit l’accès à un flux de symboles en mémoire.  
  
 [ICorProfilerModuleEnum, interface](icorprofilermoduleenum-interface.md)  
 Fournit des méthodes pour boucler séquentiellement dans une collection de modules chargés par l’application ou par le profileur.  
  
 [ICorProfilerObjectEnum, interface](icorprofilerobjectenum-interface.md)  
 Fournit des méthodes pour itérer séquentiellement au sein d’une collection d’objets figés qui sont générés par [Ngen.exe (générateur d’images natives)](../../tools/ngen-exe-native-image-generator.md).  
  
 [ICorProfilerThreadEnum, interface](icorprofilerthreadenum-interface.md)  
 Fournit des méthodes pour boucler séquentiellement dans une collection de threads dans le CLR.  
  
 [IMethodMalloc, interface](imethodmalloc-interface.md)  
 Fournit la méthode [Alloc](imethodmalloc-alloc-method.md) pour allouer de la mémoire pour un nouveau corps de fonction MSIL (Microsoft Intermediate Language).  
  
## <a name="related-sections"></a>Sections connexes  

 [Vue d’ensemble du profilage](profiling-overview.md)  
  
 [Fonctions statiques globales du profilage](profiling-global-static-functions.md)  
  
 [Énumérations de profilage](profiling-enumerations.md)  
  
 [Structures de profilage](profiling-structures.md)
