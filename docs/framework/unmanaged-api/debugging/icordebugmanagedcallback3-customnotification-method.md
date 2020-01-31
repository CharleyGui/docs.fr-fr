---
title: ICorDebugManagedCallback3::CustomNotification, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3.CustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3::CustomNotification
helpviewer_keywords:
- ICorDebugManagedCallback3::CustomNotification method [.NET Framework debugging]
- CustomNotification method [.NET Framework debugging]
ms.assetid: 5e5422ac-afa1-403d-a894-2d7348673e38
topic_type:
- apiref
ms.openlocfilehash: 078f90387a475559067d402610ec264f4076ae01
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793262"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a>ICorDebugManagedCallback3::CustomNotification, méthode
Indique qu’une notification du débogueur personnalisé a été déclenchée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
## <a name="parameters"></a>Parameters  
 `pThread`  
 dans Pointeur vers le thread qui a déclenché la notification.  
  
 `pAppDomain`  
 dans Pointeur vers le domaine d’application qui contient le thread qui a déclenché la notification.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La méthode s'est correctement terminée.|  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Notes  
 Un appel ultérieur à la méthode [ICorDebugThread4 :: GetCurrentCustomDebuggerNotification,](icordebugthread4-getcurrentcustomdebuggernotification-method.md) récupère l’objet thread qui a été passé à la méthode <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType>. Le type de l’objet thread doit avoir été préalablement activé en appelant la méthode [ICorDebugProcess3 :: SetEnableCustomNotification,](icordebugprocess3-setenablecustomnotification-method.md) . Le débogueur peut lire des paramètres spécifiques au type à partir des champs de l’objet thread et peut stocker les réponses dans des champs.  
  
 L’interface [ICorDebug](icordebug-interface.md) n’impose aucune stratégie sur les types de notifications ou leur contenu, et la sémantique des notifications est strictement un contrat entre les débogueurs, les applications et le .NET Framework.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugManagedCallback3, interface](icordebugmanagedcallback3-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
