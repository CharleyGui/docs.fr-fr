---
title: ICorDebugProcess6::DecodeEvent, méthode
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
ms.openlocfilehash: a0b77724a5a70461073d554a9794c5a904f6a363
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178579"
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
 [dans] Un membre [corDebugRecordFormat](cordebugrecordformat-enumeration.md) énumération qui spécifie le format de l’événement de débogé non galé.  
  
 `dwFlags`  
 [in] Champ de bits qui dépend de l'architecture cible et qui spécifie des informations supplémentaires sur l'événement de débogage. Pour les systèmes Windows, il peut être membre du recensement [de CorDebugDecodeEventFlagsWindows.](cordebugdecodeeventflagswindows-enumeration.md)  
  
 `dwThreadId`  
 [in] Identificateur de système d'exploitation du thread sur lequel l'exception a été levée.  
  
 `ppEvent`  
 [out] Un pointeur à l’adresse d’un objet [ICorDebugDebugEvent](icordebugdebugevent-interface.md) qui représente un événement de débogé géré décodé.  
  
## <a name="remarks"></a>Notes   
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugProcess6, interface](icordebugprocess6-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
