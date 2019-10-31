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
ms.openlocfilehash: 5ed0075da1429c70900750f3f28e8ce36a41fb28
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134541"
---
# <a name="iassemblycache-interface"></a>IAssemblyCache, interface
Represents the global assembly cache for use by the fusion technology.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CreateAssemblyCacheItem, méthode](iassemblycache-createassemblycacheitem-method.md)|Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md).|  
|[CreateAssemblyScavenger, méthode](iassemblycache-createassemblyscavenger-method.md)|Reserved for internal use by the fusion technology.|  
|[InstallAssembly, méthode](iassemblycache-installassembly-method.md)|Installs the specified assembly in the global assembly cache.|  
|[QueryAssemblyInfo, méthode](iassemblycache-queryassemblyinfo-method.md)|Gets the requested data about the specified assembly.|  
|[UninstallAssembly, méthode](iassemblycache-uninstallassembly-method.md)|Uninstalls the specified assembly from the global assembly cache.|  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **Header:** Fusion.h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de fusion](fusion-interfaces.md)
- [Global Assembly Cache](../../app-domains/gac.md)
