---
title: ICLRGCManager2, interface
ms.date: 03/30/2017
api_name:
- ICLRGCManager2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2
helpviewer_keywords:
- ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type:
- apiref
ms.openlocfilehash: 0f3ecc0d497eaee937647df47ba0956335a2fe41
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703946"
---
# <a name="iclrgcmanager2-interface"></a>ICLRGCManager2, interface
Fournit des méthodes qui permettent à un hôte d’interagir avec le système de garbage collection du common language runtime.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[SetGCStartupLimitsEx, méthode](iclrgcmanager2-setgcstartuplimitsex-method.md)|Définit la taille d’un segment de garbage collection et la taille maximale de la génération 0 du système garbage collection. Active la génération 0 et la taille des segments supérieure à `DWORD` .|  
  
## <a name="remarks"></a>Notes  
 Cette interface hérite de l' [interface ICLRGCManager](iclrgcmanager-interface.md).  
  
 Le common language runtime (CLR) implémente son mécanisme de garbage collection avec le <xref:System.GC> type managé. Pour plus d’informations sur le système de garbage collection, consultez [garbage collection](../../../standard/garbage-collection/index.md).  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Gestion automatique de la mémoire](../../../standard/automatic-memory-management.md)
- [COR_GC_STATS, structure](cor-gc-stats-structure.md)
- [ICLRControl, interface](iclrcontrol-interface.md)
- [Interfaces d'hébergement du CLR ajoutées dans .NET Framework 4 et 4.5](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
- [Hébergement](index.md)
