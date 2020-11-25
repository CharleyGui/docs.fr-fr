---
title: ASM_CACHE_FLAGS, énumération
ms.date: 03/30/2017
api_name:
- ASM_CACHE_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_CACHE_FLAGS
helpviewer_keywords:
- ASM_CACHE_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 82e9a7da-321b-48b8-b239-52eaffda6be8
topic_type:
- apiref
ms.openlocfilehash: 6c6fab627f21977e85f9885ca4b49a0276faa5ce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732162"
---
# <a name="asm_cache_flags-enumeration"></a>ASM_CACHE_FLAGS, énumération

Indique la source d’un assembly qui est représenté par [IAssemblyCacheItem](iassemblycacheitem-interface.md) dans le global assembly cache.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08,  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|Énumère le cache des assemblys précompilés à l’aide de Ngen.exe.|  
|`ASM_CACHE_GAC`|Énumère les Global Assembly Cache.|  
|`ASM_CACHE_DOWNLOAD`|Énumère les assemblys qui ont été téléchargés à la demande ou qui ont été copiés par des clichés instantanés.|  
|`ASM_CACHE_ROOT`|Indique que la fonction [GetCachePath](getcachepath-function.md) doit retourner le chemin d’accès au global assembly cache pour la Common Language Runtime (CLR) version 2,0. Significatif uniquement dans le contexte d’un appel à [GetCachePath](getcachepath-function.md).|  
|`ASM_CACHE_ROOT_EX`|Indique que la fonction [GetCachePath](getcachepath-function.md) doit retourner le chemin d’accès au global assembly cache de CLR version 4. Significatif uniquement dans le contexte d’un appel à [GetCachePath](getcachepath-function.md).|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetCachePath, fonction](getcachepath-function.md)
- [IAssemblyCacheItem, interface](iassemblycacheitem-interface.md)
- [Énumérations de fusion](fusion-enumerations.md)
