---
title: IGCHost2, interface
ms.date: 03/30/2017
api_name:
- IGCHost2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2
helpviewer_keywords:
- IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type:
- apiref
ms.openlocfilehash: 976673a0caab4e041cc80e5536544c195fcf692a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805176"
---
# <a name="igchost2-interface"></a>IGCHost2, interface
Fournit des méthodes pour obtenir des informations sur le système de garbage collection et pour contrôler certains aspects de garbage collection.  
  
> [!NOTE]
> Pour un nouveau développement, nous vous recommandons d’utiliser à la place l’interface [ICLRGCManager2](iclrgcmanager2-interface.md) .  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[SetGCStartupLimitsEx, méthode](igchost2-setgcstartuplimitsex-method.md)|Définit la taille du segment et la taille maximale de la génération 0. Active la génération 0 et la taille des segments supérieure à `DWORD` .|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** GCHost. idl, GCHost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces d'hébergement](hosting-interfaces.md)
- [Interfaces d'hébergement du CLR](clr-hosting-interfaces.md)
- [CorRuntimeHost, coclasse](corruntimehost-coclass.md)
