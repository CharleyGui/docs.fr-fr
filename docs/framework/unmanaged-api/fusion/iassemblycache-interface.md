---
title: IAssemblyCache, interface
ms.date: 03/30/2017
api_name:
- IAssemblyCache
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache
helpviewer_keywords:
- IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6dab5fe941fce3c23ba718906b29c80c6d257c2f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796769"
---
# <a name="iassemblycache-interface"></a>IAssemblyCache, interface
Représente le Global Assembly Cache pour une utilisation par la technologie de fusion.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CreateAssemblyCacheItem, méthode](iassemblycache-createassemblycacheitem-method.md)|Obtient une référence à un nouvel [IAssemblyCacheItem](iassemblycacheitem-interface.md).|  
|[CreateAssemblyScavenger, méthode](iassemblycache-createassemblyscavenger-method.md)|Réservé à un usage interne par la technologie de fusion.|  
|[InstallAssembly, méthode](iassemblycache-installassembly-method.md)|Installe l’assembly spécifié dans la Global Assembly Cache.|  
|[QueryAssemblyInfo, méthode](iassemblycache-queryassemblyinfo-method.md)|Obtient les données demandées relatives à l’assembly spécifié.|  
|[UninstallAssembly, méthode](iassemblycache-uninstallassembly-method.md)|Désinstalle l’assembly spécifié du Global Assembly Cache.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de fusion](fusion-interfaces.md)
- [Global Assembly Cache](../../app-domains/gac.md)
