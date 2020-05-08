---
title: ICorDebugExceptionObjectCallStackEnum, interface
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type:
- apiref
ms.openlocfilehash: e6dd951b0f432d455d95bb60f4c42df64d5bee24
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975990"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a>ICorDebugExceptionObjectCallStackEnum, interface
Fournit un énumérateur pour les informations de la pile des appels qui sont incorporées dans un objet exception. Cette interface est une sous-classe de l'interface ICorDebugEnum.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Icordebugexceptionobjectcallstackenum, :: suivant](icordebugexceptionobjectcallstackenum-next-method.md)|Obtient un nombre spécifié d’objets [cordebugexceptionobjectstackframe,](cordebugexceptionobjectstackframe-structure.md) qui contiennent des informations sur la pile des appels d’un objet exception.|  
  
## <a name="remarks"></a>Notes   
 L' `ICorDebugExceptionObjectCallStackEnum` interface implémente l’interface ICorDebugEnum.  
  
 Une `ICorDebugExceptionObjectCallStackEnum` instance est remplie avec des objets [cordebugexceptionobjectstackframe,](cordebugexceptionobjectstackframe-structure.md) en appelant la méthode [icordebugexceptionobjectvalue, :: enumerateexceptioncallstack,](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) . Les éléments de la pile des appels de la collection peuvent être énumérés en appelant la méthode [icordebugexceptionobjectcallstackenum, :: Next](icordebugexceptionobjectcallstackenum-next-method.md)  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
