---
title: ICorProfilerFunctionEnum::Skip, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
- ICorProfilerFunctionEnum::Skip method [.NET Framework profiling]
ms.assetid: 051465b9-e479-494a-804b-c880323b4cbe
topic_type:
- apiref
ms.openlocfilehash: da578e02db0744b1f64c1d392844aa020721e784
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95669253"
---
# <a name="icorprofilerfunctionenumskip-method"></a>ICorProfilerFunctionEnum::Skip, méthode

Fait avancer le curseur de l'énumérateur depuis sa position actuelle de manière à ignorer le nombre spécifié d'éléments.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a>Paramètres  

 `celt`  
 dans Nombre d’éléments à ignorer.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`celt` les éléments ont été ignorés.|  
|S_FALSE|Moins de `celt` éléments ont été ignorés, ce qui indique qu’il n’y a plus d’éléments.|  
  
## <a name="remarks"></a>Remarques  

 La nouvelle position du curseur de cet énumérateur est (position actuelle) + `celt` .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerFunctionEnum, interface](icorprofilerfunctionenum-interface.md)
- [Interfaces de profilage](profiling-interfaces.md)
