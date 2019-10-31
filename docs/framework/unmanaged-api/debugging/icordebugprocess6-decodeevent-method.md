---
title: ICorDebugProcess6::DecodeEvent, méthode
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
ms.openlocfilehash: fd0fba04fe3df0ada8b0b56280906beefb26bb26
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123496"
---
# <a name="icordebugprocess6decodeevent-method"></a>ICorDebugProcess6::DecodeEvent, méthode
Décode les événements de débogage managés qui ont été encapsulés dans la charge utile des événements de débogage d'exception native conçus à cet effet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DecodeEvent(  
        [in, length_is(countBytes), size_is(countBytes)]  const BYTE pRecord[],  
        [in] DWORD countBytes,  
        [in] CorDebugRecordFormat format,  
        [in] DWORD dwFlags,   
        [in] DWORD dwThreadId,   
        [out] ICorDebugDebugEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pRecord`  
 [in] Pointeur vers un tableau d'octets issu d'un événement de débogage d'exception native qui contient des informations sur un événement de débogage managé.  
  
 `countBytes`  
 [in] Nombre d'éléments dans le tableau d'octets `pRecord`.  
  
 `format`  
 dans Membre de l’énumération [cordebugrecordformat,](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md) qui spécifie le format de l’événement de débogage non managé.  
  
 `dwFlags`  
 [in] Champ de bits qui dépend de l'architecture cible et qui spécifie des informations supplémentaires sur l'événement de débogage. Pour les systèmes Windows, il peut s’agir d’un membre de l’énumération [cordebugdecodeeventflagswindows,](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md) .  
  
 `dwThreadId`  
 [in] Identificateur de système d'exploitation du thread sur lequel l'exception a été levée.  
  
 `ppEvent`  
 à Pointeur vers l’adresse d’un objet [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) qui représente un événement de débogage managé décodé.  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugProcess6, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
