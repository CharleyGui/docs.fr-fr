---
title: EMemoryCriticalLevel, énumération
ms.date: 03/30/2017
api_name:
- EMemoryCriticalLevel
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryCriticalLevel
helpviewer_keywords:
- EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type:
- apiref
ms.openlocfilehash: 3b9ad4b40ce94420f2ab5fc25335c41dec15dc09
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720549"
---
# <a name="ememorycriticallevel-enumeration"></a>EMemoryCriticalLevel, énumération

Contient des valeurs qui indiquent l’impact d’un échec lorsqu’une allocation de mémoire spécifique a été demandée, mais ne peut pas être satisfaite.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`eAppDomainCritical`|Indique que l’allocation est essentielle pour l’exécution du code managé dans le domaine qui a demandé l’allocation. Si la mémoire ne peut pas être allouée, le CLR ne peut pas garantir que le domaine est toujours utilisable. L’hôte décide de l’action à entreprendre lorsque l’allocation ne peut pas être satisfaite. Elle peut demander au CLR d’abandonner `AppDomain` automatiquement ou de l’autoriser à continuer à s’exécuter en appelant des méthodes sur [ICLRPolicyManager](iclrpolicymanager-interface.md).|  
|`eProcessCritical`|Indique que l’allocation est essentielle à l’exécution du code managé dans le processus. Cette valeur est utilisée lors du démarrage et lors de l’exécution des finaliseurs. Si la mémoire ne peut pas être allouée, le CLR ne peut pas fonctionner dans le processus. Si l’allocation échoue, le CLR est effectivement désactivé. Tous les appels suivants dans le CLR échouent avec HOST_E_CLRNOTAVAILABLE.|  
|`eTaskCritical`|Indique que l’allocation est essentielle à l’exécution de la tâche qui a demandé l’allocation. Si la mémoire ne peut pas être allouée, le CLR ne peut pas garantir que la tâche peut être exécutée. En cas de défaillance, le CLR déclenche une <xref:System.Threading.ThreadAbortException> sur le thread du système d’opération physique.|  
  
## <a name="remarks"></a>Remarques  

 Les méthodes d’allocation de mémoire définies dans les interfaces [IHostMemoryManager](ihostmemorymanager-interface.md) et [IHostMalloc](ihostmalloc-interface.md) prennent un paramètre de ce type. En fonction de la gravité d’un échec, un hôte peut décider s’il faut faire échouer la demande d’allocation immédiatement ou attendre qu’elle soit satisfaite.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRMemoryNotificationCallback, interface](iclrmemorynotificationcallback-interface.md)
- [Énumérations d'hébergement](hosting-enumerations.md)
