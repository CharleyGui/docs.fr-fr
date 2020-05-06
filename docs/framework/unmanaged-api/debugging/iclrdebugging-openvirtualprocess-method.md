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
ms.openlocfilehash: 1598130eb097655d3e83689956eb3614103eb573
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860375"
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
  
## <a name="parameters"></a>Paramètres  
 `moduleBaseAddress`  
 dans Adresse de base d’un module dans le processus cible. COR_E_NOT_CLR est retourné si le module spécifié n’est pas un module CLR.  
  
 `pDataTarget`  
 dans Abstraction de cible de données qui permet au débogueur managé d’inspecter l’état du processus. Le débogueur doit implémenter l’interface [ICorDebugDataTarget](icordebugdatatarget-interface.md) . Vous devez implémenter l’interface [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) pour prendre en charge les scénarios où le CLR qui est débogué n’est pas installé localement sur l’ordinateur.  
  
 `pLibraryProvider`  
 dans Interface de rappel de fournisseur de bibliothèque qui permet de localiser et de charger des bibliothèques de débogage spécifiques à la version à la demande. Ce paramètre est obligatoire uniquement si `ppProcess` ou `pFlags` n’est `null`pas.  
  
 `pMaxDebuggerSupportedVersion`  
 dans Version la plus récente du CLR que ce débogueur peut déboguer. Vous devez spécifier les versions majeure, mineure et de build de la dernière version du CLR que ce débogueur prend en charge, et définir le numéro de révision sur 65535 pour prendre en charge les futures versions de maintenance du CLR sur place.  
  
 `riidProcess`  
 dans ID de l’interface ICorDebugProcess à récupérer. Actuellement, les seules valeurs acceptées sont IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2 et IID_CORDEBUGPROCESS.  
  
 `ppProcess`  
 à Pointeur vers l’interface COM qui est identifiée par `riidProcess`.  
  
 `pVersion`  
 [in, out] Version du CLR. En entrée, cette valeur peut être `null`. Il peut également pointer vers une structure [CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) , auquel cas le champ de `wStructVersion` la structure doit être initialisé à 0 (zéro).  
  
 Lors de la sortie, `CLR_DEBUGGING_VERSION` la structure retournée est renseignée avec les informations de version pour le CLR.  
  
 `pdwFlags`  
 à Indicateurs d’information sur le runtime spécifié. Pour obtenir une description des indicateurs, consultez la rubrique [CLR_DEBUGGING_PROCESS_FLAGS](clr-debugging-process-flags-enumeration.md) .  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_POINTER|`pDataTarget` a la valeur `null`.|  
|CORDBG_E_LIBRARY_PROVIDER_ERROR|Le rappel [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) retourne une erreur ou ne fournit pas de handle valide.|  
|CORDBG_E_MISSING_DATA_TARGET_INTERFACE|`pDataTarget`n’implémente pas les interfaces cibles de données requises pour cette version du Runtime.|  
|CORDBG_E_NOT_CLR|Le module indiqué n’est pas un module CLR. Ce HRESULT est également retourné lorsqu’un module CLR ne peut pas être détecté parce que la mémoire a été endommagée, que le module n’est pas disponible ou que la version du CLR est ultérieure à la version du shim.|  
|CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL|Cette version du runtime ne prend pas en charge ce modèle de débogage. Actuellement, le modèle de débogage n’est pas pris en charge par les versions CLR antérieures au .NET Framework 4. Le `pwszVersion` paramètre de sortie est toujours défini sur la valeur correcte après cette erreur.|  
|CORDBG_E_UNSUPPORTED_FORWARD_COMPAT|La version du CLR est supérieure à la version que ce débogueur prétend prendre en charge. Le `pwszVersion` paramètre de sortie est toujours défini sur la valeur correcte après cette erreur.|  
|E_NO_INTERFACE|L' `riidProcess` interface n’est pas disponible.|  
|CORDBG_E_UNSUPPORTED_VERSION_STRUCT|La `CLR_DEBUGGING_VERSION` structure n’a pas de valeur reconnue pour `wStructVersion`. La seule valeur acceptée pour l’instant est 0.|  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
