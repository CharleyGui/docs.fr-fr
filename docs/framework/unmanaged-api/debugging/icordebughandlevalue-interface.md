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
ms.openlocfilehash: e695a93036e00e651ecababb0e1407661bcc48d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729081"
---
# <a name="icordebughandlevalue-interface"></a>ICorDebugHandleValue, interface

Sous-classe de ICorDebugReferenceValue qui représente une valeur de référence dans laquelle le débogueur a créé un handle pour garbage collection.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Dispose, méthode](icordebughandlevalue-dispose-method.md)|Libère le handle référencé par cet `ICorDebugHandleValue` objet sans libérer explicitement le pointeur d’interface.|  
|[GetHandleType, méthode](icordebughandlevalue-gethandletype-method.md)|Obtient une valeur CorDebugHandleType, qui décrit le genre de handle référencé par ce `ICorDebugHandleValue` .|  
  
## <a name="remarks"></a>Remarques  

 Un `ICorDebugReferenceValue` objet est invalidé par un arrêt dans l’exécution du code débogué. Un `ICorDebugHandleValue` maintient sa référence via des arrêts et des continuations, jusqu’à ce qu’il soit explicitement libéré.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
