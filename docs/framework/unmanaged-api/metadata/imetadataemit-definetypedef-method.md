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
ms.openlocfilehash: 4f1c3e823b35fcf7d5935eee111e042b2291d216
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175757"
---
# <a name="imetadataemitdefinetypedef-method"></a>IMetaDataEmit::DefineTypeDef, méthode
Crée une définition de type pour un type de temps d’exécution de langue commun, et obtient un jeton de métadonnées pour cette définition de type.  
  
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
 [dans] Le nom du type dans Unicode.  
  
 `dwTypeDefFlags`  
 [dans] `TypeDef` attributs. C’est un peu `CoreTypeAttr` de valeur.  
  
 `tkExtends`  
 [dans] Le jeton de la classe de base. Il doit être `mdTypeDef` soit `mdTypeRef` un ou un jeton.  
  
 `rtkImplements`  
 [dans] Une gamme de jetons spécifiant les interfaces que cette classe ou interface implémente.  
  
 `ptd`  
 [out] Le `mdTypeDef` jeton assigné.  
  
## <a name="remarks"></a>Notes   
 Un indicateur `dwTypeDefFlags` précise si le type créé est un type de référence système de type courant (classe ou interface) ou un type de valeur système de type commun.  
  
 Selon les paramètres fournis, cette méthode, comme un effet `mdInterfaceImpl` secondaire, peut également créer un enregistrement pour chaque interface qui est héritée ou implémentée par ce type. Cependant, cette méthode ne renvoie aucun de ces `mdInterfaceImpl` jetons. Si un client veut ajouter `mdInterfaceImpl` ou modifier plus tard `IMetaDataImport` un jeton, il doit utiliser l’interface pour l’énumérer. Si vous souhaitez utiliser la sémantique COM de l’interface, `[default]` vous `rtkImplements`devez fournir l’interface par défaut comme premier élément dans ; un attribut personnalisé défini sur la classe indiquera que la classe a `mdInterfaceImpl` une interface par défaut (qui est toujours supposé être le premier jeton déclaré pour la classe).  
  
 Chaque élément `rtkImplements` du tableau `mdTypeDef` `mdTypeRef` contient un ou un jeton. Le dernier élément dans `mdTokenNil`le tableau doit être .  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
