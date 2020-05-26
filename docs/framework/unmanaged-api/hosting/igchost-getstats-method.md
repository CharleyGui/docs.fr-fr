---
title: IGCHost::GetStats, méthode
ms.date: 03/30/2017
api_name:
- IGCHost.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type:
- apiref
ms.openlocfilehash: 67668aa7ff9faf035a047e485a8a3c8a451f45b9
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805247"
---
# <a name="igchostgetstats-method"></a>IGCHost::GetStats, méthode
Obtient les statistiques de l’état actuel du système de garbage collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pStats`  
 [in, out] Pointeur vers une structure [COR_GC_STATS](cor-gc-stats-structure.md) qui contient les statistiques relatives à l’état actuel du système garbage collection.  
  
## <a name="remarks"></a>Notes  
 Les statistiques peuvent être utilisées par un système d’allocation intelligent pour aider le système garbage collection fonctionner. Par exemple, le système d’allocation peut déterminer, après avoir examiné les statistiques, qu’il a besoin d’ajouter de la mémoire ou de forcer une collection.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** GCHost. idl, GCHost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IGCHost, interface](igchost-interface.md)
