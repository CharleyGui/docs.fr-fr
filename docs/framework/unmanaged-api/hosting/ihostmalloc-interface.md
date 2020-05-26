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
ms.openlocfilehash: 8f4e1cd7586df7d8e2a577d26f06eaed6b2c8bb7
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804603"
---
# <a name="ihostmalloc-interface"></a>IHostMalloc, interface
Fournit des méthodes qui permettent au common language runtime (CLR) de demander des allocations affinées à partir du tas par le biais de l’hôte.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Alloc, méthode](ihostmalloc-alloc-method.md)|Demande que l’hôte alloue la quantité de mémoire demandée à partir du tas.|  
|[DebugAlloc, méthode](ihostmalloc-debugalloc-method.md)|Demande que l’hôte alloue la quantité de mémoire demandée à partir du tas et effectue également le suivi de l’emplacement où la mémoire a été allouée.|  
|[Free, méthode](ihostmalloc-free-method.md)|Libère de la mémoire qui a été allouée à l’aide de la `Alloc` méthode.|  
  
## <a name="remarks"></a>Notes  
 Le CLR obtient un pointeur d’interface vers une `IHostMalloc` instance en appelant la méthode [IHostMemoryManager :: CreateMAlloc](ihostmemorymanager-createmalloc-method.md) .  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IHostMemoryManager, interface](ihostmemorymanager-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
