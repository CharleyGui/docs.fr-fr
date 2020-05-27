---
title: IMetaDataEmit::DefineTypeDef, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeDef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type:
- apiref
ms.openlocfilehash: dc064b00e32bb6b1d8c2d0c20f571b35919eae23
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009338"
---
# <a name="imetadataemitdefinetypedef-method"></a>IMetaDataEmit::DefineTypeDef, méthode
Crée une définition de type pour un type de common language runtime et obtient un jeton de métadonnées pour cette définition de type.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineTypeDef (
    [in]  LPCWSTR     szTypeDef,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `szTypeDef`  
 dans Nom du type en Unicode.  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` attributs. Il s’agit d’un masque de `CoreTypeAttr` valeur de valeurs.  
  
 `tkExtends`  
 dans Jeton de la classe de base. Il doit s’agir d’un `mdTypeDef` ou d’un `mdTypeRef` jeton.  
  
 `rtkImplements`  
 dans Tableau de jetons spécifiant les interfaces implémentées par cette classe ou cette interface.  
  
 `ptd`  
 à `mdTypeDef`Jeton assigné.  
  
## <a name="remarks"></a>Remarques  
 Un indicateur dans `dwTypeDefFlags` spécifie si le type en cours de création est un type de référence de système de type commun (classe ou interface) ou un type de valeur de système de type commun.  
  
 Selon les paramètres fournis, cette méthode, en tant qu’effet secondaire, peut également créer un `mdInterfaceImpl` enregistrement pour chaque interface héritée ou implémentée par ce type. Toutefois, cette méthode ne retourne pas l’un de ces `mdInterfaceImpl` jetons. Si un client souhaite ajouter ou modifier ultérieurement un `mdInterfaceImpl` jeton, il doit utiliser l' `IMetaDataImport` interface pour les énumérer. Si vous souhaitez utiliser la sémantique COM de l' `[default]` interface, vous devez fournir l’interface par défaut en tant que premier élément dans `rtkImplements` ; un attribut personnalisé défini sur la classe indique que la classe a une interface par défaut (qui est toujours supposée être le premier `mdInterfaceImpl` jeton déclaré pour la classe).  
  
 Chaque élément du `rtkImplements` tableau contient un `mdTypeDef` jeton ou `mdTypeRef` . Le dernier élément du tableau doit être `mdTokenNil` .  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](imetadataemit-interface.md)
- [IMetaDataEmit2, interface](imetadataemit2-interface.md)
