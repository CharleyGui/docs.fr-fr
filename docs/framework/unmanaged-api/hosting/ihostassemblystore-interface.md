---
title: IHostAssemblyStore, interface
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore
helpviewer_keywords:
- IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type:
- apiref
ms.openlocfilehash: 4b2fed963d2d0ebec54e5f7a4d95cba26c1bac1f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680936"
---
# <a name="ihostassemblystore-interface"></a>IHostAssemblyStore, interface

Fournit des méthodes qui permettent à un hôte de charger des assemblys et des modules indépendamment du common language runtime (CLR).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ProvideAssembly, méthode](ihostassemblystore-provideassembly-method.md)|Obtient une référence à un assembly qui n’est pas référencé par l' [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) retourné par un appel à [IHostAssemblyManager :: GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md).|  
|[ProvideModule, méthode](ihostassemblystore-providemodule-method.md)|Résout un module au sein d’un assembly ou d’un fichier de ressources lié (non incorporé).|  
  
## <a name="remarks"></a>Remarques  

 `IHostAssemblyStore` permet à un hôte de charger efficacement des assemblys en fonction de l’identité de l’assembly. L’hôte charge des assemblys en retournant des `IStream` instances qui pointent directement vers les octets.  
  
 Le CLR détermine si un hôte a implémenté `IHostAssemblyStore` en appelant `IHostAssemblyManager::GetNonHostAssemblyStores` lors de l’initialisation. Cela permet à l’hôte, par exemple, de contrôler la liaison aux assemblys utilisateur, mais de s’appuyer sur le runtime pour effectuer une liaison à .NET Framework assemblys.  
  
> [!NOTE]
> En fournissant une implémentation de `IHostAssemblyStore` , l’hôte spécifie son intention de résoudre tous les assemblys qui ne sont pas référencés par le `ICLRAssemblyReferenceList` retourné à partir de `IHostAssemblyManager::GetNonHostStoreAssemblies` .  
  
> [!NOTE]
> La version 2,0 de .NET Framework ne permet pas à l’hôte de charger l’image native d’un assembly, comme fourni par l’utilitaire [Ngen.exe (Native Image Generator)](../../tools/ngen-exe-native-image-generator.md) .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRAssemblyReferenceList, interface](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager, interface](ihostassemblymanager-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
