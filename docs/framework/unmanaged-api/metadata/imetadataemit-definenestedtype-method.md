---
title: IMetaDataEmit::DefineNestedType, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineNestedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type:
- apiref
ms.openlocfilehash: 99dc141cca0f911c8dd65645f6c22d950cc678d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719539"
---
# <a name="imetadataemitdefinenestedtype-method"></a>IMetaDataEmit::DefineNestedType, méthode

Crée la signature de métadonnées d’une définition de type, retourne un `mdTypeDef` jeton pour ce type et spécifie que le type défini est un membre du type référencé par le `tdEncloser` paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineNestedType (
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [in]  mdTypeDef   tdEncloser,
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `szTypeDef`  
 dans Nom du type en Unicode.  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` attributs. Il s’agit d’un masque de `CorTypeAttr` valeur de valeurs.  
  
 `tkExtends`  
 dans Jeton de la classe de base. Il s’agit soit d’un jeton, soit d’un `mdTypeDef` `mdTypeRef` jeton.  
  
 `rtkImplements`[]  
 dans Tableau de jetons qui spécifient les interfaces implémentées par cette classe ou cette interface.  
  
 `tdEncloser`  
 dans Jeton du type englobant. Le dernier élément du tableau doit être `mdTokenNil` .  
  
 `ptd`  
 à `mdTypeDef` Jeton assigné.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](imetadataemit-interface.md)
- [IMetaDataEmit2, interface](imetadataemit2-interface.md)
