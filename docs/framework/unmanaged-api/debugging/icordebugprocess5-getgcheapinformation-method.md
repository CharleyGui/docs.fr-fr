---
title: ICorDebugProcess5::GetGCHeapInformation, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetGCHeapInformation
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type:
- apiref
ms.openlocfilehash: 43054a71445193bae7a74e0ed6785cccd1d02dc2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95670990"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a>ICorDebugProcess5::GetGCHeapInformation, méthode

Fournit des informations générales sur le tas garbage collection, y compris s’il est actuellement énumérable.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pHeapInfo`  
 à Pointeur vers une valeur [COR_HEAPINFO](cor-heapinfo-structure.md) qui fournit des informations générales sur le tas garbage collection.  
  
## <a name="remarks"></a>Remarques  

 La `ICorDebugProcess5::GetGCHeapInformation` méthode doit être appelée avant d’énumérer le tas ou les régions de tas individuelles pour garantir que les structures de garbage collection dans le processus sont actuellement valides. Le tas garbage collection ne peut pas être parcouru tant qu’une collection est en cours. Dans le cas contraire, l’énumération peut capturer des structures de garbage collection qui ne sont pas valides.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugProcess5, interface](icordebugprocess5-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
