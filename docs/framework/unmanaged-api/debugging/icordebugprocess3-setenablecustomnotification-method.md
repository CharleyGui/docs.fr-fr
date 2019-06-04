---
title: ICorDebugProcess3::SetEnableCustomNotification, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3.SetEnableCustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3::SetEnableCustomNotification
helpviewer_keywords:
- ICorDebugProcess3::SetEnableCustomNotification method [.NET Framework debugging]
- SetEnableCustomNotification method [.NET Framework debugging]
ms.assetid: afd88ee9-2589-4461-a75a-9b6fe55a2525
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c98084b179d27e97ecb3bb34525967d41f8ad1cb
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489615"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a>ICorDebugProcess3::SetEnableCustomNotification, méthode
Active et désactive les notifications de débogueur personnalisées du type spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pClass`  
 [in] Type qui spécifie les notifications de débogueur personnalisées.  
  
 `fEnable`  
 [in] `true` pour activer les notifications de débogueur personnalisées ; `false` pour désactiver les notifications. La valeur par défaut est `false`.  
  
## <a name="remarks"></a>Notes  
 Lorsque `fEnable` a la valeur `true`, les appels à la <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> déclencheur de la méthode un [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) rappel. Notifications sont désactivées par défaut ; Par conséquent, le débogueur doit spécifier les types de notification qu’il connaît et souhaite gérer. Étant donné que le [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) classe est délimitée par le domaine d’application, le débogueur doit appeler `SetEnableCustomNotification` pour chaque domaine d’application dans le processus s’il souhaite recevoir la notification de l’ensemble du processus.  
  
 À compter de .NET Framework 4, la seule notification pris en charge est une notification de dépendance inter-threads.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugProcess3, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)
- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
