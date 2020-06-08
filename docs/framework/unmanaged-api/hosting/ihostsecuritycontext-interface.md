---
title: IHostSecurityContext, interface
ms.date: 03/30/2017
api_name:
- IHostSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext
helpviewer_keywords:
- IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type:
- apiref
ms.openlocfilehash: f6e25bfe11880730f6f447ccc0406d716d185624
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501493"
---
# <a name="ihostsecuritycontext-interface"></a>IHostSecurityContext, interface
Permet à l’common language runtime (CLR) de conserver les informations de contexte de sécurité implémentées par l’hôte.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Capture, méthode](ihostsecuritycontext-capture-method.md)|Obtient un clone de l' `IHostSecurityContext` instance retournée à partir d’un appel à [IHostSecurityManager :: GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md).|  
  
## <a name="remarks"></a>Remarques  
 Un hôte peut contrôler tout l’accès du code aux jetons de thread à la fois par le CLR et le code utilisateur. Il peut également s’assurer que les informations de contexte de sécurité complètes sont transmises sur des opérations asynchrones ou des points de code avec accès restreint au code. `IHostSecurityContext`encapsule ces informations de contexte de sécurité, qui sont opaques pour le Runtime. Le Runtime Capture ces informations à l’aide de `Capture` et les déplace à travers la répartition des éléments de travail du pool de threads, l’exécution du finaliseur et les constructeurs de module et de classe.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRHostProtectionManager, interface](iclrhostprotectionmanager-interface.md)
- [IHostSecurityManager, interface](ihostsecuritymanager-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
