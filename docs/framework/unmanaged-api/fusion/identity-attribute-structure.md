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
ms.openlocfilehash: 8b7edf1cc642228c4a79c855b51727264f31741c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107980"
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
  
## <a name="remarks"></a>Notes  
 La structure `IDENTITY_ATTRIBUTE` contient trois pointeurs vers des chaînes de caractères se terminant par un caractère null. Ces trois chaînes décrivent un attribut.  
  
 Une instance d’une structure `IDENTITY_ATTRIBUTE` est associée à une instance d’une structure [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) . La structure `IDENTITY_ATTRIBUTE` contient les chaînes réelles, et la structure de `IDENTITY_ATTRIBUTE_BLOB` correspondante répertorie les offsets aux trois chaînes répertoriées dans la structure `IDENTITY_ATTRIBUTE`.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Isolation. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IDefinitionIdentity, interface](idefinitionidentity-interface.md)
- [IDENTITY_ATTRIBUTE_BLOB, structure](identity-attribute-blob-structure.md)
- [Structures de fusion](fusion-structures.md)
