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
ms.openlocfilehash: 15f573ebc07bcf08a1ab8f5a5bbb88e940c5c8dc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724167"
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
|`m_linkType`|Type à lier en code natif. Cette valeur est l’une des valeurs [CorNativeLinkType,](cornativelinktype-enumeration.md) .|  
|`m_flags`|Indicateurs utilisés par l’éditeur de liens lors de la liaison de code natif. Cette valeur est l’une des valeurs [CorNativeLinkFlags,](cornativelinkflags-enumeration.md) .|  
|`m_entryPoint`|Jeton de métadonnées MemberRef qui représente le point d’entrée. Le format est `lib:entrypoint`.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de métadonnées](metadata-structures.md)
- [CorNativeLinkType, énumération](cornativelinktype-enumeration.md)
- [CorNativeLinkFlags, énumération](cornativelinkflags-enumeration.md)
