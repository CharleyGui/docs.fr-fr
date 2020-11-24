---
title: IGCHost::GetThreadStats, méthode
ms.date: 03/30/2017
api_name:
- IGCHost.GetThreadStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetThreadStats
helpviewer_keywords:
- IGCHost::GetThreadStats method [.NET Framework hosting]
- GetThreadStats method [.NET Framework hosting]
ms.assetid: 826baa9b-9218-4736-a509-7ab193b125a0
topic_type:
- apiref
ms.openlocfilehash: c48b580e632d67db5a9826c210415adab1bdba96
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95670067"
---
# <a name="igchostgetthreadstats-method"></a>IGCHost::GetThreadStats, méthode

Obtient les statistiques par thread pour garbage collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pFiberCookie`  
 dans Pointeur vers un cookie Fiber qui spécifie le thread pour lequel les statistiques doivent être récupérées.  
  
 `pStats`  
 [in, out] Pointeur vers une structure [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) qui contient les statistiques garbage collection pour le thread spécifié.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** GCHost. idl, GCHost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IGCHost, interface](igchost-interface.md)
