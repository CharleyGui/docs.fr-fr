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
ms.openlocfilehash: bac29b5950f1547c5c60ac716d40d2ef4b1a2cc2
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842478"
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
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [Interfaces d'hébergement](hosting-interfaces.md)
