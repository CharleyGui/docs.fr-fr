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
ms.openlocfilehash: 79b62a5e2aad9cfcd14ba40c1abf0342bfe57a4b
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703530"
---
# <a name="iclrmetahostpolicy-interface"></a>ICLRMetaHostPolicy, interface
Fournit la méthode [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) , qui retourne un pointeur vers une interface Common Language Runtime (CLR) en fonction d’un critère de stratégie, d’un assembly managé, d’une version et d’un fichier de configuration.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetRequestedRuntime, méthode](iclrmetahostpolicy-getrequestedruntime-method.md)|Fournit une interface CLR par défaut basée sur un critère de stratégie, un assembly managé, une version et un fichier de configuration.|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez obtenir une référence à cette interface en appelant la fonction [CLRCreateInstance](clrcreateinstance-function.md) comme indiqué dans le code suivant :  
  
```cpp  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
> Cette interface ne charge pas ou n’active pas réellement le CLR, mais retourne simplement la version CLR par défaut en fonction des versions disponibles qui sont installées ou chargées.  
  
 L’API d’hébergement .NET Framework 4 consolide les stratégies afin que les hôtes ayant des besoins spécifiques puissent utiliser les fonctionnalités de base sans engager de pénalités involontaires. Par exemple, la plupart des exportations de MSCorEE. dll sont liées à un CLR spécifique, bien qu’une méthode puisse ne pas l’exiger logiquement. L’énumération [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) fournit des stratégies de liaison communes à la majorité des hôtes.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces d'hébergement du CLR ajoutées dans .NET Framework 4 et 4.5](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
- [Hébergement](index.md)
