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
ms.openlocfilehash: 031996813718a074eebab62ff54a2de52b898c22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450216"
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
 [in] attributs `TypeDef`. Il s’agit d’un masque de ré`CoreTypeAttr` valeurs.  
  
 `tkExtends`  
 dans Jeton de la classe de base. Il doit s’agir d’un `mdTypeDef` ou d’un jeton `mdTypeRef`.  
  
 `rtkImplements`  
 dans Tableau de jetons spécifiant les interfaces implémentées par cette classe ou cette interface.  
  
 `ptd`  
 à Jeton `mdTypeDef` assigné.  
  
## <a name="remarks"></a>Notes  
 Un indicateur dans `dwTypeDefFlags` spécifie si le type en cours de création est un type de référence de système de type commun (classe ou interface) ou un type de valeur de système de type commun.  
  
 Selon les paramètres fournis, cette méthode, en tant qu’effet secondaire, peut également créer un enregistrement `mdInterfaceImpl` pour chaque interface héritée ou implémentée par ce type. Toutefois, cette méthode ne retourne pas l’un de ces `mdInterfaceImpl` jetons. Si un client souhaite ajouter ou modifier ultérieurement un jeton `mdInterfaceImpl`, il doit utiliser l’interface `IMetaDataImport` pour les énumérer. Si vous souhaitez utiliser la sémantique COM de l’interface `[default]`, vous devez fournir l’interface par défaut en tant que premier élément de `rtkImplements`; un ensemble d’attributs personnalisés sur la classe indique que la classe a une interface par défaut (qui est toujours supposée être la première `mdInterfaceImpl` jeton déclaré pour la classe).  
  
 Chaque élément du tableau `rtkImplements` contient un jeton `mdTypeDef` ou `mdTypeRef`. Le dernier élément du tableau doit être `mdTokenNil`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
