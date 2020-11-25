---
title: COR_PRF_RUNTIME_TYPE, énumération
ms.date: 03/30/2017
api_name:
- COR_PRF_RUNTIME_TYPE Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_RUNTIME_TYPE
helpviewer_keywords:
- COR_PRF_RUNTIME_TYPE enumeration [.NET Framework profiling]
ms.assetid: 35449514-333f-4918-9c60-7aa198d655d2
topic_type:
- apiref
ms.openlocfilehash: b599a97f414491ff80000f99551a727b86ae13de
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696750"
---
# <a name="cor_prf_runtime_type-enumeration"></a>COR_PRF_RUNTIME_TYPE, énumération

Contient des valeurs qui indiquent la version du common language runtime (CLR) : Desktop ou CoreCLR, qui est utilisé dans Silverlight.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|Version de bureau du CLR.|  
|`COR_PRF_CORE_CLR`|Version principale du CLR, utilisée dans Silverlight.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Spécifications  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de profilage](profiling-enumerations.md)
