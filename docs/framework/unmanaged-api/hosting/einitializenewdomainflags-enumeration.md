---
title: EInitializeNewDomainFlags, énumération
ms.date: 03/30/2017
api_name:
- EInitializeNewDomainFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EInitializeNewDomainFlags
helpviewer_keywords:
- EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
ms.openlocfilehash: 8350b507609e63c060cda08514200d386c37a6b3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724323"
---
# <a name="einitializenewdomainflags-enumeration"></a>EInitializeNewDomainFlags, énumération

Permet à l’hôte de fournir au runtime des informations sur l’initialisation d’un domaine d’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|Aucun indicateur.|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|Informe le common language runtime (CLR) que l’hôte n’apporte pas de modifications à l’état de sécurité du domaine d’application dans la <xref:System.AppDomainManager.InitializeNewDomain%2A> méthode.|  
  
## <a name="remarks"></a>Remarques  

 La méthode [ICLRDomainManager :: SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md) prend un paramètre de type `EInitializeNewDomainFlags` .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations d'hébergement](hosting-enumerations.md)
- [SetAppDomainManagerType, méthode](iclrdomainmanager-setappdomainmanagertype-method.md)
