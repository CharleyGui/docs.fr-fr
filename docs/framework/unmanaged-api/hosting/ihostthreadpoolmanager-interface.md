---
title: IHostThreadPoolManager, interface
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager
helpviewer_keywords:
- IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: c3a2cd90-7c4e-4374-bb87-b41befb8344f
topic_type:
- apiref
ms.openlocfilehash: b6625b0ef4dc3de4067514a0b39849c7a958d5c4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730758"
---
# <a name="ihostthreadpoolmanager-interface"></a>IHostThreadPoolManager, interface

Fournit des méthodes qui permettent au common language runtime (CLR) de configurer le pool de threads et de mettre en file d’attente des éléments de travail dans le pool de threads.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetAvailableThreads, méthode](ihostthreadpoolmanager-getavailablethreads-method.md)|Obtient le nombre de threads dans le pool de threads qui ne traitent pas actuellement des éléments de travail.|  
|[GetMaxThreads, méthode](ihostthreadpoolmanager-getmaxthreads-method.md)|Obtient le nombre maximal de threads que l’hôte conserve simultanément dans le pool de threads.|  
|[GetMinThreads, méthode](ihostthreadpoolmanager-getminthreads-method.md)|Obtient le nombre minimal de threads inactifs que l’hôte gère en prévision des demandes.|  
|[QueueUserWorkItem, méthode](ihostthreadpoolmanager-queueuserworkitem-method.md)|Met en file d’attente une fonction pour l’exécution et fournit un objet contenant les données que la fonction doit utiliser.|  
|[SetMaxThreads, méthode](ihostthreadpoolmanager-setmaxthreads-method.md)|Définit le nombre maximal de threads que l’hôte peut conserver dans le pool de threads.|  
|[SetMinThreads, méthode](ihostthreadpoolmanager-setminthreads-method.md)|Définit le nombre minimal de threads inactifs que l’hôte doit gérer en prévision des demandes.|  
  
## <a name="remarks"></a>Remarques  

 L’hôte n’est pas requis pour configurer le pool de threads à l’aide des valeurs spécifiées dans les appels aux `SetMaxThreads` `SetMinThreads` méthodes et. Dans ce cas, l’hôte doit retourner une valeur HRESULT de E_NOTIMPL à partir de ces méthodes.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [Interfaces d'hébergement](hosting-interfaces.md)
