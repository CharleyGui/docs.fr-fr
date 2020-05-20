---
title: CreateDebuggingInterfaceFromVersion, fonction
ms.date: 03/30/2017
api_name:
- CreateDebuggingInterfaceFromVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function [.NET Framework hosting]
ms.assetid: a746a849-463c-44f5-a2f0-9e812ed8bcc3
topic_type:
- apiref
ms.openlocfilehash: 0e1395229b67c4054df62935375a4136edf63078
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616487"
---
# <a name="createdebugginginterfacefromversion-function"></a>CreateDebuggingInterfaceFromVersion, fonction
Crée un objet [ICorDebug](../debugging/icordebug-interface.md) basé sur les informations de version spécifiées.  
  
 Cette fonction est obsolète dans le .NET Framework 4. Au lieu de cela, pour obtenir une interface pour le common language runtime (CLR) 2,0, utilisez la méthode [ICLRRuntimeInfo :: GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) et spécifiez l’identificateur de classe CLSID_CLRDebuggingLegacy et l’identificateur d’interface IID_ICorDebug. Pour obtenir une interface pour CLR 4 ou version ultérieure, appelez la fonction [CLRCreateInstance](clrcreateinstance-function.md) et spécifiez l’identificateur de classe CLSID_CLRDebugging et l’identificateur d’interface IID_ICLRDebugging.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,
    [in]  LPCWSTR  szDebuggeeVersion,
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `iDebuggerVersion`  
 dans Version de `ICorDebug` qui est attendue par le débogueur. Consultez l’énumération [CorDebugInterfaceVersion,](../debugging/cordebuginterfaceversion-enumeration.md) pour connaître les valeurs valides.  
  
 `szDebuggeeVersion`  
 dans Version de common language runtime associée à l’application ou au processus à déboguer. Pour plus d’informations sur la récupération de cette valeur, consultez la méthode [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) ou [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) .  
  
 `ppCordb`  
 à Emplacement qui reçoit un pointeur vers l' `ICorDebug` objet.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les codes d’erreur COM standard tels qu’ils sont définis dans le fichier WinError. h, en plus des valeurs suivantes.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_INVALIDARG|`szDebuggeeVersion`ou `ppCordb` est null, ou la chaîne de version est incorrecte.|  
  
## <a name="remarks"></a>Notes  
 Le `szDebuggeeVersion` paramètre est mappé à la version correspondante de mscordbi. dll.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)
