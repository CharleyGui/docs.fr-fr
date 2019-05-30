---
title: IGCHost, interface
ms.date: 03/30/2017
api_name:
- IGCHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost
helpviewer_keywords:
- IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 167e2477e5185112408793e145bc5a4fabea7fc8
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377619"
---
# <a name="igchost-interface"></a>IGCHost, interface
Fournit des méthodes pour obtenir des informations sur le système de garbage collection et contrôler certains aspects du garbage collection.  
  
> [!NOTE]
>  À compter de .NET Framework 4.5, vous pouvez utiliser la [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) pour définir la taille d’un segment de garbage collection et la taille maximale de la génération du système de nettoyage 0 pour les valeurs supérieure (méthode) le `DWORD` limite imposée par le [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) (méthode).  
  
> [!NOTE]
>  Cette interface est destinée uniquement à une utilisation expert. Il peut affecter les performances d’une application pour une utilisation incorrecte.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Collect, méthode](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|Force une collection pour la génération donnée, quel que soit l’état du garbage collection en cours.|  
|[GetStats, méthode](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|Obtient les statistiques pour l’état actuel du système garbage collection.|  
|[GetThreadStats, méthode](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|Obtient les statistiques par thread pour le garbage collection.|  
|[SetGCStartupLimits, méthode](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|Définit la taille du segment et la taille maximale pour la génération 0.|  
|[SetVirtualMemLimit, méthode](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|Définit la taille maximale de mémoire virtuelle du runtime.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** GCHost.idl, GCHost.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CorRuntimeHost, coclasse](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
