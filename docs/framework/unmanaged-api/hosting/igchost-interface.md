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
ms.openlocfilehash: 9d6c9d22f4e50c21e2f41b7efd402907ff5843db
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805219"
---
# <a name="igchost-interface"></a>IGCHost, interface
Fournit des méthodes pour obtenir des informations sur le système de garbage collection et pour contrôler certains aspects de garbage collection.  
  
> [!NOTE]
> À partir de la .NET Framework 4,5, vous pouvez utiliser la méthode [IGCHost2 :: setgcstartuplimitsex,](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) pour définir la taille d’un segment garbage collection et la taille maximale de la génération 0 du système garbage collection sur des valeurs supérieures à la `DWORD` limite imposée par la méthode [SetGCStartupLimits (](igchost-setgcstartuplimits-method.md) .  
  
> [!NOTE]
> Cette interface n’est destinée qu’à une utilisation par des experts. Cela peut affecter les performances d’une application si elle est utilisée de manière incorrecte.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Collect, méthode](igchost-collect-method.md)|Force une collection à se produire pour la génération donnée, quel que soit l’état du garbage collection actuel.|  
|[GetStats, méthode](igchost-getstats-method.md)|Obtient les statistiques de l’état actuel du système de garbage collection.|  
|[GetThreadStats, méthode](igchost-getthreadstats-method.md)|Obtient les statistiques par thread pour garbage collection.|  
|[SetGCStartupLimits, méthode](igchost-setgcstartuplimits-method.md)|Définit la taille du segment et la taille maximale de la génération 0.|  
|[SetVirtualMemLimit, méthode](igchost-setvirtualmemlimit-method.md)|Définit la taille maximale de la mémoire virtuelle du Runtime.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** GCHost. idl, GCHost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces d'hébergement](hosting-interfaces.md)
- [CorRuntimeHost, coclasse](corruntimehost-coclass.md)
