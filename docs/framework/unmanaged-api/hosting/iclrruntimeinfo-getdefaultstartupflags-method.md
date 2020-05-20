---
title: ICLRRuntimeInfo::GetDefaultStartupFlags, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags method [.NET Framework hosting]
- GetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 35c2173e-3b0b-4b2a-950d-e0a01c6df052
topic_type:
- apiref
ms.openlocfilehash: 8513787f48ae89632816face386bbcda20555dac
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703888"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a>ICLRRuntimeInfo::GetDefaultStartupFlags, méthode
Obtient les indicateurs de démarrage et le fichier de configuration d’hôte qui sera utilisé pour démarrer le Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pdwStartupFlags`  
 à Pointeur vers les indicateurs de démarrage de l’hôte qui sont actuellement définis.  
  
 `pwzHostConfigFile`  
 à Pointeur vers le chemin d’accès du répertoire du fichier de configuration hôte actuel.  
  
 `pcchHostConfigFile`  
 [in, out] En entrée, taille de `pwzHostConfigFile` , pour éviter les dépassements de mémoire tampon. Si `pwzHostConfigFile` a la valeur null, la méthode retourne la taille requise de `pwzHostConfigFile` pour la pré-allocation.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT qui indiquent un échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne les valeurs d’indicateur par défaut ( `STARTUP_CONCURRENT_GC` et `NULL` ), ou les valeurs fournies par un appel précédent à la [méthode ICLRRuntimeInfo :: SetDefaultStartupFlags,](iclrruntimeinfo-setdefaultstartupflags-method.md), ou les valeurs définies par l’une des `CorBind*` méthodes si elles sont liées à ce Runtime.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRRuntimeInfo, interface](iclrruntimeinfo-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
- [Hébergement](index.md)
