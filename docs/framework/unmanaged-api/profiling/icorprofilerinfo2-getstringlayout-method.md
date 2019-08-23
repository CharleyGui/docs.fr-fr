---
title: ICorProfilerInfo2::GetStringLayout, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStringLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 63ad2532240c9f18a00421281fae0d111dbfaec5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963793"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a>ICorProfilerInfo2::GetStringLayout, méthode
Obtient des informations sur la disposition d'un objet string. Cette méthode est déconseillée dans le .NET Framework 4 et est remplacée par la méthode [ICorProfilerInfo3:: GetStringLayout2,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pBufferLengthOffset`  
 à Pointeur vers le décalage de l’emplacement, relatif au `ObjectID` pointeur, qui stocke la longueur de la chaîne. La longueur est stockée sous `DWORD`la forme d’un.  
  
> [!NOTE]
> Ce paramètre retourne la longueur de la chaîne elle-même, pas la longueur de la mémoire tampon. La longueur de la mémoire tampon n’est plus disponible.  
  
 `PStringLengthOffset`  
 à Pointeur vers le décalage de l’emplacement, relatif au `ObjectID` pointeur, qui stocke la longueur de la chaîne elle-même. La longueur est stockée sous `DWORD`la forme d’un.  
  
 `pBufferOffset`  
 à Pointeur vers l’offset de la mémoire tampon, relatif au `ObjectID` pointeur, qui stocke la chaîne de caractères larges.  
  
## <a name="remarks"></a>Notes  
 La `GetStringLayout` méthode obtient les offsets, par rapport `ObjectID` au pointeur, des emplacements dans lesquels sont stockés les éléments suivants:  
  
- Longueur de la mémoire tampon de la chaîne.  
  
- Longueur de la chaîne elle-même.  
  
- Mémoire tampon qui contient la chaîne réelle de caractères larges.  
  
 Les chaînes peuvent se terminer par un caractère null.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl, CorProf. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
