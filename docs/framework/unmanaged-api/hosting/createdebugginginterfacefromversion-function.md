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
ms.openlocfilehash: b68fbc713374642c9f55d49ee51a88c5785cf4b2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727872"
---
# <a name="createdebugginginterfacefromversion-function"></a>CreateDebuggingInterfaceFromVersion, fonction

Crée un objet [ICorDebug](../debugging/icordebug-interface.md) basé sur les informations de version spécifiées.  
  
 Cette fonction est obsolète dans le .NET Framework 4. Au lieu de cela, pour obtenir une interface pour le common language runtime (CLR) 2,0, utilisez la méthode [ICLRRuntimeInfo :: GetInterface](iclrruntimeinfo-getinterface-method.md) et spécifiez l’identificateur de classe CLSID_CLRDebuggingLegacy et l’identificateur d’interface IID_ICorDebug. Pour obtenir une interface pour CLR 4 ou version ultérieure, appelez la fonction [CLRCreateInstance](clrcreateinstance-function.md) et spécifiez l’identificateur de classe CLSID_CLRDebugging et l’identificateur d’interface IID_ICLRDebugging.  
  
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
 dans Version de common language runtime associée à l’application ou au processus à déboguer. Pour plus d’informations sur la récupération de cette valeur, consultez la méthode [GetVersionFromProcess](getversionfromprocess-function.md) ou [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) .  
  
 `ppCordb`  
 à Emplacement qui reçoit un pointeur vers l' `ICorDebug` objet.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Cette méthode retourne les codes d’erreur COM standard tels qu’ils sont définis dans le fichier WinError. h, en plus des valeurs suivantes.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_INVALIDARG|`szDebuggeeVersion` ou `ppCordb` est null, ou la chaîne de version est incorrecte.|  
  
## <a name="remarks"></a>Remarques  

 Le `szDebuggeeVersion` paramètre est mappé à la version correspondante de MSCorDbi.dll.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)
