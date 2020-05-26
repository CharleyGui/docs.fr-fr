---
title: IHostMemoryManager::NeedsVirtualAddressSpace, méthode
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.NeedsVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace method [.NET Framework hosting]
- NeedsVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: 71f0eab5-0170-46f8-9f88-1df5abdeb34a
topic_type:
- apiref
ms.openlocfilehash: bb13c7329c558aa92ec65237aa8a9963c82fe1dc
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804510"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a>IHostMemoryManager::NeedsVirtualAddressSpace, méthode
Avertit l’hôte que le common language runtime (CLR) va tenter d’utiliser la mémoire spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `startAddress`  
 dans Adresse de début de la mémoire.  
  
 `size`  
 dans Taille, en octets, de la mémoire.  
  
## <a name="remarks"></a>Notes  
 La `NeedsVirtualAddressSpace` méthode est une méthode de rappel qui doit être implémentée par le writer de l’application d’hébergement. Elle est appelée par le CLR.  
  
 Si l’hôte ne souhaite pas que le CLR utilise la mémoire spécifiée, il peut retourner un E_OUTOFMEMORY HRESULT.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IHostMemoryManager, interface](ihostmemorymanager-interface.md)
