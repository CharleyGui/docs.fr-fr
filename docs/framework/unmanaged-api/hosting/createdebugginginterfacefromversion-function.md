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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 247383e267ab3e8932d43621e122986a59d9a30d
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490512"
---
# <a name="createdebugginginterfacefromversion-function"></a>CreateDebuggingInterfaceFromVersion, fonction
Crée un [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) objet basé sur les informations de version spécifié.  
  
 Cette fonction est obsolète dans le .NET Framework 4. Pour obtenir une interface pour le common language runtime (CLR) 2.0, utilisez plutôt le [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) (méthode) et spécifiez l’identificateur de classe CLSID_CLRDebuggingLegacy et l’identificateur d’interface IID_ICorDebug. Pour obtenir une interface pour le CLR 4 ou version ultérieure, appelez le [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) de fonction et spécifier l’identificateur de classe CLSID_CLRDebugging et l’identificateur d’interface IID_ICLRDebugging.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,   
    [in]  LPCWSTR  szDebuggeeVersion,   
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `iDebuggerVersion`  
 [in] La version de `ICorDebug` qui est attendue par le débogueur. Consultez le [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) énumération pour les valeurs valides.  
  
 `szDebuggeeVersion`  
 [in] Version du common language runtime associée à l’application ou le processus à déboguer. Consultez le [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) ou [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) méthode pour plus d’informations sur la récupération de cette valeur.  
  
 `ppCordb`  
 [out] L’emplacement qui reçoit un pointeur vers le `ICorDebug` objet.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne des codes d’erreur COM standard, tel que défini dans le fichier WinError.h, en plus des valeurs suivantes.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_INVALIDARG|`szDebuggeeVersion` ou `ppCordb` est null, ou la version de chaîne est incorrecte.|  
  
## <a name="remarks"></a>Notes  
 Le `szDebuggeeVersion` paramètre correspond à la version correspondante de MSCorDbi.dll.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions d’hébergement CLR dépréciées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
