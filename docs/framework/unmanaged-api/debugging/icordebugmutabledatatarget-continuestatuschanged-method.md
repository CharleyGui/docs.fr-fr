---
title: ICorDebugMutableDataTarget::ContinueStatusChanged, méthode
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
ms.openlocfilehash: 49f517c0c09771ce86e43b801f6d7fce695d907a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213307"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a>ICorDebugMutableDataTarget::ContinueStatusChanged, méthode
Modifie l'état de continuation de l'événement de débogage en suspens sur le thread spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
## <a name="parameters"></a>Paramètres  
 `dwThreadId`  
 Identificateur de thread défini par le système d'exploitation.  
  
 `continueStatus`  
 Valeur [COREDB_CONTINUE_STATUS](../common-data-types-unmanaged-api-reference.md) qui représente le nouvel état de continuation demandé.  
  
## <a name="remarks"></a>Remarks  
 Le débogueur appelle la méthode `ContinueStatusChanged` quand il appelle une méthode ICorDebug qui nécessite une gestion potentiellement anormale de l'événement de débogage actif. Par exemple, si une exception est en suspens et que le débogueur demande une opération susceptible d’annuler l’exception (comme [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) ou `FuncEval`), cette API permet de demander l’annulation de l’exception.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugMutableDataTarget, interface](icordebugmutabledatatarget-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
