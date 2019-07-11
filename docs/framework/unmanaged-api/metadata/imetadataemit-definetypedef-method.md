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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0777151d10149ec7311a7761bc7f6bff5ba98e0e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777487"
---
# <a name="imetadataemitdefinetypedef-method"></a>IMetaDataEmit::DefineTypeDef, méthode
Crée une définition de type pour un type common language runtime et obtient un jeton de métadonnées pour cette définition de type.  
  
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
 [in] Le nom du type au format Unicode.  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` attributs. Il s’agit d’un masque de bits de `CoreTypeAttr` valeurs.  
  
 `tkExtends`  
 [in] Le jeton de la classe de base. Il doit être un `mdTypeDef` ou un `mdTypeRef` jeton.  
  
 `rtkImplements`  
 [in] Un tableau de jetons spécifiant les interfaces qui implémente cette classe ou une interface.  
  
 `ptd`  
 [out] Le `mdTypeDef` jeton attribué.  
  
## <a name="remarks"></a>Notes  
 Un indicateur dans `dwTypeDefFlags` Spécifie si le type en cours de création est un common type system type référence (classe ou interface) ou un type de valeur système type commun.  
  
 Selon les paramètres fournis, cette méthode, comme un effet secondaire, peut également créer un `mdInterfaceImpl` enregistrement pour chaque interface héritée ou implémentée par ce type. Toutefois, cette méthode ne retourne pas un de ces `mdInterfaceImpl` jetons. Si un client souhaite ultérieurement ajouter ou modifier un `mdInterfaceImpl` jeton, il doit utiliser le `IMetaDataImport` interface pour les énumérer. Si vous souhaitez utiliser une sémantique COM de le `[default]` interface, vous devez fournir l’interface par défaut comme premier élément dans `rtkImplements`; un attribut personnalisé est défini sur la classe indiquera que la classe possède une interface par défaut (qui est censé toujours pour être le tout d’abord `mdInterfaceImpl` jeton déclaré pour la classe).  
  
 Chaque élément de la `rtkImplements` tableau contient un `mdTypeDef` ou `mdTypeRef` jeton. Le dernier élément dans le tableau doit être `mdTokenNil`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
