---
title: IMetaDataImport::FindMemberRef, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
ms.openlocfilehash: d8b8bfd0e70e75c702f32555c10f433a1ff4ae10
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175419"
---
# <a name="imetadataimportfindmemberref-method"></a>IMetaDataImport::FindMemberRef, méthode
Obtient un pointeur vers le jeton MemberRef pour la <xref:System.Type> référence du membre qui est inclus par le spécifié et qui a le nom spécifié et la signature des métadonnées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `td`  
 [dans] Le jeton TypeRef pour la classe ou l’interface qui entoure la référence du membre à la recherche. Si cette `mdTokenNil`valeur est, la recherche est faite pour une variable globale ou une référence fonction globale.  
  
 `szName`  
 [dans] Le nom de la référence du membre à la recherche.  
  
 `pvSigBlob`  
 [dans] Un pointeur à la signature binaire métadonnées de la référence du membre.  
  
 `cbSigBlob`  
 [dans] La taille dans `pvSigBlob`les octets de .  
  
 `pmr`  
 [out] Un pointeur pour le jeton De MemberRef correspondant.  
  
## <a name="remarks"></a>Notes   
 Vous spécifiez le membre`td`en utilisant`szName`sa classe ou son`pvSigBlob`interface d’enceinte ( ), son nom ( ), et en option sa signature ().  
  
 La signature `FindMemberRef` transmise doit avoir été générée dans la portée actuelle, parce que les signatures sont liées à une portée particulière. Une signature peut intégrer un jeton qui identifie la classe d’enceinte ou le type de valeur. Le jeton est un index dans le tableau local TypeDef. Vous ne pouvez pas construire une signature en temps d’exécution `FindMemberRef`en dehors du contexte de la portée actuelle et utiliser cette signature comme entrée à .  
  
 `FindMemberRef`ne trouve que les références des membres qui ont été définies directement dans la classe ou l’interface; il ne trouve pas de références de membres héritées.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
