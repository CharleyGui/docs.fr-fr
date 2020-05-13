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
ms.openlocfilehash: dd87745a29514a2f9f05aa142baae4e05d4b4a7b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206595"
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
|[GetRegisterSet, méthode](icordebugnativeframe-getregisterset-method.md)|Obtient un pointeur vers un [ICorDebugRegisterSet](icordebugregisterset-interface.md) qui représente le jeu de registres pour ce `ICorDebugNativeFrame` .|  
|[SetIP, méthode](icordebugnativeframe-setip-method.md)|Définit le pointeur d’instruction à l’emplacement d’offset spécifié en code natif.|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
