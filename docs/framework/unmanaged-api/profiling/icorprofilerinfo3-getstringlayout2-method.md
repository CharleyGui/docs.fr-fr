---
title: ICorProfilerInfo3::GetStringLayout2, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetStringLayout2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type:
- apiref
ms.openlocfilehash: dc4df7e7cb93f137013d0a0e4d805c7563d4fe1a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697894"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a>ICorProfilerInfo3::GetStringLayout2, méthode

Obtient des informations sur la disposition d'un objet string. Cette méthode remplace la méthode [ICorProfilerInfo2 :: GetStringLayout,](icorprofilerinfo2-getstringlayout-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pStringLengthOffset`  
 à Pointeur vers le décalage de l’emplacement, relatif au `ObjectID` pointeur, qui stocke la longueur de la chaîne elle-même. La longueur est stockée sous la forme d’un `DWORD` .  
  
 `pBufferOffset`  
 à Pointeur vers l’offset de la mémoire tampon, relatif au `ObjectID` pointeur, qui stocke la chaîne de caractères larges.  
  
## <a name="remarks"></a>Remarques  

 Les chaînes peuvent ou non se terminer par un caractère null.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo3, interface](icorprofilerinfo3-interface.md)
- [Interfaces de profilage](profiling-interfaces.md)
