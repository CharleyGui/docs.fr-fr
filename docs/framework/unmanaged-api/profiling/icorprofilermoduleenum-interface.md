---
title: ICorProfilerModuleEnum, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum
helpviewer_keywords:
- ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: 24d0fcfa-1601-4fba-868f-da8c97303467
topic_type:
- apiref
ms.openlocfilehash: 5c4efff46c2460ee77f5a8011dc80796ac62a69e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442697"
---
# <a name="icorprofilermoduleenum-interface"></a>ICorProfilerModuleEnum, interface
Fournit des méthodes pour boucler séquentiellement dans une collection de modules chargés par l’application ou par le profileur.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Clone, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-clone-method.md)|Obtient un pointeur d'interface vers une copie de cette interface `ICorProfilerModuleEnum`.|  
|[GetCount, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-getcount-method.md)|Obtient le nombre de modules managés chargés dans l'application.|  
|[Next, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-next-method.md)|Obtient le nombre spécifié de modules contigus dans une collection séquentielle d’objets, à commencer par la position actuelle de l’énumérateur dans la séquence.|  
|[Reset, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-reset-method.md)|Déplace le curseur de l'énumérateur à la position de départ de la séquence.|  
|[Skip, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-skip-method.md)|Fait avancer la position du curseur de l'énumérateur de manière à ignorer le nombre spécifié d'éléments.|  
  
## <a name="remarks"></a>Notes  
 L'interface `ICorProfilerModuleEnum` est un énumérateur. Elle permet au récepteur d’un tableau de récupérer des éléments de l’expéditeur à une fréquence appropriée pour le récepteur. En d'autres termes, le récepteur peut contrôler explicitement le flux d'éléments de tableau et éviter ainsi les problèmes liés au passage de tableaux volumineux en tant que paramètres de méthode.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [EnumModules, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)
