---
title: ICorProfilerInfo4::InitializeCurrentThread, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4::InitializeCurrentThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type:
- apiref
ms.openlocfilehash: b52a0e7f993629c1005883723c734996d75300a7
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868432"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a>ICorProfilerInfo4::InitializeCurrentThread, méthode
Initialise le thread actuel avant les appels d’API du profileur suivants sur le même thread, afin que l’interblocage puisse être évité.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a>Notes  
 Nous vous recommandons d’appeler `InitializeCurrentThread` sur tout thread qui appellera une API de profileur alors qu’il y a des threads suspendus. Cette méthode est généralement utilisée par les profileurs d’échantillonnage qui créent leur propre thread pour appeler la méthode [ICorProfilerInfo2 ::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) pour effectuer des parcours de pile pendant que le thread cible est suspendu. En appelant `InitializeCurrentThread` une fois que le profileur a créé le thread d’échantillonnage pour la première fois, les profileurs peuvent garantir que l’initialisation différée par thread que le CLR effectue normalement pendant le premier appel à `DoStackSnapshot` peut désormais se produire en toute sécurité quand aucun autre thread n’est suspendu.  
  
> [!NOTE]
> `InitializeCurrentThread` effectue l’initialisation à l’avance pour terminer les tâches qui prennent des verrous et peut se bloquer. Appelez `InitializeCurrentThread` uniquement lorsqu’il n’y a pas de threads suspendus.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo4, interface](icorprofilerinfo4-interface.md)
- [Interfaces de profilage](profiling-interfaces.md)
- [Profilage](index.md)
