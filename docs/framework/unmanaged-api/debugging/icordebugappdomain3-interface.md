---
title: ICorDebugAppDomain3, interface
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3
helpviewer_keywords:
- ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 875ef5be-c1e7-4d95-97e9-d3a667aeaba0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3676cb32ceaf6f241672751f0feafbd3cb83e05
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968874"
---
# <a name="icordebugappdomain3-interface"></a>ICorDebugAppDomain3, interface
Fournit des méthodes pour récupérer des informations sur les représentations managées des types de Windows Runtime actuellement chargés dans un domaine d’application. Cette interface est une extension des interfaces ICorDebugAppDomain et ICorDebugAppDomain2.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|Obtient un énumérateur pour tous les types de Windows Runtime mis en cache.|  
|[ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|Obtient un énumérateur pour les types de Windows Runtime mis en cache dans un domaine d’application en fonction de leurs identificateurs d’interface.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est destinée à être utilisée par un débogueur conjointement à un appel d’évaluation de fonction `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`à. Quand la méthode récupère les identificateurs d’interface pris en charge par un objet Windows Runtime Server, le débogueur peut utiliser les méthodes définies dans cette interface pour les mapper aux types managés qui correspondent à ces interfaces.  
  
 Pour récupérer une instance de cette interface, exécutez `QueryInterface` sur une instance de l’interface ICorDebugAppDomain ou ICorDebugAppDomain2.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Windows Runtime  
  
 **En-tête :** CorDebug. idl, CorDebug. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
