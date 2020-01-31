---
title: ICorDebugVariableHomeEnum, interface
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum
helpviewer_keywords:
- ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: c312ae6d-c8dc-48d6-9f1e-ead515c88fdf
topic_type:
- apiref
ms.openlocfilehash: 74b3c7bed54f3735efbd5d2c56962d427518f71a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790950"
---
# <a name="icordebugvariablehomeenum-interface"></a>ICorDebugVariableHomeEnum, interface
Fournit un énumérateur aux variables locales et aux arguments dans une fonction.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next, méthode](icordebugvariablehomeenum-next-method.md)|Obtient le nombre spécifié d’instances [ICorDebugVariableHome](icordebugvariablehome-interface.md) qui contiennent des informations sur les variables locales et les arguments d’une fonction.|  
  
## <a name="remarks"></a>Notes  
 L’interface `ICorDebugVariableHomeEnum` implémente l’interface ICorDebugEnum.  
  
 Une instance de `ICorDebugVariableHomeEnum` est remplie avec des instances [ICorDebugVariableHome](icordebugvariablehome-interface.md) en appelant la méthode [ICorDebugCode4 :: EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md) . Chaque instance [ICorDebugVariableHome](icordebugvariablehome-interface.md) de la collection représente une variable locale ou un argument dans une fonction. Les objets [ICorDebugVariableHome](icordebugvariablehome-interface.md) de la collection peuvent être énumérés en appelant la méthode [ICorDebugVariableHomeEnum :: Next](icordebugvariablehomeenum-next-method.md) .  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugVariableHome, interface](icordebugvariablehome-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
