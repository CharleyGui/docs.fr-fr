---
title: IAssemblyCacheItem, interface
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: ccc9387a-9f44-4f4f-bf8f-0ea6d2afa21b
topic_type:
- apiref
ms.openlocfilehash: 72922d1fd0f8ae5e59fe76c7aa50f9c52dcd5302
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719942"
---
# <a name="iassemblycacheitem-interface"></a>IAssemblyCacheItem, interface

Représente un assembly unique dans le Global Assembly Cache.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[AbortItem, méthode](iassemblycacheitem-abortitem-method.md)|Permet à l’assembly dans le Global Assembly Cache d’effectuer des opérations de nettoyage avant qu’il ne soit libéré.|  
|[Commit, méthode](iassemblycacheitem-commit-method.md)|Valide la référence de l’assembly mis en cache dans la mémoire.|  
|[CreateStream, méthode](iassemblycacheitem-createstream-method.md)|Crée un flux de donnée avec le nom et le format spécifiés.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de fusion](fusion-interfaces.md)
- [Global Assembly Cache](../../app-domains/gac.md)
- [IAssemblyCache, interface](iassemblycache-interface.md)
