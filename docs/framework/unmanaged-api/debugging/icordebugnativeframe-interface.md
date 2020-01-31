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
ms.openlocfilehash: 41ac0b29ade2f78b893df72e8a17624373f6dd78
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792788"
---
# <a name="icordebugnativeframe-interface"></a>ICorDebugNativeFrame, interface

Implémentation spécialisée de ICorDebugFrame utilisée pour les frames natifs.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CanSetIP, méthode](icordebugnativeframe-cansetip-method.md)|Obtient une valeur qui indique s’il est possible de définir en toute sécurité le pointeur d’instruction à l’emplacement d’offset spécifié en code natif.|  
|[GetIP, méthode](icordebugnativeframe-getip-method.md)|Obtient l’offset du frame de pile en code natif.|  
|[GetLocalDoubleRegisterValue, méthode](icordebugnativeframe-getlocaldoubleregistervalue-method.md)|Obtient un pointeur vers un ICorDebugValue qui représente la valeur d’un argument ou d’une variable locale stockée dans deux registres de mémoire d’un frame natif.|  
|[GetLocalMemoryRegisterValue, méthode](icordebugnativeframe-getlocalmemoryregistervalue-method.md)|Obtient un pointeur vers un `ICorDebugValue` qui représente la valeur d’une variable locale, dont les bits de poids faible sont stockés dans le registre spécifié et les bits élevés sont stockés à l’adresse mémoire spécifiée.|  
|[GetLocalMemoryValue, méthode](icordebugnativeframe-getlocalmemoryvalue-method.md)|Obtient un pointeur vers un `ICorDebugValue` qui représente la valeur d’une variable locale stockée à l’adresse mémoire spécifiée.|  
|[GetLocalRegisterMemoryValue, méthode](icordebugnativeframe-getlocalregistermemoryvalue-method.md)|Obtient un pointeur vers un `ICorDebugValue` qui représente la valeur d’une variable locale, dont les bits élevés sont stockés dans le registre spécifié et les bits de poids faible sont stockés à l’adresse mémoire spécifiée.|  
|[GetLocalRegisterValue, méthode](icordebugnativeframe-getlocalregistervalue-method.md)|Obtient un pointeur vers un `ICorDebugValue` qui représente la valeur d’un argument ou d’une variable locale stockée dans le registre natif spécifié.|  
|[GetRegisterSet, méthode](icordebugnativeframe-getregisterset-method.md)|Obtient un pointeur vers un [ICorDebugRegisterSet](icordebugregisterset-interface.md) qui représente le jeu de registres pour ce `ICorDebugNativeFrame`.|  
|[SetIP, méthode](icordebugnativeframe-setip-method.md)|Définit le pointeur d’instruction à l’emplacement d’offset spécifié en code natif.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
