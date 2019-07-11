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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2796be32154275387da891683cc5053095f534af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772328"
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
|`MDUpdateENC`|Indique que tandis que les métadonnées peuvent être mis à jour, jetons ne peut pas être déplacés.|  
|`MDUpdateFull`|Indique que les jetons peuvent être déplacées au cours des mises à jour.|  
|`MDUpdateExtension`|Indique que les mises à jour peuvent comporter que des ajouts. Les jetons ne peuvent pas être déplacées.|  
|`MDUpdateIncremental`|Indique que la compilation est incrémentielle.|  
|`MDUpdateDelta`|Indique que seules les métadonnées modifiées doivent être enregistrée.|  
|`MDUpdateMask`|Inclut `MDUpdateENC`, `MDUpdateFull` et `MDUpdateIncremental`.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr.h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
