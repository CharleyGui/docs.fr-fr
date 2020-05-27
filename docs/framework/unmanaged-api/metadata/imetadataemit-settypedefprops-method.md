---
title: IMetaDataEmit::SetTypeDefProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetTypeDefProps
helpviewer_keywords:
- SetTypeDefProps method [.NET Framework metadata]
- IMetaDataEmit::SetTypeDefProps method [.NET Framework metadata]
ms.assetid: 480d596a-759f-4d29-ac1a-3dbff8f3544d
topic_type:
- apiref
ms.openlocfilehash: b05527f118de059c674ea659b1a22b7895126cf4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007765"
---
# <a name="imetadataemitsettypedefprops-method"></a>IMetaDataEmit::SetTypeDefProps, méthode
Définit les fonctionnalités d’un type défini par un appel antérieur à [IMetaDataEmit ::D efinetypedef](imetadataemit-definetypedef-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[]
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `td`  
 dans `mdTypeDef`Jeton obtenu à partir de l’appel d’origine vers [IMetaDataEmit ::D efinetypedef](imetadataemit-definetypedef-method.md).  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` attributs. Il s’agit d’un masque de `CorTypeAttr` valeur de valeurs.  
  
 `tkExtends`  
 dans `mdToken`De la classe de base. Obtenu à partir d’un appel précédent à [IMetaDataEmit ::D efineimporttype](imetadataemit-defineimporttype-method.md), ou `null` .  
  
 `rtkImplements[]`  
 dans Tableau de jetons pour les interfaces implémentées par ce type. Ces `mdTypeRef` jetons sont obtenus à l’aide de [IMetaDataEmit ::D efineimporttype](imetadataemit-defineimporttype-method.md). Le dernier élément du tableau doit être `mdTokenNil` .  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](imetadataemit-interface.md)
- [IMetaDataEmit2, interface](imetadataemit2-interface.md)
