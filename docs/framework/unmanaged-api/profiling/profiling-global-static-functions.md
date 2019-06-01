---
title: Fonctions statiques globales du profilage
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ea65c06871d9762fa6daac229a568594b4c4479
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457474"
---
# <a name="profiling-global-static-functions"></a>Fonctions statiques globales du profilage
Cette section décrit les fonctions d’API non managées qui utilise l’API de profilage.  
  
## <a name="in-this-section"></a>Dans cette section  
  
## <a name="net-framework-version-1-profiling-functions"></a>Fonctions de profilage .NET framework version 1  
 [FunctionEnter, fonction](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)  
 Notifie le profileur que le contrôle est passé à une fonction. Déconseillée dans le .NET Framework 2.0.  
  
 [FunctionLeave, fonction](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)  
 Notifie le profileur qu’une fonction est sur le point de retourner à l’appelant. Déconseillée dans le .NET Framework 2.0.  
  
 [FunctionTailcall, fonction](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md)  
 Notifie le profileur que la fonction en cours d’exécution est sur le point d’effectuer un appel tail à une autre fonction. Déconseillée dans le .NET Framework 2.0.  
  
## <a name="net-framework-version-2-profiling-functions"></a>Fonctions de profilage .NET framework version 2  
 [FunctionIDMapper, fonction](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)  
 Notifie le profileur que l’identificateur donné d’une fonction peut être remappé vers un autre ID à utiliser dans le [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), et [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) rappels pour cette fonction. Permet également au profileur d’indiquer s’il souhaite recevoir des rappels pour cette fonction  
  
 [FunctionEnter2, fonction](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 Notifie le profileur que le contrôle est passé à une fonction et fournit des informations sur la pile des arguments de fonction et de frame. Déconseillée dans le .NET Framework 4.  
  
 [FunctionLeave2, fonction](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 Notifie le profileur qu’une fonction doit renvoyer à l’appelant et fournit des informations sur la valeur de retour pile frame et de fonction. Déconseillée dans le .NET Framework 4.  
  
 [FunctionTailcall2, fonction](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 Notifie le profileur que la fonction en cours d’exécution est sur le point d’effectuer un appel tail à une autre fonction et fournit des informations sur le frame de pile. Déconseillée dans le .NET Framework 4.  
  
 [StackSnapshotCallback, fonction](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)  
 Fournit au profileur des informations sur chaque frame managé et chaque exécution de trames non gérées sur la pile pendant un parcours de pile, ce qui est lancée par le [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) (méthode).  
  
## <a name="net-framework-version-4-profiling-functions"></a>Fonctions de profilage .NET framework version 4  
 [FunctionIDMapper2, fonction](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 Notifie le profileur que l’identificateur donné d’une fonction peut être remappé vers un autre ID à utiliser dans le [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), et [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), ou[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), et [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) rappels pour cette fonction. permet également au profileur d’indiquer s’il souhaite recevoir des rappels pour cette fonction.  
  
 `FunctionIDMapper2` étend la [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) fonctionne avec un `clientData` paramètre, qui les profileurs peuvent utiliser pour distinguer les différents runtimes.  
  
 [FunctionEnter3, fonction](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 Notifie le profileur que le contrôle est passé à une fonction.  
  
 [FunctionEnter3WithInfo, fonction](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 Notifie le profileur que le contrôle est passé à une fonction et fournit un handle qui peut être passé à [ICorProfilerInfo3::GetFunctionEnter3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) pour récupérer les arguments de fonction et de frame de pile.  
  
 [FunctionLeave3, fonction](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 Notifie le profileur que le contrôle a été renvoyé à partir d’une fonction.  
  
 [FunctionLeave3WithInfo, fonction](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 Notifie le profileur que le contrôle a été renvoyé à partir d’une fonction et fournit un handle qui peut être passé à [ICorProfilerInfo3::GetFunctionLeave3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) pour récupérer le frame de pile et la valeur de retour.  
  
 [FunctionTailcall3, fonction](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 Notifie le profileur que la fonction en cours d’exécution est sur le point d’effectuer un appel tail à une autre fonction.  
  
 [FunctionTailcall3WithInfo, fonction](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 Informe le profileur que la fonction en cours d’exécution est sur le point d’effectuer un appel tail à une autre fonction et fournit un handle qui peut être passé à [ICorProfilerInfo3::GetFunctionTailcall3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) pour récupérer le frame de pile.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Vue d’ensemble du profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Énumérations de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [Structures de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
