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
ms.openlocfilehash: 603ab20b57dc4ba736b0342797d0be649a5bebc4
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207484"
---
# <a name="icordebugobjectvalue-interface"></a>ICorDebugObjectValue, interface

Sous-classe de « ICorDebugValue » qui représente une valeur qui contient un objet.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetClass, méthode](icordebugobjectvalue-getclass-method.md)|Obtient un pointeur d’interface vers le common language runtime (CLR) <xref:System.Type> de l’objet référencé par ce `ICorDebugObjectValue` .|  
|[GetContext, méthode](icordebugobjectvalue-getcontext-method.md)|Non implémenté.|  
|[GetFieldValue, méthode](icordebugobjectvalue-getfieldvalue-method.md)|Obtient un pointeur d’interface vers un [ICorDebugValue](icordebugvalue-interface.md) qui représente la valeur du champ spécifié de la classe spécifiée.|  
|[GetManagedCopy, méthode](icordebugobjectvalue-getmanagedcopy-method.md)|Obsolète. N'appelez pas cette méthode.|  
|[GetVirtualMethod, méthode](icordebugobjectvalue-getvirtualmethod-method.md)|Non implémenté.|  
|[IsValueClass, méthode](icordebugobjectvalue-isvalueclass-method.md)|Obtient une valeur qui indique si l’objet référencé par ce `ICorDebugObjectValue` est un type valeur.|  
|[SetFromManagedCopy, méthode](icordebugobjectvalue-setfrommanagedcopy-method.md)|Obsolète. N'appelez pas cette méthode.|  
  
## <a name="remarks"></a>Remarks  
 Un `ICorDebugObjectValue` reste valide jusqu’à ce que le processus en cours de débogage se poursuive.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
