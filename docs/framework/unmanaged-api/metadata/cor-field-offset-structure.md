---
title: COR_FIELD_OFFSET, structure
ms.date: 03/30/2017
api_name:
- COR_FIELD_OFFSET
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_FIELD_OFFSET
helpviewer_keywords:
- COR_FIELD_OFFSET structure [.NET Framework metadata]
ms.assetid: cced5298-277f-4a5a-8ecf-a0050c1096ea
topic_type:
- apiref
ms.openlocfilehash: 1a8ab5aa5909af60089d5e4cc8092e15bc75e8cc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724180"
---
# <a name="cor_field_offset-structure"></a>COR_FIELD_OFFSET, structure

Stocke l'offset, dans une classe, du champ spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`ridOfField`|`mdFieldDef`Jeton de métadonnées qui représente le champ.|  
|`ulOffset`|Offset du champ dans sa classe.|  
  
## <a name="remarks"></a>Remarques  

 Les méthodes [IMetaDataImport :: GetClassLayout](imetadataimport-getclasslayout-method.md) et [IMetaDataEmit :: SetClassLayout,](imetadataemit-setclasslayout-method.md) prennent un paramètre de type `COR_FIELD_OFFSET` .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h, CorProf. idl  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de métadonnées](metadata-structures.md)
- [IMetaDataEmit, interface](imetadataemit-interface.md)
- [IMetaDataImport, interface](imetadataimport-interface.md)
