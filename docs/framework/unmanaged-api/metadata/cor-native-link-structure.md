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
ms.openlocfilehash: d03c22c455f0e44ce32d4593d9eee50ceef94a22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443949"
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
|`m_linkType`|Type à lier en code natif. Cette valeur est l’une des valeurs [CorNativeLinkType,](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) .|  
|`m_flags`|Indicateurs utilisés par l’éditeur de liens lors de la liaison de code natif. Cette valeur est l’une des valeurs [CorNativeLinkFlags,](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) .|  
|`m_entryPoint`|Jeton de métadonnées MemberRef qui représente le point d’entrée. Le format est `lib:entrypoint`.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [CorNativeLinkType, énumération](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)
- [CorNativeLinkFlags, énumération](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
