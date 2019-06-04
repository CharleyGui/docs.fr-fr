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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d530f37c979a1ecddf2cb3895234aab2f7556b88
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489633"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a>ICLRDebugging::OpenVirtualProcess, méthode
Obtient l’interface ICorDebugProcess qui correspond à un module common language runtime (CLR) chargé dans le processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] L’adresse de base d’un module dans le processus cible. COR_E_NOT_CLR sera retourné si le module spécifié n’est pas un module CLR.  
  
 `pDataTarget`  
 [in] Abstraction de cible de données qui permet au débogueur managé d’inspecter l’état du processus. Le débogueur doit implémenter le [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface. Vous devez implémenter le [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface pour prendre en charge les scénarios où le CLR qui est en cours de débogage n’est pas installé localement sur l’ordinateur.  
  
 `pLibraryProvider`  
 [in] Une interface de rappel de fournisseur bibliothèque qui permet des bibliothèques de débogage spécifiques à la version être à la demande et le chargement. Ce paramètre est obligatoire uniquement si `ppProcess` ou `pFlags` n’est pas `null`.  
  
 `pMaxDebuggerSupportedVersion`  
 [in] La version la plus récente du CLR que ce débogueur peut déboguer. Vous devez spécifier major, minor, build à partir de la dernière version CLR que ce débogueur prend en charge les versions et définir le numéro de révision et 65 535 pour prendre en charge les futures versions de maintenance du CLR sur place.  
  
 `riidProcess`  
 [in] ID de l’interface ICorDebugProcess à récupérer. Actuellement, les seules valeurs acceptées sont IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2 et IID_CORDEBUGPROCESS.  
  
 `ppProcess`  
 [out] Un pointeur vers l’interface COM qui est identifié par `riidProcess`.  
  
 `pVersion`  
 [in, out] La version du CLR. En entrée, cette valeur peut être `null`. Il peut aussi pointer vers un [CLR_DEBUGGING_VERSION](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) structure, auquel cas la structure `wStructVersion` champ doit être initialisé à 0 (zéro).  
  
 Lors de la sortie, retournée `CLR_DEBUGGING_VERSION` structure est remplie avec les informations de version pour le CLR.  
  
 `pdwFlags`  
 [out] Indicateurs d’information sur le runtime spécifié. Consultez le [CLR_DEBUGGING_PROCESS_FLAGS](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) rubrique pour obtenir une description des indicateurs.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_POINTER|`pDataTarget` a la valeur `null`.|  
|CORDBG_E_LIBRARY_PROVIDER_ERROR|Le [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) rappel retourne une erreur ou ne fournit pas un handle valide.|  
|CORDBG_E_MISSING_DATA_TARGET_INTERFACE|`pDataTarget` n’implémente pas les interfaces de cible de données requises pour cette version du runtime.|  
|CORDBG_E_NOT_CLR|Le module indiqué n’est pas un module CLR. Ce HRESULT est également retourné lorsqu’un module CLR ne peut pas être détecté, car la mémoire est endommagée, le module n’est pas disponible, ou la version du CLR est postérieure à la version de shim.|  
|CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL|Cette version du runtime ne prend pas en charge ce modèle de débogage. Actuellement, le modèle de débogage n’est pas prise en charge par les versions antérieures au .NET Framework 4 du CLR. Le `pwszVersion` paramètre de sortie est toujours défini à la valeur correcte après cette erreur.|  
|CORDBG_E_UNSUPPORTED_FORWARD_COMPAT|La version du CLR est supérieure à la version par ce débogueur pour prendre en charge. Le `pwszVersion` paramètre de sortie est toujours défini à la valeur correcte après cette erreur.|  
|E_NO_INTERFACE|Le `riidProcess` interface n’est pas disponible.|  
|CORDBG_E_UNSUPPORTED_VERSION_STRUCT|Le `CLR_DEBUGGING_VERSION` structure n’a pas de valeur reconnue pour `wStructVersion`. La seule valeur acceptée pour l’instant est 0.|  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
