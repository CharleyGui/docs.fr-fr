---
title: IDENTITY_ATTRIBUTE, structure
ms.date: 03/30/2017
api_name:
- IDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE
helpviewer_keywords:
- IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type:
- apiref
ms.openlocfilehash: da4b1d6f2a7079ef33859fce29c9555ac06fcfc2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725649"
---
# <a name="identity_attribute-structure"></a>IDENTITY_ATTRIBUTE, structure

Contient des informations sur les attributs de métadonnées concernant une instance de [IDefinitionIdentity](idefinitionidentity-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`pszNamespace`|Pointeur vers une chaîne de caractères se terminant par un caractère null qui contient l’espace de noms dans lequel se trouve l’attribut.|  
|`pszName`|Pointeur vers une chaîne de caractères se terminant par un caractère null qui contient le nom de l’attribut.|  
|`pszValue`|Pointeur vers une chaîne de caractères se terminant par un caractère null qui contient la valeur de l’attribut.|  
  
## <a name="remarks"></a>Remarques  

 La `IDENTITY_ATTRIBUTE` structure contient trois pointeurs vers des chaînes de caractères se terminant par un caractère null. Ces trois chaînes décrivent un attribut.  
  
 Une instance d’une `IDENTITY_ATTRIBUTE` structure est associée à une instance d’une structure [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) . La `IDENTITY_ATTRIBUTE` structure contient les chaînes réelles et la structure correspondante `IDENTITY_ATTRIBUTE_BLOB` répertorie les offsets aux trois chaînes répertoriées dans la `IDENTITY_ATTRIBUTE` structure.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Isolation. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IDefinitionIdentity, interface](idefinitionidentity-interface.md)
- [IDENTITY_ATTRIBUTE_BLOB, structure](identity-attribute-blob-structure.md)
- [Structures de fusion](fusion-structures.md)
