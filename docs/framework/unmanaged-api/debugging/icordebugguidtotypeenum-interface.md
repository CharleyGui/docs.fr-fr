---
title: ICorDebugGuidToTypeEnum, interface
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum
helpviewer_keywords:
- ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type:
- apiref
ms.openlocfilehash: 2663e5604cdd55472cc148b2d2b38599df81f11e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794436"
---
# <a name="icordebugguidtotypeenum-interface"></a>ICorDebugGuidToTypeEnum, interface
Fournit un énumérateur qui définit le mappage entre un jeu de GUID et leurs types correspondants, représentés par les instances ICorDebugType. Cette interface hérite des méthodes de l’interface ICorDebugEnum.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ICorDebugGuidToTypeEnum::Next](icordebugguidtotypeenum-next-method.md)|Obtient le nombre spécifié d’instances [cordebugguidtotypemapping,](cordebugguidtotypemapping-structure.md) qui mappent les GUID aux informations de type.|  
  
## <a name="remarks"></a>Notes  
 Un objet d’interface `ICorDebugGuidToTypeEnum` peut être récupéré en appelant la méthode [ICorDebugAppDomain3 :: getcachedwinrttypes,](icordebugappdomain3-getcachedwinrttypes-method.md) . Un débogueur peut appeler la méthode [suivante](icordebugguidtotypeenum-next-method.md) de cette interface pour récupérer des objets [cordebugguidtotypemapping,](cordebugguidtotypemapping-structure.md) qui représentent des mappages de représentations managées de Windows Runtime types chargés dans le domaine d’application utilisé pour l’appel à la méthode [ICorDebugAppDomain3 :: getcachedwinrttypes,](icordebugappdomain3-getcachedwinrttypes-method.md) .  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Windows Runtime  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
