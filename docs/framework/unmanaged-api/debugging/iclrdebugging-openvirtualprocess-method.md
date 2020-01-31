---
title: ICLRDebugging::OpenVirtualProcess, méthode
ms.date: 03/30/2017
api_name:
- ICLRDebugging.OpenVirtualProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::OpenVirtualProcess
helpviewer_keywords:
- OpenVirtualProcess method [.NET Framework debugging]
- ICLRDebugging::OpenVirtualProcess method [.NET Framework debugging]
ms.assetid: e8ab7c41-d508-4ed9-8a31-ead072b5a314
topic_type:
- apiref
ms.openlocfilehash: 585b3d605d0df9169c12ca10198846ec0a7fe6d4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793608"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a>ICLRDebugging::OpenVirtualProcess, méthode
Obtient l’interface ICorDebugProcess qui correspond à un module common language runtime (CLR) chargé dans le processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OpenVirtualProcess(  
    [in] ULONG64 moduleBaseAddress,  
    [in] IUnknown * pDataTarget,  
    [in] ICLRDebuggingLibraryProvider * pLibraryProvider,  
    [in] CLR_DEBUGGING_VERSION * pMaxDebuggerSupportedVersion,  
    [in] REFIID riidProcess,  
    [out, iid_is(riidProcess)] IUnknown ** ppProcess,  
    [in, out] CLR_DEBUGGING_VERSION * pVersion,  
    [out] CLR_DEBUGGING_PROCESS_FLAGS * pdwFlags);  
```  
  
## <a name="parameters"></a>Parameters  
 `moduleBaseAddress`  
 dans Adresse de base d’un module dans le processus cible. COR_E_NOT_CLR est retourné si le module spécifié n’est pas un module CLR.  
  
 `pDataTarget`  
 dans Abstraction de cible de données qui permet au débogueur managé d’inspecter l’état du processus. Le débogueur doit implémenter l’interface [ICorDebugDataTarget](icordebugdatatarget-interface.md) . Vous devez implémenter l’interface [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) pour prendre en charge les scénarios où le CLR qui est débogué n’est pas installé localement sur l’ordinateur.  
  
 `pLibraryProvider`  
 dans Interface de rappel de fournisseur de bibliothèque qui permet de localiser et de charger des bibliothèques de débogage spécifiques à la version à la demande. Ce paramètre est obligatoire uniquement si `ppProcess` ou `pFlags` n’est pas `null`.  
  
 `pMaxDebuggerSupportedVersion`  
 dans Version la plus récente du CLR que ce débogueur peut déboguer. Vous devez spécifier les versions majeure, mineure et de build de la dernière version du CLR que ce débogueur prend en charge, et définir le numéro de révision sur 65535 pour prendre en charge les futures versions de maintenance du CLR sur place.  
  
 `riidProcess`  
 dans ID de l’interface ICorDebugProcess à récupérer. Actuellement, les seules valeurs acceptées sont IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2 et IID_CORDEBUGPROCESS.  
  
 `ppProcess`  
 à Pointeur vers l’interface COM qui est identifiée par `riidProcess`.  
  
 `pVersion`  
 [in, out] Version du CLR. En entrée, cette valeur peut être `null`. Il peut également pointer vers une structure [CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) , auquel cas le champ `wStructVersion` de la structure doit être initialisé à 0 (zéro).  
  
 Lors de la sortie, la structure `CLR_DEBUGGING_VERSION` retournée est renseignée avec les informations de version du CLR.  
  
 `pdwFlags`  
 à Indicateurs d’information sur le runtime spécifié. Pour obtenir une description des indicateurs, consultez la rubrique [CLR_DEBUGGING_PROCESS_FLAGS](clr-debugging-process-flags-enumeration.md) .  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La méthode s'est correctement terminée.|  
|E_POINTER|`pDataTarget` est `null`.|  
|CORDBG_E_LIBRARY_PROVIDER_ERROR|Le rappel [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) retourne une erreur ou ne fournit pas de handle valide.|  
|CORDBG_E_MISSING_DATA_TARGET_INTERFACE|`pDataTarget` n’implémente pas les interfaces cibles de données requises pour cette version du Runtime.|  
|CORDBG_E_NOT_CLR|Le module indiqué n’est pas un module CLR. Ce HRESULT est également retourné lorsqu’un module CLR ne peut pas être détecté parce que la mémoire a été endommagée, que le module n’est pas disponible ou que la version du CLR est ultérieure à la version du shim.|  
|CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL|Cette version du runtime ne prend pas en charge ce modèle de débogage. Actuellement, le modèle de débogage n’est pas pris en charge par les versions CLR antérieures au .NET Framework 4. Le paramètre de sortie `pwszVersion` est toujours défini sur la valeur correcte après cette erreur.|  
|CORDBG_E_UNSUPPORTED_FORWARD_COMPAT|La version du CLR est supérieure à la version que ce débogueur prétend prendre en charge. Le paramètre de sortie `pwszVersion` est toujours défini sur la valeur correcte après cette erreur.|  
|E_NO_INTERFACE|L’interface `riidProcess` n’est pas disponible.|  
|CORDBG_E_UNSUPPORTED_VERSION_STRUCT|La structure `CLR_DEBUGGING_VERSION` n’a pas de valeur reconnue pour `wStructVersion`. La seule valeur acceptée pour l’instant est 0.|  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
