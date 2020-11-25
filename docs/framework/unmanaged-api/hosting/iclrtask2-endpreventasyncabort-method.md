---
title: ICLRTask2::EndPreventAsyncAbort, méthode
ms.date: 03/30/2017
api_name:
- ICLRTask2.EndPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::EndPreventAsyncAbort
helpviewer_keywords:
- EndPreventAsyncAbort method [.NET Framework hosting]
- ICLRTask2::EndPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: d8013659-e3df-44b3-814f-a6b534ce62f8
topic_type:
- apiref
ms.openlocfilehash: 7f8963403c60815bbf1cd3008ed7fec73d849fea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720254"
---
# <a name="iclrtask2endpreventasyncabort-method"></a>ICLRTask2::EndPreventAsyncAbort, méthode

Autorise les demandes d’abandon de thread nouvelles ou en attente pour entraîner des abandons de threads sur le thread actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a>Valeur de retour  

 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|HOST_E_INVALIDOPERATION|La méthode a été appelée sur un thread qui n’est pas le thread actuel.|  
  
## <a name="remarks"></a>Remarques  

 L’appel de cette méthode décrémente d’une unité le compteur de temporisation de thread-abandon du thread actuel.  
  
 Les appels à [ICLRTask2 :: BeginPreventAsyncAbort,](iclrtask2-beginpreventasyncabort-method.md) et `EndPreventAsyncAbort` peuvent être imbriqués. Tant que le compteur est supérieur à zéro, les abandons de thread pour le thread actuel sont retardés.  
  
 La fonctionnalité exposée par cette fonctionnalité est utilisée en interne par la machine virtuelle. Une utilisation incorrecte de ces méthodes peut entraîner un comportement non spécifié dans la machine virtuelle. Par exemple, l’appel de `EndPreventAsyncAbort` sans tout d’abord appeler `BeginPreventAsyncAbort` peut affecter la valeur zéro au compteur lorsque la machine virtuelle l’a incrémentée précédemment. De même, le compteur interne n’est pas vérifié pour le dépassement de capacité. Si elle dépasse sa limite intégrale parce qu’elle est incrémentée par l’hôte et la machine virtuelle, le comportement résultant n’est pas spécifié.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [BeginPreventAsyncAbort, méthode](iclrtask2-beginpreventasyncabort-method.md)
- [ICLRTask2, interface](iclrtask2-interface.md)
- [ICLRTaskManager, interface](iclrtaskmanager-interface.md)
- [IHostTask, interface](ihosttask-interface.md)
- [IHostTaskManager, interface](ihosttaskmanager-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
