---
title: ICorDebugProcess3, interface
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3
helpviewer_keywords:
- ICorDebugProcess3 interface [.NET Framework debugging]
ms.assetid: ced9c82e-d7b0-4806-a151-98b6611d3097
topic_type:
- apiref
ms.openlocfilehash: 826736d2db7aa1e618a2e5fe0655cedad9556b17
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213437"
---
# <a name="icordebugprocess3-interface"></a>ICorDebugProcess3, interface
Contrôle les notifications de débogueur personnalisées.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[SetEnableCustomNotification, méthode](icordebugprocess3-setenablecustomnotification-method.md)|Active et désactive les notifications personnalisées du débogueur du type spécifié.|  
  
## <a name="remarks"></a>Remarks  
 Cette interface étend logiquement les interfaces ICorDebugProcess et ICorDebugProcess2.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
