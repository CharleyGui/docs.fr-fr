---
title: ICorProfilerInfo::EndInprocDebugging, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.EndInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::EndInprocDebugging
helpviewer_keywords:
- ICorProfilerInfo::EndInprocDebugging method [.NET Framework profiling]
- EndInprocDebugging method [.NET Framework profiling]
ms.assetid: 35bc1188-9767-4141-8038-60ea015b99ac
topic_type:
- apiref
ms.openlocfilehash: e929c74ba0f1f33ddbb28476b3c9e0a512567ac6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95669053"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a>ICorProfilerInfo::EndInprocDebugging, méthode

Arrête une session de débogage en cours de processus. Cette méthode est obsolète dans la version 2,0 de .NET Framework.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
## <a name="parameters"></a>Paramètres  

 `dwProfilerContext`  
 dans Valeur qui identifie la session de débogage. Cette valeur doit être la même que celle reçue dans la méthode [ICorProfilerInfo :: BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) .  
  
## <a name="remarks"></a>Remarques  

 Vous devez appeler [ICorProfilerInfo :: BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) et `EndInprocDebugging` dans la même méthode de rappel.  
  
 Les services de débogage du CLR ont pris en charge le débogage de processus limité dans le .NET Framework versions 1,0 et 1,1. Le débogage en cours de processus permettait à un profileur d’utiliser les parties d’inspection de l’API de débogage. Toutefois, en raison des commentaires des clients, le débogage en cours de processus a été supprimé de la .NET Framework dans la version 2,0 et remplacé par un ensemble de fonctionnalités qui est plus en ligne avec l’API de profilage.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Version de .NET Framework :** 1,0  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
