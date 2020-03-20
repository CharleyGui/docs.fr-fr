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
ms.openlocfilehash: adc8ea16f0ab2bf383f8a63c49ba7d61c6bac113
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176446"
---
# <a name="createdebugginginterfacefromversion-function"></a>CreateDebuggingInterfaceFromVersion, fonction
Crée un objet [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) basé sur les informations de version spécifiées.  
  
 Cette fonction est obsolète dans le cadre .NET 4. Au lieu de cela, pour obtenir une interface pour l’heure de fonctionnement de la langue commune (CLR) 2.0, utilisez la méthode [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) et spécifier l’identifiant de classe CLSID_CLRDebuggingLegacy et l’identifiant d’interface IID_ICorDebug. Pour obtenir une interface pour CLR 4 ou plus tard, appelez la fonction [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) et spécifiez l’identifiant de classe CLSID_CLRDebugging et l’identifiant d’interface IID_ICLRDebugging.  
  
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
 [dans] La version `ICorDebug` de cela est attendue par le débbugger. Voir le recensement [de CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) pour les valeurs valides.  
  
 `szDebuggeeVersion`  
 [dans] La version courante de l’heure d’exécution de langue associée à l’application ou au processus à déboguer. Consultez la méthode [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) ou [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) pour plus d’informations sur la récupération de cette valeur.  
  
 `ppCordb`  
 [out] L’emplacement qui reçoit `ICorDebug` un pointeur de l’objet.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode renvoie les codes d’erreur COM standard tels que définis dans le fichier WinError.h en plus des valeurs suivantes.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_INVALIDARG|`szDebuggeeVersion`ou `ppCordb` est nul, ou la chaîne de version est incorrecte.|  
  
## <a name="remarks"></a>Notes   
 Les `szDebuggeeVersion` cartes de paramètres à la version correspondante de MSCorDbi.dll.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor  
  
 **Bibliothèque:** MSCorEE.dll MSCorEE.dll MSCorEE.dll MSCor  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonction d'hébergement du CLR déconseillées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
