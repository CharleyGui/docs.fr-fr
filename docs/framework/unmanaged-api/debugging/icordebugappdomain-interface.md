---
title: ICorDebugAppDomain, interface
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
ms.openlocfilehash: 9abcb765357a0f305ae5acae77a4a13b07a003a3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134688"
---
# <a name="icordebugappdomain-interface"></a>ICorDebugAppDomain, interface

Fournit des méthodes pour le débogage de domaines d'application. This interface is a subclass of ICorDebugController.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Attach, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|Attaches the debugger to the application domain.|  
|[EnumerateAssemblies, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|Gets an enumerator for the assemblies in the application domain.|  
|[EnumerateBreakpoints, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|Gets an enumerator for all active breakpoints in the application domain.|  
|[EnumerateSteppers, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|Gets an enumerator for all active steppers in the application domain.|  
|[GetID, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|Gets the unique ID of the application domain.|  
|[GetModuleFromMetaDataInterface, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|Gets the ICorDebugModule object with the given metadata interface.|  
|[GetName, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|Gets the name of the application domain.|  
|[GetObject, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|Gets an interface pointer to the common language runtime (CLR) application domain.|  
|[GetProcess, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|Gets the process containing the application domain.|  
|[IsAttached, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|Determines whether the debugger is attached to the application domain.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
