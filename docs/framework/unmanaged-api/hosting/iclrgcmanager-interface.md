---
title: ICLRGCManager, interface
ms.date: 03/30/2017
api_name:
- ICLRGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager
helpviewer_keywords:
- ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type:
- apiref
ms.openlocfilehash: f878e2f1f86bc42c0ff5abada8d7df4feb9ed228
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504184"
---
# <a name="iclrgcmanager-interface"></a>ICLRGCManager, interface
Fournit des méthodes qui permettent à un hôte d’interagir avec le système de garbage collection du common language runtime.  
  
> [!NOTE]
> À partir de la .NET Framework 4,5, vous pouvez utiliser la méthode [ICLRGCManager2 :: setgcstartuplimitsex,](iclrgcmanager2-setgcstartuplimitsex-method.md) pour définir la taille d’un segment garbage collection et la taille maximale de la génération 0 du système garbage collection sur des valeurs supérieures à la `DWORD` limite imposée par la méthode [SetGCStartupLimits (](iclrgcmanager-setgcstartuplimits-method.md) .  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Collect, méthode](iclrgcmanager-collect-method.md)|Force une garbage collection pour la génération spécifiée.|  
|[GetStats, méthode](iclrgcmanager-getstats-method.md)|Obtient un ensemble de statistiques actuelles sur le système de garbage collection.|  
|[SetGCStartupLimits, méthode](iclrgcmanager-setgcstartuplimits-method.md)|Définit la taille d’un segment de garbage collection et la taille maximale de la génération 0 du système garbage collection.|  
  
## <a name="remarks"></a>Remarques  
 Le common language runtime (CLR) implémente son mécanisme de garbage collection avec le <xref:System.GC> type managé. Pour plus d’informations sur le système de garbage collection, consultez [garbage collection](../../../standard/garbage-collection/index.md).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Gestion automatique de la mémoire](../../../standard/automatic-memory-management.md)
- [COR_GC_STATS, structure](cor-gc-stats-structure.md)
- [ICLRControl, interface](iclrcontrol-interface.md)
- [Interfaces d'hébergement du CLR](clr-hosting-interfaces.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
- [Hosting](index.md)
