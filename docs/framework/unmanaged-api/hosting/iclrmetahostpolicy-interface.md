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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 426d77114d3deeff94c39e2f5fc1f2e56e753641
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490277"
---
# <a name="iclrmetahostpolicy-interface"></a>ICLRMetaHostPolicy, interface
Fournit le [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) (méthode), qui retourne un pointeur vers une interface commune de runtime (CLR) langue selon un critère de stratégie, gérés de fichier de configuration, de la version et de l’assembly.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetRequestedRuntime, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|Fournit une interface CLR par défaut selon un critère de stratégie, gérés de fichier d’assembly, version et la configuration.|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez obtenir une référence à cette interface en appelant le [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) fonction comme indiqué dans le code suivant :  
  
```  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
>  Cette interface ne pas réellement charger ou activer le CLR, mais retourne simplement la version CLR par défaut selon les versions disponibles qui sont installées ou chargées.  
  
 L’API d’hébergement .NET Framework 4 consolide les stratégies de sorte que les hôtes avec des besoins spécifiques puissent utiliser les fonctionnalités de base sans encourir des pénalités imprévues. Par exemple, la plupart des exportations MSCorEE.dll seront lié à un CLR spécifique, bien qu’une méthode peut logiquement impose pas. Le [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) énumération fournit des stratégies de liaison qui sont communes à la majorité des ordinateurs hôtes.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MetaHost.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces d’hébergement CLR ajoutées dans .NET Framework 4 et 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md)
