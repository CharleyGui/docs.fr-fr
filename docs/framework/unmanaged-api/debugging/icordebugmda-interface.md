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
ms.openlocfilehash: d711f36b4e2071dac9458a023e1d3cf4743e77b3
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212631"
---
# <a name="icordebugmda-interface"></a>ICorDebugMDA, interface
Représente un message d'Assistant Débogage managé (MDA).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetDescription, méthode](icordebugmda-getdescription-method.md)|Obtient une chaîne contenant une description de cet Assistant Débogage managé.|  
|[GetFlags, méthode](icordebugmda-getflags-method.md)|Obtient les indicateurs associés à cet Assistant Débogage managé.|  
|[GetName, méthode](icordebugmda-getname-method.md)|Obtient une chaîne contenant le nom de cet Assistant Débogage managé.|  
|[GetOSThreadId, méthode](icordebugmda-getosthreadid-method.md)|Obtient l’identificateur de thread de système d’exploitation sur lequel cet Assistant Débogage managé s’exécute.|  
|[GetXML, méthode](icordebugmda-getxml-method.md)|Obtient le flux de données XML complet associé à cet Assistant Débogage managé.|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Diagnostic d’erreurs avec les Assistants Débogage managé](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
