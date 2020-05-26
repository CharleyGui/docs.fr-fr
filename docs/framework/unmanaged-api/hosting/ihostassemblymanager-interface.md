---
title: IHostAssemblyManager, interface
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager
helpviewer_keywords:
- IHostAssemblyManager interface [.NET Framework hosting]
ms.assetid: dfec05bb-3cd7-4bd5-b396-a4f097c3a636
topic_type:
- apiref
ms.openlocfilehash: 8106dd70f6c4099b2246530622f0845f22a0c53f
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805050"
---
# <a name="ihostassemblymanager-interface"></a>IHostAssemblyManager, interface
Fournit des méthodes qui permettent à un hôte de spécifier des jeux d’assemblys qui doivent être chargés par le common language runtime (CLR) ou par l’hôte.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetAssemblyStore, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|Obtient un pointeur d’interface vers un [IHostAssemblyStore](ihostassemblystore-interface.md) qui représente la liste des assemblys chargés par l’hôte.|  
|[GetNonHostStoreAssemblies, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|Obtient un pointeur d’interface vers un [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) qui représente la liste des assemblys que l’hôte attend que le CLR se charge.|  
  
## <a name="remarks"></a>Notes  
 L’hôte n’est pas tenu d’implémenter `IHostAssemblyManager` ou `IHostAssemblyStore` . Si l’hôte implémente `IHostAssemblyManager` , il doit également implémenter `IHostAssemblyStore` .  
  
 Le runtime interroge pour un `IHostAssemblyManager` en appelant [IHostControl :: GetHostManager,](ihostcontrol-gethostmanager-method.md) lors de l’initialisation avec un `IID` de IID_IHostAssemblyManager.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRAssemblyReferenceList, interface](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyStore, interface](ihostassemblystore-interface.md)
- [IHostControl, interface](ihostcontrol-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
