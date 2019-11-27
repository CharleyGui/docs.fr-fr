---
title: CorSetENC, énumération
ms.date: 03/30/2017
api_name:
- CorSetENC
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetENC
helpviewer_keywords:
- CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type:
- apiref
ms.openlocfilehash: 39f72e670ddc700c257f50f6bad6fab702ec21b6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432773"
---
# <a name="corsetenc-enumeration"></a>CorSetENC, énumération
Contient des valeurs utilisées pour influencer le comportement pendant la génération de métadonnées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorSetENC {  
  
    MDSetENCOn                  = 0x00000001,  
    MDSetENCOff                 = 0x00000002,  
  
    MDUpdateENC                 = 0x00000001,  
    MDUpdateFull                = 0x00000002,  
    MDUpdateExtension           = 0x00000003,  
    MDUpdateIncremental         = 0x00000004,  
    MDUpdateDelta               = 0x00000005,  
    MDUpdateMask                = 0x00000007  
  
} CorSetENC;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`MDSetENCOn`|Obsolète.|  
|`MDSetENCOff`|Obsolète.|  
|`MDUpdateENC`|Indique que les métadonnées peuvent être mises à jour et que les jetons ne peuvent pas être déplacés.|  
|`MDUpdateFull`|Indique que les jetons peuvent être déplacés pendant les mises à jour.|  
|`MDUpdateExtension`|Indique que les mises à jour ne peuvent comporter que des ajouts. Les jetons ne peuvent pas être déplacés.|  
|`MDUpdateIncremental`|Indique que la compilation est incrémentielle.|  
|`MDUpdateDelta`|Indique que seules les métadonnées modifiées doivent être enregistrées.|  
|`MDUpdateMask`|Comprend `MDUpdateENC`, `MDUpdateFull` et `MDUpdateIncremental`.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
