---
title: IHostIoCompletionManager, interface
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c28d1983-83f7-46e2-990f-dbb9dc07c818
topic_type:
- apiref
ms.openlocfilehash: 90675d9be71342efa903767abbf63102b40a2c35
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804688"
---
# <a name="ihostiocompletionmanager-interface"></a>IHostIoCompletionManager, interface
Fournit des méthodes qui permettent au common language runtime (CLR) d’interagir avec les ports de terminaison d’e/s fournis par l’hôte.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Bind, méthode](ihostiocompletionmanager-bind-method.md)|Lie un handle à un port de terminaison d’e/s.|  
|[CloseIoCompletionPort, méthode](ihostiocompletionmanager-closeiocompletionport-method.md)|Ferme un port qui a été créé à l’aide d’un appel antérieur à `CreateIoCompletionPort` .|  
|[CreateIoCompletionPort, méthode](ihostiocompletionmanager-createiocompletionport-method.md)|Demande que l’hôte crée un port de terminaison d’e/s.|  
|[GetAvailableThreads, méthode](ihostiocompletionmanager-getavailablethreads-method.md)|Obtient le nombre de threads de terminaison d’e/s qui ne sont pas en cours de traitement des demandes.|  
|[GetHostOverlappedSize, méthode](ihostiocompletionmanager-gethostoverlappedsize-method.md)|Obtient la taille des données personnalisées que l’hôte envisage d’ajouter aux demandes d’e/s.|  
|[GetMaxThreads, méthode](ihostiocompletionmanager-getmaxthreads-method.md)|Obtient le nombre maximal de threads que l’hôte peut allouer aux demandes d’e/s de service.|  
|[GetMinThreads, méthode](ihostiocompletionmanager-getminthreads-method.md)|Obtient le nombre minimal de threads que l’hôte fournit pour traiter les demandes d’e/s.|  
|[InitializeHostOverlapped, méthode](ihostiocompletionmanager-initializehostoverlapped-method.md)|Fournit à l’hôte la possibilité d’initialiser toutes les données personnalisées relatives à une demande d’e/s.|  
|[SetCLRIoCompletionManager, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|Fournit à l’hôte un pointeur d’interface vers une instance [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) implémentée par le CLR.|  
|[SetMaxThreads, méthode](ihostiocompletionmanager-setmaxthreads-method.md)|Définit le nombre maximal de threads que l’hôte alloue aux demandes d’e/s de service.|  
|[SetMinThreads, méthode](ihostiocompletionmanager-setminthreads-method.md)|Définit le nombre minimal de threads que l’hôte doit allouer à l’achèvement d’e/s.|  
  
## <a name="remarks"></a>Notes  
 `IHostIoCompletionManager`correspond à l' `ICLRIoCompletionManager` interface implémentée par le CLR. Le CLR appelle les méthodes de `IHostIoCompletionManager` pour lier des handles aux ports fournis par l’hôte, et l’hôte appelle les méthodes de `ICLRIoCompletionManager` pour signaler l’achèvement des demandes d’e/s.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces d'hébergement](hosting-interfaces.md)
