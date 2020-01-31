---
title: Fonctions statiques globales du profilage
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
ms.openlocfilehash: 20ee2a9e045d839aa8ac043e035c438986b987ef
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76860864"
---
# <a name="profiling-global-static-functions"></a>Fonctions statiques globales du profilage
Cette section décrit les fonctions d’API non managées utilisées par l’API de profilage.  
  
## <a name="in-this-section"></a>Dans cette section  
  
## <a name="net-framework-version-1-profiling-functions"></a>.NET Framework les fonctions de profilage de la version 1  
 [FunctionEnter, fonction](functionenter-function.md)  
 Indique au profileur que le contrôle est passé à une fonction. Déconseillé dans le .NET Framework 2,0.  
  
 [FunctionLeave, fonction](functionleave-function.md)  
 Notifie le profileur qu’une fonction va retourner à l’appelant. Déconseillé dans le .NET Framework 2,0.  
  
 [FunctionTailcall, fonction](functiontailcall-function.md)  
 Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction. Déconseillé dans le .NET Framework 2,0.  
  
## <a name="net-framework-version-2-profiling-functions"></a>.NET Framework les fonctions de profilage de la version 2  
 [FunctionIDMapper, fonction](functionidmapper-function.md)  
 Notifie le profileur que l’identificateur donné d’une fonction peut être remappé à un autre ID à utiliser dans les rappels [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)et [FunctionTailcall2](functiontailcall2-function.md) pour cette fonction. Permet également au profileur d’indiquer s’il souhaite recevoir des rappels pour cette fonction  
  
 [FunctionEnter2, fonction](functionenter2-function.md)  
 Notifie le profileur que le contrôle est passé à une fonction et fournit des informations sur le frame de pile et les arguments de fonction. Déconseillé dans le .NET Framework 4.  
  
 [FunctionLeave2, fonction](functionleave2-function.md)  
 Notifie le profileur qu’une fonction va retourner à l’appelant et fournit des informations sur le frame de pile et la valeur de retour de fonction. Déconseillé dans le .NET Framework 4.  
  
 [FunctionTailcall2, fonction](functiontailcall2-function.md)  
 Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction et fournit des informations sur le frame de pile. Déconseillé dans le .NET Framework 4.  
  
 [StackSnapshotCallback, fonction](stacksnapshotcallback-function.md)  
 Fournit au profileur des informations sur chaque frame managé et chaque série de frames non managés sur la pile pendant un parcours de pile, qui est initié par la méthode [ICorProfilerInfo2 ::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) .  
  
## <a name="net-framework-version-4-profiling-functions"></a>.NET Framework les fonctions de profilage de la version 4  
 [FunctionIDMapper2, fonction](functionidmapper2-function.md)  
 Notifie le profileur que l’identificateur donné d’une fonction peut être remappé à un autre ID à utiliser dans les rappels [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)et [FunctionTailcall3](functiontailcall3-function.md), ou[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)et [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) pour cette fonction. Permet également au profileur d’indiquer s’il souhaite recevoir des rappels pour cette fonction.  
  
 `FunctionIDMapper2` étend la fonction [FunctionIDMapper](functionidmapper-function.md) avec un paramètre `clientData`, que les profileurs peuvent utiliser pour lever l’ambiguïté entre les runtimes.  
  
 [FunctionEnter3, fonction](functionenter3-function.md)  
 Indique au profileur que le contrôle est passé à une fonction.  
  
 [FunctionEnter3WithInfo, fonction](functionenter3withinfo-function.md)  
 Notifie le profileur que le contrôle est passé à une fonction et fournit un handle qui peut être passé à [ICorProfilerInfo3 :: GetFunctionEnter3Info,](icorprofilerinfo3-getfunctionenter3info-method.md) pour récupérer le frame de pile et les arguments de fonction.  
  
 [FunctionLeave3, fonction](functionleave3-function.md)  
 Indique au profileur que le contrôle est retourné à partir d’une fonction.  
  
 [FunctionLeave3WithInfo, fonction](functionleave3withinfo-function.md)  
 Indique au profileur que le contrôle est retourné à partir d’une fonction et fournit un handle qui peut être passé à [ICorProfilerInfo3 :: GetFunctionLeave3Info,](icorprofilerinfo3-getfunctionleave3info-method.md) pour récupérer le frame de pile et la valeur de retour.  
  
 [FunctionTailcall3, fonction](functiontailcall3-function.md)  
 Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction.  
  
 [FunctionTailcall3WithInfo, fonction](functiontailcall3withinfo-function.md)  
 Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction et fournit un handle qui peut être passé à [ICorProfilerInfo3 :: GetFunctionTailcall3Info,](icorprofilerinfo3-getfunctiontailcall3info-method.md) pour récupérer le frame de pile.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Vue d’ensemble du profilage](profiling-overview.md)  
  
 [Interfaces de profilage](profiling-interfaces.md)  
  
 [Énumérations de profilage](profiling-enumerations.md)  
  
 [Structures de profilage](profiling-structures.md)
