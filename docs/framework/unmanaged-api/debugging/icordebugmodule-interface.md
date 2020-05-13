---
title: ICorDebugModule, interface
ms.date: 03/30/2017
api_name:
- ICorDebugModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule
helpviewer_keywords:
- ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type:
- apiref
ms.openlocfilehash: 105e56f2508eabbb6876a09d35e6abfbfc08950b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212241"
---
# <a name="icordebugmodule-interface"></a>ICorDebugModule, interface

Représente un module common language runtime (CLR), qui est un fichier exécutable ou une bibliothèque de liens dynamiques (DLL).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CreateBreakpoint, méthode](icordebugmodule-createbreakpoint-method.md)|Non implémenté.|  
|[EnableClassLoadCallbacks, méthode](icordebugmodule-enableclassloadcallbacks-method.md)|Détermine si les rappels [ICorDebugManagedCallback :: LoadClass](icordebugmanagedcallback-loadclass-method.md) et [ICorDebugManagedCallback :: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) sont appelés pour ce module.|  
|[EnableJITDebugging, méthode](icordebugmodule-enablejitdebugging-method.md)|Détermine si le compilateur juste-à-temps (JIT) préserve les informations de débogage pour les méthodes dans ce module.|  
|[GetAssembly, méthode](icordebugmodule-getassembly-method.md)|Obtient l’assembly conteneur pour ce module.|  
|[GetBaseAddress, méthode](icordebugmodule-getbaseaddress-method.md)|Obtient l’adresse de base du module.|  
|[GetClassFromToken, méthode](icordebugmodule-getclassfromtoken-method.md)|Obtient la ICorDebugClass à partir des métadonnées.|  
|[GetEditAndContinueSnapshot, méthode](icordebugmodule-geteditandcontinuesnapshot-method.md)|Action déconseillée.|  
|[GetFunctionFromRVA, méthode](icordebugmodule-getfunctionfromrva-method.md)|Non implémenté.|  
|[GetFunctionFromToken, méthode](icordebugmodule-getfunctionfromtoken-method.md)|Obtient la fonction spécifiée par le jeton de métadonnées.|  
|[GetGlobalVariableValue, méthode](icordebugmodule-getglobalvariablevalue-method.md)|Obtient un objet de valeur pour la variable globale spécifiée.|  
|[GetMetaDataInterface, méthode](icordebugmodule-getmetadatainterface-method.md)|Obtient un pointeur d’interface de métadonnées qui peut être utilisé pour examiner les métadonnées du module.|  
|[GetName, méthode](icordebugmodule-getname-method.md)|Obtient le nom de fichier du module.|  
|[GetProcess, méthode](icordebugmodule-getprocess-method.md)|Obtient le processus conteneur pour ce module.|  
|[GetSize, méthode](icordebugmodule-getsize-method.md)|Obtient la taille du module en octets.|  
|[GetToken, méthode](icordebugmodule-gettoken-method.md)|Obtient le jeton pour l’entrée de table pour ce module.|  
|[IsDynamic, méthode](icordebugmodule-isdynamic-method.md)|Indique si le module est dynamique.|  
|[IsInMemory, méthode](icordebugmodule-isinmemory-method.md)|Indique si ce module existe uniquement en mémoire.|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebug, interface](icordebug-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
