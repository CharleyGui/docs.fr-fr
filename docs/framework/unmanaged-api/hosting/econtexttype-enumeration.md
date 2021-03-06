---
title: EContextType, énumération
ms.date: 03/30/2017
api_name:
- EContextType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EContextType
helpviewer_keywords:
- EContextType enumeration [.NET Framework hosting]
ms.assetid: 92b926a9-b87e-408a-9036-df7b752c9492
topic_type:
- apiref
ms.openlocfilehash: c6d1ace12bd07fa1f14c8570eca1f950a5c22be9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686330"
---
# <a name="econtexttype-enumeration"></a>EContextType, énumération

Décrit le contexte de sécurité du thread en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`eCurrentContext`|Indique le contexte sur le thread actuel au moment où le common language runtime (CLR) appelle la méthode [IHostSecurityManager :: GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md) , ou le contexte demandé par le CLR dans un appel à la méthode [IHostSecurityManager :: SetSecurityContext](ihostsecuritymanager-setsecuritycontext-method.md) .|  
|`eRestrictedContext`|Indique un contexte sur lequel l’hôte a des privilèges inférieurs, tels que le garbage collector ou des constructeurs de classe ou de module.|  
  
## <a name="remarks"></a>Remarques  

 Le CLR fournit l’une des `EContextType` valeurs en tant que valeur de paramètre dans les appels aux `IHostSecurityManager::GetSecurityContext` `IHostSecurityManager::SetSecurityContext` méthodes et.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IHostSecurityContext, interface](ihostsecuritycontext-interface.md)
- [IHostSecurityManager, interface](ihostsecuritymanager-interface.md)
- [Énumérations d'hébergement](hosting-enumerations.md)
