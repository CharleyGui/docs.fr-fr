---
title: IMethodMalloc, interface
ms.date: 03/30/2017
api_name:
- IMethodMalloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc
helpviewer_keywords:
- IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type:
- apiref
ms.openlocfilehash: 3f840154d472dbcea7dfef7ba93e38c80b836734
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447548"
---
# <a name="imethodmalloc-interface"></a>IMethodMalloc, interface
Fournit une méthode pour allouer de la mémoire pour un nouveau corps de fonction MSIL (Microsoft Intermediate Language).  
  
> [!NOTE]
> L’interface `IMethodMalloc` est un allocateur de mémoire simple. Elle vous permet d’allouer de la mémoire, mais pas de la libérer.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Alloc, méthode](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|Tente d’allouer une quantité de mémoire spécifiée pour un nouveau corps de fonction MSIL.|  
  
## <a name="remarks"></a>Notes  
 Chaque allocateur est spécifique à un module et garantit que le corps de la fonction sera à un décalage positif par rapport à la base du module. La mémoire au-dessus de la base d’un module peut être précieuse, l’allocateur doit donc être utilisé pour allouer de la mémoire uniquement pour un corps de fonction.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
