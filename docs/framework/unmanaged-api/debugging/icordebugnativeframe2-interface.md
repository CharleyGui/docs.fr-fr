---
title: ICorDebugNativeFrame2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2
helpviewer_keywords:
- ICorDebugNativeFrame2 interface [.NET Framework debugging]
ms.assetid: 52a80838-af36-4399-bc97-d8a4c6d76df2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 638ce7933ededf2ff7b03b1c5aed7f6bdbfebc6c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912794"
---
# <a name="icordebugnativeframe2-interface"></a>ICorDebugNativeFrame2, interface
Fournit des méthodes qui testent les relations entre frames enfant et parent.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[IsChild, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ischild-method.md)|Détermine si le frame actuel est un Frame enfant.|  
|[IsMatchingParentFrame, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)|Détermine si le frame spécifié est le parent du frame actuel.|  
|[GetStackParameterSize, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-getstackparametersize-method.md)|Retourne la taille cumulée des paramètres sur la pile sur les systèmes d’exploitation x86.|  
  
## <a name="remarks"></a>Notes  
 Cette interface étend logiquement l’interface «ICorDebugNativeFrame».  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl, CorDebug. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
