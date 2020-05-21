---
title: ICLRRuntimeInfo::LoadLibrary, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadLibrary
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadLibrary
helpviewer_keywords:
- ICLRRuntimeInfo::LoadLibrary method [.NET Framework hosting]
- LoadLibrary method [.NET Framework hosting]
ms.assetid: 4517ada3-4417-4ac5-a150-73da7a87c686
topic_type:
- apiref
ms.openlocfilehash: 09c80c3a56d86943ebe00e5222bb5452ab44e150
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762173"
---
# <a name="iclrruntimeinfoloadlibrary-method"></a>ICLRRuntimeInfo::LoadLibrary, méthode
Charge une bibliothèque .NET Framework à partir du common language runtime (CLR) représenté par une interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .  
  
 Cette méthode remplace la fonction [LoadLibraryShim](loadlibraryshim-function.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pwzDllName`  
 dans Nom de l’assembly à charger.  
  
 `phndModule`  
 à Handle de l’assembly chargé.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_POINTER|`pwzDllName` ou `phndModule` est null.|  
|E_OUTOFMEMORY|Mémoire disponible insuffisante pour traiter la demande.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode charge uniquement les dll incluses dans le package redistribuable .NET Framework. Il ne peut pas charger les assemblys générés par l’utilisateur.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRRuntimeInfo, interface](iclrruntimeinfo-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
- [Hébergement](index.md)
