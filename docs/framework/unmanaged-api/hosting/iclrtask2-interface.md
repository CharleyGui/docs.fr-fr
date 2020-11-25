---
title: ICLRTask2, interface
ms.date: 03/30/2017
api_name:
- ICLRTask2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2
helpviewer_keywords:
- ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type:
- apiref
ms.openlocfilehash: 9332b3462ba389783a113d173e32850d40427ce2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720228"
---
# <a name="iclrtask2-interface"></a>ICLRTask2, interface

Fournit toutes les fonctionnalités de l’interface [ICLRTask](iclrtask-interface.md) ; en outre, fournit des méthodes qui permettent de retarder les abandons de thread sur le thread actuel.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[BeginPreventAsyncAbort, méthode](iclrtask2-beginpreventasyncabort-method.md)|Retarde les nouvelles demandes d’abandon de thread sur le thread actuel.|  
|[BeginPreventAsyncAbort, méthode](iclrtask2-endpreventasyncabort-method.md)|Autorise les demandes d’abandon de thread nouvelles ou en attente pour entraîner des abandons de threads sur le thread actuel.|  
  
## <a name="remarks"></a>Remarques  

 L' `ICLRTask2` interface hérite de l' `ICLRTask` interface et ajoute des méthodes qui permettent à l’hôte de retarder les abandons de thread, afin de protéger une région de code qui ne doit pas échouer. `BeginPreventAsyncAbort`L’appel de incrémente le compteur Delay-thread-abort pour le thread actuel, puis l’appelle `EndPreventAsyncAbort` décrémente. Les appels à `BeginPreventAsyncAbort` et `EndPreventAsyncAbort` peuvent être imbriqués. Tant que le compteur est supérieur à zéro, les abandons de thread pour le thread actuel sont retardés.  
  
 Si les appels à `BeginPreventAsyncAbort` et ne `EndPreventAsyncAbort` sont pas couplés, il est possible d’atteindre un État dans lequel les abandons de thread ne peuvent pas être remis au thread actuel.  
  
 Le délai n’est pas respecté pour un thread qui s’arrête lui-même.  
  
 La fonctionnalité exposée par cette fonctionnalité est utilisée en interne par la machine virtuelle. Une utilisation incorrecte de ces méthodes peut entraîner un comportement non spécifié dans la machine virtuelle. Par exemple, l’appel de `EndPreventAsyncAbort` sans tout d’abord appeler `BeginPreventAsyncAbort` peut affecter la valeur zéro au compteur lorsque la machine virtuelle l’a incrémentée précédemment. De même, le compteur interne n’est pas vérifié pour le dépassement de capacité. Si elle dépasse sa limite intégrale parce qu’elle est incrémentée par l’hôte et la machine virtuelle, le comportement résultant n’est pas spécifié.  
  
 Pour plus d’informations sur les membres hérités de `ICLRTask` et sur les autres utilisations de cette interface, consultez l’interface [ICLRTask](iclrtask-interface.md) .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRTask, interface](iclrtask-interface.md)
- [ICLRTaskManager, interface](iclrtaskmanager-interface.md)
- [IHostTask, interface](ihosttask-interface.md)
- [IHostTaskManager, interface](ihosttaskmanager-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
