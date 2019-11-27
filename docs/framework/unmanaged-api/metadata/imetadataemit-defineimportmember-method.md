---
title: IMetaDataEmit::DefineImportMember, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportMember
helpviewer_keywords:
- DefineImportMember method [.NET Framework metadata]
- IMetaDataEmit::DefineImportMember method [.NET Framework metadata]
ms.assetid: c7dd94c6-335b-46ff-9dfe-505056db5673
topic_type:
- apiref
ms.openlocfilehash: 75711b3d87699ff5db21a04351ff0acaccabb5aa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431855"
---
# <a name="imetadataemitdefineimportmember-method"></a>IMetaDataEmit::DefineImportMember, méthode
Crée une référence au membre spécifié d’un type ou d’un module qui est défini en dehors de la portée actuelle et définit un jeton pour cette référence.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineImportMember (   
    [in]  IMetaDataAssemblyImport  *pAssemImport,   
    [in]  const void               *pbHashValue,   
    [in]  ULONG                    cbHashValue,  
    [in]  IMetaDataImport          *pImport,   
    [in]  mdToken                  mbMember,   
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,   
    [in]  mdToken                  tkParent,   
    [out] mdMemberRef              *pmr   
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pAssemImport`  
 dans Interface [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) qui représente l’assembly à partir duquel le membre cible est importé.  
  
 `pbHashValue`  
 dans Tableau qui contient le hachage de l’assembly spécifié par `pAssemImport`.  
  
 `cbHashValue`  
 [in] Nombre d'octets dans le tableau `pbHashValue`.  
  
 `pImport`  
 dans Interface [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) qui représente la portée des métadonnées à partir de laquelle le membre cible est importé.  
  
 `mbMember`  
 dans Jeton de métadonnées qui spécifie le membre cible. Le jeton peut être une `mdMethodDef` (pour une méthode membre), `mdProperty` (pour une propriété de membre) ou `mdFieldDef` (pour un champ de membre).  
  
 `pAssemEmit`  
 dans Interface [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) qui représente l’assembly dans lequel le membre cible est importé.  
  
 `tkParent`  
 dans Jeton `mdTypeRef` ou `mdModuleRef` pour le type ou le module, respectivement, qui possède le membre cible.  
  
 `pmr`  
 à Jeton `mdMemberRef` qui est défini dans la portée actuelle pour la référence de membre.  
  
## <a name="remarks"></a>Notes  
 La méthode `DefineImportMember` recherche le membre, spécifié par `mbMember`, qui est défini dans une autre étendue, spécifié par `pImport`et récupère ses propriétés. Elle utilise ces informations pour appeler la méthode [IMetaDataEmit ::D efinememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) dans l’étendue actuelle afin de créer la référence de membre.  
  
 En règle générale, avant d’utiliser la méthode `DefineImportMember`, vous devez créer, dans la portée actuelle, une référence de type ou une référence de module pour la classe, l’interface ou le module parent du membre cible. Le jeton de métadonnées pour cette référence est ensuite passé dans l’argument `tkParent`. Vous n’avez pas besoin de créer une référence au parent du membre cible s’il sera résolu ultérieurement par le compilateur ou l’éditeur de liens. En résumé :  
  
- Si le membre cible est un champ ou une méthode, utilisez la méthode [IMetaDataEmit ::D efinetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) ou [IMetaDataEmit ::D efineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) pour créer une référence de type, dans la portée actuelle, pour la classe parente ou l’interface parente du membre.  
  
- Si le membre cible est une variable globale ou une fonction globale (autrement dit, pas un membre d’une classe ou d’une interface), utilisez la méthode [IMetaDataEmit ::D efinemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) pour créer une référence de module, dans la portée actuelle, pour le module parent du membre.  
  
- Si le parent du membre cible sera résolu ultérieurement par le compilateur ou l’éditeur de liens, transmettez `mdTokenNil` dans `tkParent`. Le seul scénario dans lequel cela s’applique est lorsqu’une fonction globale ou une variable globale est importée à partir d’un fichier. obj qui sera finalement lié dans le module actuel et les métadonnées fusionnées.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
