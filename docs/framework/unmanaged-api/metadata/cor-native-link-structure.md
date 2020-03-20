---
title: COR_NATIVE_LINK, structure
ms.date: 03/30/2017
api_name:
- COR_NATIVE_LINK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_NATIVE_LINK
helpviewer_keywords:
- COR_NATIVE_LINK structure [.NET Framework metadata]
ms.assetid: 6ef78d3c-1c69-4141-b687-dcb065b7a74d
topic_type:
- apiref
ms.openlocfilehash: 812b70a594b5aa933f52d36f32d96d712267ecf4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177957"
---
# <a name="cor_native_link-structure"></a>COR_NATIVE_LINK, structure
Contient des informations utilisées pour lier du code natif.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`m_linkType`|Le type à être lié dans le code natif. Cette valeur est l’une des valeurs [de CorNativeLinkType.](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)|  
|`m_flags`|Drapeaux utilisés par le lien lors de la liaison du code indigène. Cette valeur est l’une des valeurs [corNativeLinkFlags.](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)|  
|`m_entryPoint`|Le jeton de métadonnées MemberRef qui représente le point d’entrée. Le format est `lib:entrypoint`.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [CorNativeLinkType, énumération](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)
- [CorNativeLinkFlags, énumération](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
