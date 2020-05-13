---
title: ICorDebugModule::IsInMemory, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsInMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsInMemory
helpviewer_keywords:
- IsInMemory method [.NET Framework debugging]
- ICorDebugModule::IsInMemory method [.NET Framework debugging]
ms.assetid: 89940711-98e7-4aa6-bffc-5e39e91e1b7d
topic_type:
- apiref
ms.openlocfilehash: c5fa55a84ed8907a5072f6099c3bf02cd6d78683
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213125"
---
# <a name="icordebugmoduleisinmemory-method"></a>ICorDebugModule::IsInMemory, méthode
Obtient une valeur qui indique si ce module existe uniquement en mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pInMemory`  
 [out] `true` Si ce module existe uniquement en mémoire ; Sinon, `false` .  
  
## <a name="remarks"></a>Remarks  
 Le common language runtime (CLR) prend en charge le chargement de modules à partir de flux bruts d’octets. Ces modules sont appelés *modules en mémoire* et n’existent pas sur le disque.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi
