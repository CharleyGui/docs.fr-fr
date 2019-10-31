---
title: ICorDebugHandleValue, interface
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue
helpviewer_keywords:
- ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type:
- apiref
ms.openlocfilehash: 94472e84b73cdffe09505088b1e7fbc20a209bc3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138480"
---
# <a name="icordebughandlevalue-interface"></a>ICorDebugHandleValue, interface

Sous-classe de ICorDebugReferenceValue qui représente une valeur de référence dans laquelle le débogueur a créé un handle pour garbage collection.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Dispose, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|Libère le handle référencé par cet objet `ICorDebugHandleValue` sans libérer explicitement le pointeur d’interface.|  
|[GetHandleType, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|Obtient une valeur CorDebugHandleType, qui décrit le genre de handle référencé par cet `ICorDebugHandleValue`.|  
  
## <a name="remarks"></a>Notes  
 Un objet `ICorDebugReferenceValue` est invalidé par un arrêt dans l’exécution du code débogué. Un `ICorDebugHandleValue` conserve sa référence par des arrêts et des continuations, jusqu’à ce qu’il soit explicitement libéré.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
