---
title: ICLRMetaHostPolicy, interface
ms.date: 03/30/2017
api_name:
- ICLRMetaHostPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy
helpviewer_keywords:
- ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type:
- apiref
ms.openlocfilehash: 277c13895374116eb67f6515f45df638f61b0453
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140857"
---
# <a name="iclrmetahostpolicy-interface"></a>ICLRMetaHostPolicy, interface
Fournit la méthode [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) , qui retourne un pointeur vers une interface Common Language Runtime (CLR) en fonction d’un critère de stratégie, d’un assembly managé, d’une version et d’un fichier de configuration.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetRequestedRuntime, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|Fournit une interface CLR par défaut basée sur un critère de stratégie, un assembly managé, une version et un fichier de configuration.|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez obtenir une référence à cette interface en appelant la fonction [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) comme indiqué dans le code suivant :  
  
```cpp  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
> Cette interface ne charge pas ou n’active pas réellement le CLR, mais retourne simplement la version CLR par défaut en fonction des versions disponibles qui sont installées ou chargées.  
  
 L’API d’hébergement .NET Framework 4 consolide les stratégies afin que les hôtes ayant des besoins spécifiques puissent utiliser les fonctionnalités de base sans engager de pénalités involontaires. Par exemple, la plupart des exportations de MSCorEE. dll sont liées à un CLR spécifique, bien qu’une méthode puisse ne pas l’exiger logiquement. L’énumération [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) fournit des stratégies de liaison communes à la majorité des hôtes.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces d’hébergement CLR ajoutées dans .NET Framework 4 et 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md)
