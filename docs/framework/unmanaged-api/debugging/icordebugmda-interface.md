---
title: ICorDebugMDA, interface
ms.date: 03/30/2017
api_name:
- ICorDebugMDA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA
helpviewer_keywords:
- ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type:
- apiref
ms.openlocfilehash: 4201fe23bf54388510088e21471edce91809e94c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129796"
---
# <a name="icordebugmda-interface"></a>ICorDebugMDA, interface
Représente un message d'Assistant Débogage managé (MDA).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetDescription, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|Obtient une chaîne contenant une description de cet Assistant Débogage managé.|  
|[GetFlags, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|Obtient les indicateurs associés à cet Assistant Débogage managé.|  
|[GetName, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|Obtient une chaîne contenant le nom de cet Assistant Débogage managé.|  
|[GetOSThreadId, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|Obtient l’identificateur de thread de système d’exploitation sur lequel cet Assistant Débogage managé s’exécute.|  
|[GetXML, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|Obtient le flux de données XML complet associé à cet Assistant Débogage managé.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Diagnostic d’erreurs avec les Assistants Débogage managé](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
