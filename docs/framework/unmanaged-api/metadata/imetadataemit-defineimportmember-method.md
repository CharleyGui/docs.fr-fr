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
ms.openlocfilehash: ec8a24251ac4f0701b1adab19829078270229ced
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004593"
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
 dans Interface [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) qui représente l’assembly à partir duquel le membre cible est importé.  
  
 `pbHashValue`  
 dans Tableau qui contient le hachage de l’assembly spécifié par `pAssemImport` .  
  
 `cbHashValue`  
 [in] Nombre d'octets dans le tableau `pbHashValue`.  
  
 `pImport`  
 dans Interface [IMetaDataImport](imetadataimport-interface.md) qui représente la portée des métadonnées à partir de laquelle le membre cible est importé.  
  
 `mbMember`  
 dans Jeton de métadonnées qui spécifie le membre cible. Le jeton peut être un `mdMethodDef` jeton (pour une méthode membre), `mdProperty` (pour une propriété de membre) ou `mdFieldDef` (pour un champ de membre).  
  
 `pAssemEmit`  
 dans Interface [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) qui représente l’assembly dans lequel le membre cible est importé.  
  
 `tkParent`  
 dans `mdTypeRef`Jeton ou `mdModuleRef` pour le type ou le module, respectivement, qui possède le membre cible.  
  
 `pmr`  
 à `mdMemberRef`Jeton qui est défini dans la portée actuelle pour la référence de membre.  
  
## <a name="remarks"></a>Remarques  
 La `DefineImportMember` méthode recherche le membre, spécifié par `mbMember` , qui est défini dans une autre portée, spécifiée par `pImport` , et récupère ses propriétés. Elle utilise ces informations pour appeler la méthode [IMetaDataEmit ::D efinememberref](imetadataemit-definememberref-method.md) dans l’étendue actuelle afin de créer la référence de membre.  
  
 En général, avant d’utiliser la `DefineImportMember` méthode, vous devez créer, dans la portée actuelle, une référence de type ou une référence de module pour la classe, l’interface ou le module parent du membre cible. Le jeton de métadonnées pour cette référence est ensuite passé dans l' `tkParent` argument. Vous n’avez pas besoin de créer une référence au parent du membre cible s’il sera résolu ultérieurement par le compilateur ou l’éditeur de liens. Pour résumer :  
  
- Si le membre cible est un champ ou une méthode, utilisez la méthode [IMetaDataEmit ::D efinetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) ou [IMetaDataEmit ::D efineimporttype](imetadataemit-defineimporttype-method.md) pour créer une référence de type, dans la portée actuelle, pour la classe parente ou l’interface parente du membre.  
  
- Si le membre cible est une variable globale ou une fonction globale (autrement dit, pas un membre d’une classe ou d’une interface), utilisez la méthode [IMetaDataEmit ::D efinemoduleref](imetadataemit-definemoduleref-method.md) pour créer une référence de module, dans la portée actuelle, pour le module parent du membre.  
  
- Si le parent du membre cible sera résolu ultérieurement par le compilateur ou l’éditeur de liens, alors transmettez `mdTokenNil` `tkParent` . Le seul scénario dans lequel cela s’applique est lorsqu’une fonction globale ou une variable globale est importée à partir d’un fichier. obj qui sera finalement lié dans le module actuel et les métadonnées fusionnées.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](imetadataemit-interface.md)
- [IMetaDataEmit2, interface](imetadataemit2-interface.md)
