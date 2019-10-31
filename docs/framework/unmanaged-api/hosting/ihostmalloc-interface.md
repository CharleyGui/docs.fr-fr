---
title: IHostMalloc, interface
ms.date: 03/30/2017
api_name:
- IHostMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc
helpviewer_keywords:
- IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type:
- apiref
ms.openlocfilehash: abc6cca185b318be016f92ac8c97d21f7af5940a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136778"
---
# <a name="ihostmalloc-interface"></a>IHostMalloc, interface
Fournit des méthodes qui permettent au common language runtime (CLR) de demander des allocations affinées à partir du tas par le biais de l’hôte.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Alloc, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|Demande que l’hôte alloue la quantité de mémoire demandée à partir du tas.|  
|[DebugAlloc, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|Demande que l’hôte alloue la quantité de mémoire demandée à partir du tas et effectue également le suivi de l’emplacement où la mémoire a été allouée.|  
|[Free, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|Libère de la mémoire qui a été allouée à l’aide de la méthode `Alloc`.|  
  
## <a name="remarks"></a>Notes  
 Le CLR obtient un pointeur d’interface vers une instance de `IHostMalloc` en appelant la méthode [IHostMemoryManager :: CreateMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) .  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IHostMemoryManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
