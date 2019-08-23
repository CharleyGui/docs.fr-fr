---
title: ICorDebugNativeFrame, interface
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame
helpviewer_keywords:
- ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c01346b42fff812f8358482ae0e8570c03ee9231
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912799"
---
# <a name="icordebugnativeframe-interface"></a>ICorDebugNativeFrame, interface

Implémentation spécialisée de ICorDebugFrame utilisée pour les frames natifs.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CanSetIP, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|Obtient une valeur qui indique s’il est possible de définir en toute sécurité le pointeur d’instruction à l’emplacement d’offset spécifié en code natif.|  
|[GetIP, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|Obtient l’offset du frame de pile en code natif.|  
|[GetLocalDoubleRegisterValue, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|Obtient un pointeur vers un ICorDebugValue qui représente la valeur d’un argument ou d’une variable locale stockée dans deux registres de mémoire d’un frame natif.|  
|[GetLocalMemoryRegisterValue, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|Obtient un pointeur vers un `ICorDebugValue` qui représente la valeur d’une variable locale, dont les bits de poids faible sont stockés dans le registre spécifié et les bits élevés sont stockés à l’adresse mémoire spécifiée.|  
|[GetLocalMemoryValue, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|Obtient un pointeur vers un `ICorDebugValue` qui représente la valeur d’une variable locale stockée à l’adresse mémoire spécifiée.|  
|[GetLocalRegisterMemoryValue, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|Obtient un pointeur vers un `ICorDebugValue` qui représente la valeur d’une variable locale, dont les bits élevés sont stockés dans le registre spécifié et les bits de poids faible sont stockés à l’adresse mémoire spécifiée.|  
|[GetLocalRegisterValue, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|Obtient un pointeur vers un `ICorDebugValue` qui représente la valeur d’un argument ou d’une variable locale stockée dans le registre natif spécifié.|  
|[GetRegisterSet, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|Obtient un pointeur vers un [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) qui représente le jeu de registres pour `ICorDebugNativeFrame`ce.|  
|[SetIP, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|Définit le pointeur d’instruction à l’emplacement d’offset spécifié en code natif.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl, CorDebug. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
