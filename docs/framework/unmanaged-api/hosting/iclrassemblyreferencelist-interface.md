---
title: ICLRAssemblyReferenceList, interface
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList
helpviewer_keywords:
- ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type:
- apiref
ms.openlocfilehash: a75235cd0ac0e55412f0ba58881796e3ebc801f1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679193"
---
# <a name="iclrassemblyreferencelist-interface"></a>ICLRAssemblyReferenceList, interface

Gère une liste d’assemblys qui sont chargés par le common language runtime (CLR) et non par l’hôte.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[IsAssemblyReferenceInList, méthode](iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|Obtient une valeur qui indique si le pointeur fourni référence un assembly de la liste.|  
|[IsStringAssemblyReferenceInList, méthode](iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|Obtient une valeur qui indique si le nom fourni correspond au nom d’un assembly dans la liste.|  
  
## <a name="remarks"></a>Remarques  

 Appelez la méthode [ICLRAssemblyIdentityManager :: GetCLRAssemblyReferenceList,](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) pour obtenir un pointeur vers une instance de `ICLRAssemblyReferenceList` .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRAssemblyIdentityManager, interface](iclrassemblyidentitymanager-interface.md)
- [IHostAssemblyStore, interface](ihostassemblystore-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
