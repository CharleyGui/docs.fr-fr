---
title: ICLRRuntimeInfo::LoadErrorString, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadErrorString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadErrorString
helpviewer_keywords:
- ICLRRuntimeInfo::LoadErrorString method [.NET Framework hosting]
- LoadErrorString method [.NET Framework hosting]
ms.assetid: 52c543ab-9ef5-4ee7-b836-c0ffc35cd45b
topic_type:
- apiref
ms.openlocfilehash: da6efae38cd70a68feea56b12e86be23fde7f0cb
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762186"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a>ICLRRuntimeInfo::LoadErrorString, méthode
Convertit une valeur HRESULT en un message d’erreur approprié pour la culture spécifiée.  
  
 Cette méthode remplace les fonctions suivantes :  
  
- [LoadStringRC,](loadstringrc-function.md)  
  
- [LoadStringRCEx,](loadstringrcex-function.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a>Paramètres  
 `iResourceID`  
 dans HRESULT à traduire.  
  
 `pwzBuffer`  
 à Chaîne de message associée au HRESULT donné.  
  
 `pcchBuffer`  
 [in, out] Taille de `pwzbuffer` pour éviter les dépassements de mémoire tampon. Si `pwzbuffer` a la valeur null, `pcchBuffer` fournit la taille attendue de `pwzbuffer` pour autoriser la préallocation.  
  
 `iLocaleID`  
 dans Identificateur de culture. Pour utiliser la culture par défaut, vous devez spécifier-1.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_POINTER|`pcchBuffer` a la valeur null.|  
|E_INVALIDARG|`pwzBuffer` a la valeur null.|  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRRuntimeInfo, interface](iclrruntimeinfo-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
- [Hébergement](index.md)
