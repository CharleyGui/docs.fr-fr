---
title: Fonctions statiques globales du profilage
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
ms.openlocfilehash: d1d9b0a4c61ce7c3f8f9792046fb4bddf0fdfa05
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447433"
---
# <a name="profiling-global-static-functions"></a>Fonctions statiques globales du profilage
Cette section décrit les fonctions d’API non managées utilisées par l’API de profilage.  
  
## <a name="in-this-section"></a>Dans cette section  
  
## <a name="net-framework-version-1-profiling-functions"></a>.NET Framework les fonctions de profilage de la version 1  
 [FunctionEnter, fonction](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)  
 Indique au profileur que le contrôle est passé à une fonction. Déconseillé dans le .NET Framework 2,0.  
  
 [FunctionLeave, fonction](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)  
 Notifie le profileur qu’une fonction va retourner à l’appelant. Déconseillé dans le .NET Framework 2,0.  
  
 [FunctionTailcall, fonction](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md)  
 Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction. Déconseillé dans le .NET Framework 2,0.  
  
## <a name="net-framework-version-2-profiling-functions"></a>.NET Framework les fonctions de profilage de la version 2  
 [FunctionIDMapper, fonction](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)  
 Notifie le profileur que l’identificateur donné d’une fonction peut être remappé à un autre ID à utiliser dans les rappels [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)et [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) pour cette fonction. Permet également au profileur d’indiquer s’il souhaite recevoir des rappels pour cette fonction  
  
 [FunctionEnter2, fonction](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 Notifie le profileur que le contrôle est passé à une fonction et fournit des informations sur le frame de pile et les arguments de fonction. Déconseillé dans le .NET Framework 4.  
  
 [FunctionLeave2, fonction](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 Notifie le profileur qu’une fonction va retourner à l’appelant et fournit des informations sur le frame de pile et la valeur de retour de fonction. Déconseillé dans le .NET Framework 4.  
  
 [FunctionTailcall2, fonction](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction et fournit des informations sur le frame de pile. Déconseillé dans le .NET Framework 4.  
  
 [StackSnapshotCallback, fonction](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)  
 Fournit au profileur des informations sur chaque frame managé et chaque série de frames non managés sur la pile pendant un parcours de pile, qui est initié par la méthode [ICorProfilerInfo2 ::D ostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) .  
  
## <a name="net-framework-version-4-profiling-functions"></a>.NET Framework les fonctions de profilage de la version 4  
 [FunctionIDMapper2, fonction](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 Notifie le profileur que l’identificateur donné d’une fonction peut être remappé à un autre ID à utiliser dans les rappels [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)et [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), ou[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)et [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) pour cette fonction. Permet également au profileur d’indiquer s’il souhaite recevoir des rappels pour cette fonction.  
  
 `FunctionIDMapper2` étend la fonction [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) avec un paramètre `clientData`, que les profileurs peuvent utiliser pour lever l’ambiguïté entre les runtimes.  
  
 [FunctionEnter3, fonction](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 Indique au profileur que le contrôle est passé à une fonction.  
  
 [FunctionEnter3WithInfo, fonction](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 Notifie le profileur que le contrôle est passé à une fonction et fournit un handle qui peut être passé à [ICorProfilerInfo3 :: GetFunctionEnter3Info,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) pour récupérer le frame de pile et les arguments de fonction.  
  
 [FunctionLeave3, fonction](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 Indique au profileur que le contrôle est retourné à partir d’une fonction.  
  
 [FunctionLeave3WithInfo, fonction](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 Indique au profileur que le contrôle est retourné à partir d’une fonction et fournit un handle qui peut être passé à [ICorProfilerInfo3 :: GetFunctionLeave3Info,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) pour récupérer le frame de pile et la valeur de retour.  
  
 [FunctionTailcall3, fonction](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction.  
  
 [FunctionTailcall3WithInfo, fonction](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction et fournit un handle qui peut être passé à [ICorProfilerInfo3 :: GetFunctionTailcall3Info,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) pour récupérer le frame de pile.  
  
## <a name="related-sections"></a>Sections connexes  
 [Vue d’ensemble du profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Énumérations de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [Structures de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
