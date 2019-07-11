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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 341972629e18213536919fe53bfae94613b4d6e9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777646"
---
# <a name="imetadataemitdefineimportmember-method"></a>IMetaDataEmit::DefineImportMember, méthode
Crée une référence au membre spécifié d’un type ou un module qui est défini en dehors de la portée actuelle et définit un jeton pour cette référence.  
  
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
 [in] Un [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface qui représente l’assembly à partir duquel le membre cible est importé.  
  
 `pbHashValue`  
 [in] Un tableau qui contient le hachage pour l’assembly spécifié par `pAssemImport`.  
  
 `cbHashValue`  
 [in] Nombre d'octets dans le tableau `pbHashValue`.  
  
 `pImport`  
 [in] Un [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface qui représente la portée des métadonnées à partir duquel le membre cible est importé.  
  
 `mbMember`  
 [in] Le jeton de métadonnées qui spécifie le membre cible. Le jeton peut être un `mdMethodDef` (pour une méthode membre), `mdProperty` (pour une propriété de membre) ou `mdFieldDef` (pour un champ de membre) jeton.  
  
 `pAssemEmit`  
 [in] Un [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface qui représente l’assembly dans lequel le membre cible est importé.  
  
 `tkParent`  
 [in] Le `mdTypeRef` ou `mdModuleRef` jeton pour le type ou le module, respectivement, qui possède le membre cible.  
  
 `pmr`  
 [out] Le `mdMemberRef` jeton qui est défini dans la portée actuelle pour la référence de membre.  
  
## <a name="remarks"></a>Notes  
 Le `DefineImportMember` méthode recherche le membre spécifié par `mbMember`, qui est défini dans une autre portée spécifiée par `pImport`et récupère ses propriétés. Il utilise ces informations pour appeler le [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) méthode dans la portée actuelle pour créer la référence de membre.  
  
 En règle générale, avant d’utiliser le `DefineImportMember` (méthode), vous devez créer, dans la portée actuelle, une référence de type ou la référence de module pour le membre cible parent classe, interface ou le module. Le jeton de métadonnées pour cette référence est ensuite passé dans le `tkParent` argument. Vous n’avez pas besoin créer une référence au parent du membre cible si elle doit être résolu ultérieurement par le compilateur ou l’éditeur de liens. Pour récapituler :  
  
- Si le membre cible est un champ ou une méthode, utilisez la [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) ou [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) méthode pour créer une référence de type, dans la portée actuelle, pour le classe parente ou l’interface parente du membre.  
  
- Si le membre cible est une fonction globale ou de variable globale (autrement dit, pas un membre d’une classe ou une interface), utilisez le [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) pour créer une référence de module, dans la portée actuelle, pour le parent du membre (méthode) module.  
  
- Si le parent du membre cible doit être résolu ultérieurement par le compilateur ou l’éditeur de liens, puis passer `mdTokenNil` dans `tkParent`. Le seul scénario dans lequel cela s’applique est lorsqu’une fonction globale ou variable globale est en cours d’importation à partir d’un fichier .obj qui sera finalement lié dans le module actuel, et les métadonnées fusionnées.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
