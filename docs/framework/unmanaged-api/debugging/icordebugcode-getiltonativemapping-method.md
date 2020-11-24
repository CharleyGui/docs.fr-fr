---
title: ICorDebugCode::GetILToNativeMapping, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetILToNativeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetILToNativeMapping method [.NET Framework debugging]
ms.assetid: a8ecd8c8-9627-4356-9c6f-bd05e24637c0
topic_type:
- apiref
ms.openlocfilehash: 0adb9e58ca2c6b5b430a0413fa11ba59d79a0539
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688105"
---
# <a name="icordebugcodegetiltonativemapping-method"></a>ICorDebugCode::GetILToNativeMapping, méthode

Obtient un tableau d’instances de « COR_DEBUG_IL_TO_NATIVE_MAP » qui représentent des mappages de décalages MSIL (Microsoft Intermediate Language) aux offsets natifs.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `cMap`  
 [in] Taille du tableau `map`.  
  
 `pcMap`  
 à Pointeur vers le nombre réel d’éléments retournés dans le `map` tableau.  
  
 `map`  
 à Tableau de `COR_DEBUG_IL_TO_NATIVE_MAP` structures, chacune représentant un mappage d’un offset MSIL à un offset natif.  
  
 Il n’y a aucun classement pour le tableau d’éléments retournés.  
  
## <a name="remarks"></a>Remarques  

 La `GetILToNativeMapping` méthode retourne des résultats significatifs uniquement si cette instance « ICorDebugCode » représente du code natif qui était compilé juste-à-temps (JIT) à partir du code MSIL.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugCode, interface](icordebugcode-interface1.md)
