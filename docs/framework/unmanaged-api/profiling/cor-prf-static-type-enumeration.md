---
title: COR_PRF_STATIC_TYPE, énumération
ms.date: 03/30/2017
api_name:
- COR_PRF_STATIC_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_STATIC_TYPE
helpviewer_keywords:
- COR_PRF_STATIC_TYPE enumeration [.NET Framework profiling]
ms.assetid: 441d7809-5b65-41a5-ba64-2910a8008315
topic_type:
- apiref
ms.openlocfilehash: 2fbcbb6f6115ec48085b533dbf5611054a8235c5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696737"
---
# <a name="cor_prf_static_type-enumeration"></a>COR_PRF_STATIC_TYPE, énumération

Indique si un champ est statique et si oui, la qualité statique qui s'y applique. Ces valeurs peuvent être combinées à l’aide de l’opération or au niveau du bit pour indiquer que le champ a plusieurs qualités statiques différentes.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|Le champ n’est pas statique.|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|Le champ est un domaine d’application statique.|  
|`COR_PRF_FIELD_THREAD_STATIC`|Le champ est thread-static.|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|Le champ est context-static.|  
|`COR_PRF_FIELD_RVA_STATIC`|Le champ est adresse virtuelle relative (RVA)-static.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de profilage](profiling-enumerations.md)
