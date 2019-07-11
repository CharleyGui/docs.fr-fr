---
title: ICorDebugNativeFrame::SetIP, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::SetIP
helpviewer_keywords:
- ICorDebugNativeFrame::SetIP method [.NET Framework debugging]
- SetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 57784a51-c76d-48f8-9392-584d0e1946d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc442e0bcd8d392041284269e46821e0642d0891
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765886"
---
# <a name="icordebugnativeframesetip-method"></a>ICorDebugNativeFrame::SetIP, méthode
Définit le pointeur d’instruction à l’emplacement de décalage spécifié dans le code natif.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `nOffset`  
 [in] Emplacement de décalage dans le code natif.  
  
## <a name="remarks"></a>Notes  
 Les appels à `SetIP` invalider immédiatement tous les frames et des chaînes pour le thread actuel. Si le débogueur a besoin des informations de frame après un appel à `SetIP`, il doit effectuer une nouvelle trace de pile.  
  
 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) essaiera de conserver le frame de pile dans un état valide. Toutefois, même si le frame est dans un état valide, autant que le runtime est concerné, il reste peut-être des problèmes, tels que des variables locales non initialisées et ainsi de suite. L’appelant est responsable de la cohérence du programme en cours d’exécution.  
  
 Sur les plateformes 64 bits, le pointeur d’instruction ne peut pas être déplacé hors d’un `catch` ou `finally` bloc. Si `SetIP` est appelée pour effectuer ce déplacement sur une plateforme 64 bits, il retourne un HRESULT indiquant un échec.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi
