---
title: ICLRProbingAssemblyEnum, interface
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum
helpviewer_keywords:
- ICLRProbingAssemblyEnum interface [.NET Framework hosting]
ms.assetid: e7d3ccab-b0f0-4872-8935-0ed72920171b
topic_type:
- apiref
ms.openlocfilehash: 6df08889af30542af5a128cbffc38a57ce640fde
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728925"
---
# <a name="iclrprobingassemblyenum-interface"></a>ICLRProbingAssemblyEnum, interface

Fournit des méthodes qui permettent à l’hôte d’accéder aux identités de détection d’un assembly à l’aide des informations d’identité de l’assembly qui sont internes au common language runtime (CLR), sans avoir à créer ou à comprendre cette identité.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Méthode Get](iclrprobingassemblyenum-get-method.md)|Obtient l’identité de l’assembly au niveau de l’index spécifié.|  
  
## <a name="remarks"></a>Remarques  

 Les méthodes telles que [ICLRAssemblyIdentityManager :: GetProbingAssembliesFromReference,](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) retournent une `ICLRProbingAssemblyEnum` instance.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRAssemblyIdentityManager, interface](iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList, interface](iclrassemblyreferencelist-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
