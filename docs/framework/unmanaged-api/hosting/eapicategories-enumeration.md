---
title: EApiCategories, énumération
ms.date: 03/30/2017
api_name:
- EApiCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EApiCategories
helpviewer_keywords:
- EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type:
- apiref
ms.openlocfilehash: 0fd9409a5157e1013365c94f01631f130a76f54b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131211"
---
# <a name="eapicategories-enumeration"></a>EApiCategories, énumération
Décrit les catégories de fonctionnalités que l’hôte peut empêcher de s’exécuter dans du code de confiance partielle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    eNoCategory               = 0,  
    eSynchronization          = 0x1,  
    eSharedState              = 0x2,  
    eExternalProcessMgmt      = 0x4,  
    eSelfAffectingProcessMgmt = 0x8,  
    eExternalThreading        = 0x10,  
    eSelfAffectingThreading   = 0x20,  
    eSecurityInfrastructure   = 0x40,  
    eUI                       = 0x80,  
    eMayLeakOnAbort           = 0x100,  
    eAll                      = 0x1ff  
} EHostProtectionCategories;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`eAll`|Spécifie que l’exécution de toutes les classes et membres managés couverts par d’autres `EApiCategories` champs est bloquée dans du code d’un code d’approbation partiel.|  
|`eExternalProcessMgmt`|Spécifie que les classes et les membres managés qui autorisent la création, la manipulation et la destruction de processus externes ne sont pas exécutés dans du code d’un code d’approbation partiel.|  
|`eExternalThreading`|Spécifie que les classes et les membres managés qui autorisent la création, la manipulation et la destruction de threads externes ne sont pas exécutés dans du code d’un code d’approbation partiel.|  
|`eMayLeakOnAbort`|Spécifie que les types et membres managés susceptibles d’entraîner une fuite de mémoire lors de l’abandon ne peuvent pas s’exécuter dans du code d’un niveau de confiance partiel.|  
|`eNoCategory`|Spécifie qu’il n’est pas possible de bloquer l’exécution des catégories de code managé dans du code de confiance partielle.|  
|`eSecurityInfrastructure`|Spécifie que l’utilisation de l’infrastructure de sécurité common language runtime (CLR) par le code d’un point de confiance partiel est bloquée.|  
|`eSelfAffectingProcessMgmt`|Spécifie que les classes et les membres managés dont les fonctionnalités peuvent affecter le processus hébergé ne peuvent pas s’exécuter dans du code partiellement fiable.|  
|`eSelfAffectingThreading`|Spécifie que les classes et les membres managés dont les fonctionnalités peuvent affecter les threads dans le processus hébergé ne peuvent pas s’exécuter dans du code de confiance partielle.|  
|`eSharedState`|Spécifie que les classes et les membres managés qui exposent l’état partagé ne sont pas en cours d’exécution dans du code de confiance partielle.|  
|`eSynchronization`|Spécifie que les classes et les membres de common language runtime qui autorisent le code utilisateur à contenir des verrous ne pourront pas s’exécuter dans du code partiellement fiable.|  
|`eUI`|Spécifie que les classes et les membres managés qui autorisent ou nécessitent une interaction humaine ne sont pas en cours d’exécution dans du code partiellement fiable.|  
  
## <a name="remarks"></a>Notes  
 La méthode [ICLRHostProtectionManager :: SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) prend un paramètre de type `EApiCategories`.  
  
 L’énumération `EApiCategories` et la méthode `SetProtectedCategories` sont directement liées à la classe <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> managée. La classe managée est utilisée avec l’énumération <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType>, dont les valeurs correspondent directement aux valeurs de `EApiCategories`, pour marquer les membres et les types managés qui exposent les fonctionnalités correspondant aux catégories décrites par `EApiCategories`.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRHostProtectionManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
