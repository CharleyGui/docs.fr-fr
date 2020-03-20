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
ms.openlocfilehash: a7449ffc8a8ccf2db62ab3cff2f9cfaffd0c72a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175861"
---
# <a name="imetadataemitdefineimportmember-method"></a>IMetaDataEmit::DefineImportMember, méthode
Crée une référence au membre spécifié d’un type ou d’un module qui est défini en dehors de la portée actuelle, et définit un jeton pour cette référence.  
  
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
 [dans] Une interface [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) qui représente l’assemblage à partir duquel le membre cible est importé.  
  
 `pbHashValue`  
 [dans] Un tableau qui contient le hachage pour l’assemblage spécifié par `pAssemImport`.  
  
 `cbHashValue`  
 [in] Nombre d'octets dans le tableau `pbHashValue`.  
  
 `pImport`  
 [dans] Une interface [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) qui représente la portée des métadonnées à partir de laquelle le membre cible est importé.  
  
 `mbMember`  
 [dans] Le jeton des métadonnées qui spécifie le membre cible. Le jeton peut `mdMethodDef` être un jeton (pour une méthode membre), `mdProperty` (pour une propriété membre), ou `mdFieldDef` (pour un champ membre) jeton.  
  
 `pAssemEmit`  
 [dans] Une interface [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) qui représente l’assemblage dans lequel le membre cible est importé.  
  
 `tkParent`  
 [dans] Le `mdTypeRef` `mdModuleRef` ou le jeton pour le type ou le module, respectivement, qui possède le membre cible.  
  
 `pmr`  
 [out] Le `mdMemberRef` jeton qui est défini dans la portée actuelle de la référence du membre.  
  
## <a name="remarks"></a>Notes   
 La `DefineImportMember` méthode recherche le membre, spécifié par `mbMember`, qui `pImport`est défini dans une autre portée, spécifiée par , et récupère ses propriétés. Il utilise ces informations pour appeler la méthode [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) dans la portée actuelle pour créer la référence des membres.  
  
 En général, avant `DefineImportMember` d’utiliser la méthode, vous devez créer, dans la portée actuelle, une référence type ou une référence de module pour la classe, l’interface ou le module parent du membre cible. Le jeton des métadonnées pour `tkParent` cette référence est ensuite adopté dans l’argument. Vous n’avez pas besoin de créer une référence au parent du membre cible si elle sera résolue plus tard par le compilateur ou le lien. Pour résumer :  
  
- Si le membre cible est un champ ou une méthode, utilisez soit la méthode [IMetaDataEmit: :DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) ou la méthode [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) pour créer une référence type, dans la portée actuelle, pour la classe mère du membre ou l’interface parente.  
  
- Si le membre cible est une fonction variable ou globale globale globale (c’est-à-dire non membre d’une classe ou d’une interface), utilisez la méthode [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) pour créer une référence de module, dans la portée actuelle, pour le module parent du membre.  
  
- Si le parent du membre cible sera résolu plus tard par le `mdTokenNil` `tkParent`compilateur ou le lien, puis passez dedans . Le seul scénario dans lequel cela s’applique est quand une fonction globale ou une variable globale est importée à partir d’un fichier .obj qui sera finalement lié dans le module actuel et les métadonnées fusionnées.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
