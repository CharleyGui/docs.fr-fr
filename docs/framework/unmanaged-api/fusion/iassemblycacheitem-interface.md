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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 193604068e379d62107b25f2bc348cd7c8bc6e98
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796706"
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
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de fusion](fusion-interfaces.md)
- [Global Assembly Cache](../../app-domains/gac.md)
- [IAssemblyCache, interface](iassemblycache-interface.md)
