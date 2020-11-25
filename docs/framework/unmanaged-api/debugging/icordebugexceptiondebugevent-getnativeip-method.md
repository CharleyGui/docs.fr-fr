---
title: ICorDebugExceptionDebugEvent::GetNativeIP, méthoded
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
ms.openlocfilehash: f3b29b3ceda521afe9543588af332531aa03e84e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697413"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a>ICorDebugExceptionDebugEvent::GetNativeIP, méthoded

Obtient le pointeur d'instruction natif de cet événement de débogage d'exception.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pIP`  
 [out] Pointeur vers le pointeur d'instruction de cet événement de débogage d'exception. Pour plus d'informations, consultez la section Notes.  
  
## <a name="remarks"></a>Remarques  

 La signification de ce pointeur d'instruction varie selon le type d'événement, comme indiqué dans le tableau suivant.  
  
|Type d'événement|Signification de la valeur `pStackPointer`|  
|----------------|--------------------------------------|  
|[MANAGED_EXCEPTION_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|Adresse de l'instruction défaillante.|  
|[MANAGED_EXCEPTION_USER_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|Adresse de code dans le frame indiquée par la méthode [getstackpointer,](icordebugexceptiondebugevent-getstackpointer-method.md) où l’exécution reprend si aucune exception n’a été levée. L'exception peut provoquer ou non l'exécution de code différent, comme le bloc catch d'une clause `try/catch/finally`, dans ce frame.|  
|[MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](cordebugrecordformat-enumeration.md)|L’adresse de code où l' `catch` exécution du gestionnaire démarrera dans le frame indiqué par la méthode [getstackpointer,](icordebugexceptiondebugevent-getstackpointer-method.md) .|  
|[MANAGED_EXCEPTION_UNHANDLED](cordebugrecordformat-enumeration.md)|`pIP` est égal à 0.|  
  
 Le type d’événement est disponible à partir de la méthode [ICorDebugDebugEvent :: GetEventKind](icordebugdebugevent-geteventkind-method.md) .  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugExceptionDebugEvent, interface](icordebugexceptiondebugevent-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
