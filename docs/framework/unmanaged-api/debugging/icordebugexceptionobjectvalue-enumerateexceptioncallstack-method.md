---
title: ICorDebugExceptionObjectValue::EnumerateExceptionCallStack, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue.EnumerateExceptionCallStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
helpviewer_keywords:
- EnumerateExceptionCallStack method, ICorDebugExceptionObjectValue interface [.NET Framework debugging]
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack method [.NET Framework debugging]
ms.assetid: 00c64533-15dd-47f4-bb97-fe80a1ebadef
topic_type:
- apiref
ms.openlocfilehash: 57eb284bfe39ce92b2d6c03a2aeb4ae84d6aba91
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788667"
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a>ICorDebugExceptionObjectValue::EnumerateExceptionCallStack, méthode
Obtient un énumérateur de la pile des appels incorporée dans un objet exception.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
## <a name="parameters"></a>Parameters  
 ppCallStackEnum  
 à Pointeur vers l’adresse d’un objet d’interface [icordebugexceptionobjectcallstackenum,](icordebugexceptionobjectcallstackenum-interface.md) qui est un énumérateur de trace de la pile pour un objet exception managée.  
  
## <a name="remarks"></a>Notes  
 Si aucune information de pile des appels n’est disponible, la méthode retourne `S_OK`, et [icordebugexceptionobjectcallstackenum,](icordebugexceptionobjectcallstackenum-interface.md) est un énumérateur valide dont la longueur est égale à 0. Si la méthode ne peut pas récupérer les informations de trace de la pile, la valeur de retour est `E_FAIL` et aucun énumérateur n’est retourné.  
  
 L’objet [icordebugexceptionobjectcallstackenum,](icordebugexceptionobjectcallstackenum-interface.md) est chargé de décoder les données de trace de la pile à partir du champ `_stackTrace` de l’objet exception.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugExceptionObjectValue, interface](icordebugexceptionobjectvalue-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
