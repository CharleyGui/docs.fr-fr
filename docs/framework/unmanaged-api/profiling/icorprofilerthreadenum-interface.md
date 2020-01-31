---
title: ICorProfilerThreadEnum, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum
helpviewer_keywords:
- ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: 1e35031b-e095-4c14-9644-8deeb3081e0b
topic_type:
- apiref
ms.openlocfilehash: b9fb308f19ff09218c97b030296b9a3d4f0f2512
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868185"
---
# <a name="icorprofilerthreadenum-interface"></a>ICorProfilerThreadEnum, interface
Fournit des méthodes pour itérer séquentiellement une collection de threads dans le Common Language Runtime.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Clone, méthode](icorprofilerthreadenum-clone-method.md)|Obtient un pointeur d'interface vers une copie de cette interface `ICorProfilerThreadEnum`.|  
|[GetCount, méthode](icorprofilerthreadenum-getcount-method.md)|Obtient le nombre de threads utilisés par l'application.|  
|[Next, méthode](icorprofilerthreadenum-next-method.md)|Obtient le nombre spécifié de threads contigus dans une collection séquentielle de threads, à commencer par la position actuelle de l’énumérateur dans la séquence.|  
|[Reset, méthode](icorprofilerthreadenum-reset-method.md)|Déplace le curseur de l'énumérateur à la position de départ de la séquence.|  
|[Skip, méthode](icorprofilerthreadenum-skip-method.md)|Fait avancer le curseur de l'énumérateur depuis sa position actuelle de manière à ignorer le nombre spécifié d'éléments.|  
  
## <a name="remarks"></a>Notes  
 L'interface `ICorProfilerThreadEnum` est un énumérateur. Elle permet au récepteur d’un tableau de récupérer des éléments de l’expéditeur à une fréquence appropriée pour le récepteur. En d'autres termes, le récepteur peut contrôler explicitement le flux d'éléments de tableau et éviter ainsi les problèmes liés au passage de tableaux volumineux en tant que paramètres de méthode.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
- [Interfaces de profilage](profiling-interfaces.md)
