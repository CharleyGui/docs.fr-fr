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
ms.openlocfilehash: 12b97b28383eb7c39f20ee0e88f55d48e60ad956
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494097"
---
# <a name="imethodmalloc-interface"></a>IMethodMalloc, interface
Fournit une méthode pour allouer de la mémoire pour un nouveau corps de fonction MSIL (Microsoft Intermediate Language).  
  
> [!NOTE]
> L' `IMethodMalloc` interface est un allocateur de mémoire simple. Elle vous permet d’allouer de la mémoire, mais pas de la libérer.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Alloc, méthode](imethodmalloc-alloc-method.md)|Tente d’allouer une quantité de mémoire spécifiée pour un nouveau corps de fonction MSIL.|  
  
## <a name="remarks"></a>Remarques  
 Chaque allocateur est spécifique à un module et garantit que le corps de la fonction sera à un décalage positif par rapport à la base du module. La mémoire au-dessus de la base d’un module peut être précieuse, l’allocateur doit donc être utilisé pour allouer de la mémoire uniquement pour un corps de fonction.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](profiling-interfaces.md)
