---
title: ICLRMetaHost::EnumerateLoadedRuntimes, méthode
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateLoadedRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type:
- apiref
ms.openlocfilehash: 7b09bb9c3abcb23997bfd412c3ea939404e583c1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504171"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a>ICLRMetaHost::EnumerateLoadedRuntimes, méthode
Retourne une énumération qui comprend un pointeur d’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) valide pour chaque version du Common Language Runtime (CLR) qui est chargé dans un processus donné. Cette méthode remplace la fonction [GetVersionFromProcess](getversionfromprocess-function.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `hndProcess`  
 dans Handle du processus à examiner pour les runtimes chargés.  
  
 `ppEnumerator`  
 à <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown>Énumération d’interfaces [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) correspondant à chaque CLR chargé par le processus.  
  
## <a name="return-value"></a>Valeur renvoyée  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_POINTER|`ppEnumerator` a la valeur null.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode répertorie tous les runtimes chargés, même s’ils ont été chargés avec des fonctions déconseillées telles que [CorBindToRuntime](corbindtoruntime-function.md).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRMetaHost, interface](iclrmetahost-interface.md)
- [Hosting](index.md)
