---
title: ICorProfilerFunctionEnum, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum
helpviewer_keywords:
- ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0a1d4a38-cd0b-4231-91df-13646218ae72
topic_type:
- apiref
ms.openlocfilehash: 17f7243096b7ac18e456f8f31196055492015346
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447795"
---
# <a name="icorprofilerfunctionenum-interface"></a>ICorProfilerFunctionEnum, interface
Fournit des méthodes pour itérer séquentiellement une collection de fonctions dans le Common Language Runtime.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Clone, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-clone-method.md)|Obtient un pointeur d'interface vers une copie de cette interface `ICorProfilerFunctionEnum`.|  
|[GetCount, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-getcount-method.md)|Obtient le nombre de fonctions qui ont été chargées par l'application ou chargées de force par le profileur.|  
|[Next, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-next-method.md)|Obtient le nombre spécifié de fonctions contiguës dans une collection séquentielle de fonctions, à commencer par la position actuelle de l'énumérateur dans la séquence.|  
|[Reset, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-reset-method.md)|Déplace le curseur de l'énumérateur à la position de départ de la séquence.|  
|[Skip, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-skip-method.md)|Fait avancer le curseur de l'énumérateur depuis sa position actuelle de manière à ignorer le nombre spécifié d'éléments.|  
  
## <a name="remarks"></a>Notes  
 L'interface `ICorProfilerFunctionEnum` est un énumérateur. Elle permet au récepteur d’un tableau de récupérer des éléments de l’expéditeur à une fréquence appropriée pour le récepteur. En d'autres termes, le récepteur peut contrôler explicitement le flux d'éléments de tableau et éviter ainsi les problèmes liés au passage de tableaux volumineux en tant que paramètres de méthode.  
  
 `ICorProfilerFunctionEnum` énumère les fonctions qui ont déjà été compilées juste-à-temps, mais n’inclut pas les fonctions qui sont chargées à partir d’images natives générées avec Ngen. exe.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [EnumJITedFunctions, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
