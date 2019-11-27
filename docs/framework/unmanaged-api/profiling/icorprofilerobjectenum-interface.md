---
title: ICorProfilerObjectEnum, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum
helpviewer_keywords:
- ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 13e1651c-9523-40ef-bfd7-87fb94519f8b
topic_type:
- apiref
ms.openlocfilehash: 95dce47a65bd437525011d2c1588d7e13adac85b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428185"
---
# <a name="icorprofilerobjectenum-interface"></a>ICorProfilerObjectEnum, interface
Fournit des méthodes pour itérer séquentiellement au sein d’une collection d’objets figés qui sont générés par le [Générateur d’images natives de Ngen. exe (Native Image Generator)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Clone, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-clone-method.md)|Obtient un pointeur d'interface vers une copie de cette interface `ICorProfilerObjectEnum`.|  
|[GetCount, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-getcount-method.md)|Obtient le nombre total d’objets figés dans la collection.|  
|[Next, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-next-method.md)|Obtient le nombre spécifié d’objets contigus dans une collection séquentielle d’objets, en commençant à la position actuelle de l’énumérateur dans la séquence.|  
|[Reset, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-reset-method.md)|Déplace le curseur de cet énumérateur à la position de départ de la séquence.|  
|[Skip, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-skip-method.md)|Avance le curseur de cet énumérateur de sa position actuelle afin que le nombre d’éléments spécifié soit ignoré.|  
  
## <a name="remarks"></a>Notes  
 L'interface `ICorProfilerObjectEnum` est un énumérateur. Elle permet au récepteur d’un tableau de récupérer des éléments de l’expéditeur à une fréquence appropriée pour le récepteur. En d’autres termes, le récepteur est en mesure de contrôler explicitement le déroulement des éléments du tableau, évitant ainsi les problèmes liés à la transmission de grands tableaux en tant que paramètres de méthode.  
  
 Utilisez [ICorProfilerInfo2 :: EnumModuleFrozenObjects (](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md) pour obtenir un pointeur vers l’interface `ICorProfilerObjectEnum`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [EnumModuleFrozenObjects, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)
