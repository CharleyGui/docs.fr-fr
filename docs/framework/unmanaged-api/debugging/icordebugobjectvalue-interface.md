---
title: ICorDebugObjectValue, interface
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue
helpviewer_keywords:
- ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type:
- apiref
ms.openlocfilehash: e104f8c522af2ee4cd42332b7459f4a2fd185511
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792689"
---
# <a name="icordebugobjectvalue-interface"></a>ICorDebugObjectValue, interface

Sous-classe de « ICorDebugValue » qui représente une valeur qui contient un objet.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetClass, méthode](icordebugobjectvalue-getclass-method.md)|Obtient un pointeur d’interface vers le common language runtime (CLR) <xref:System.Type> de l’objet référencé par ce `ICorDebugObjectValue`.|  
|[GetContext, méthode](icordebugobjectvalue-getcontext-method.md)|Non implémenté.|  
|[GetFieldValue, méthode](icordebugobjectvalue-getfieldvalue-method.md)|Obtient un pointeur d’interface vers un [ICorDebugValue](icordebugvalue-interface.md) qui représente la valeur du champ spécifié de la classe spécifiée.|  
|[GetManagedCopy, méthode](icordebugobjectvalue-getmanagedcopy-method.md)|Obsolète. N'appelez pas cette méthode.|  
|[GetVirtualMethod, méthode](icordebugobjectvalue-getvirtualmethod-method.md)|Non implémenté.|  
|[IsValueClass, méthode](icordebugobjectvalue-isvalueclass-method.md)|Obtient une valeur qui indique si l’objet référencé par ce `ICorDebugObjectValue` est un type valeur.|  
|[SetFromManagedCopy, méthode](icordebugobjectvalue-setfrommanagedcopy-method.md)|Obsolète. N'appelez pas cette méthode.|  
  
## <a name="remarks"></a>Notes  
 Une `ICorDebugObjectValue` reste valide jusqu’à ce que le processus en cours de débogage se poursuive.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
