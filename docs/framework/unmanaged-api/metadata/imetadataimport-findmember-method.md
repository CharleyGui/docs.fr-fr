---
title: IMetaDataImport::FindMember, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMember
helpviewer_keywords:
- IMetaDataImport::FindMember method [.NET Framework metadata]
- FindMember method [.NET Framework metadata]
ms.assetid: ad32fb84-c2b6-41cd-888d-787ff3a90449
topic_type:
- apiref
ms.openlocfilehash: dab155b82d87609b3d3f390133e6490502a43518
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177282"
---
# <a name="imetadataimportfindmember-method"></a>IMetaDataImport::FindMember, méthode
Obtient un pointeur sur le jeton MemberDef pour le <xref:System.Type> champ ou la méthode qui est inclus par le spécifié et qui a le nom spécifié et la signature des métadonnées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,
   [in]  PCCOR_SIGNATURE   pvSigBlob,
   [in]  ULONG             cbSigBlob,
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `td`  
 [dans] Le jeton TypeDef pour la classe ou l’interface qui entoure le membre à rechercher. Si cette `mdTokenNil`valeur est, la recherche est faite pour une variable globale ou fonction globale.  
  
 `szName`  
 [dans] Le nom du membre à rechercher.  
  
 `pvSigBlob`  
 [dans] Un pointeur à la signature binaire métadonnées du membre.  
  
 `cbSigBlob`  
 [dans] La taille dans `pvSigBlob`les octets de .  
  
 `pmb`  
 [out] Un pointeur pour le jeton MemberDef correspondant.  
  
## <a name="remarks"></a>Notes   
 Vous spécifiez le membre`td`en utilisant`szName`sa classe ou son`pvSigBlob`interface d’enceinte ( ), son nom ( ), et en option sa signature (). Il peut y avoir plusieurs membres avec le même nom dans une classe ou une interface. Dans ce cas, passez la signature du membre pour trouver le match unique.  
  
 La signature `FindMember` transmise doit avoir été générée dans la portée actuelle, parce que les signatures sont liées à une portée particulière. Une signature peut intégrer un jeton qui identifie la classe d’enceinte ou le type de valeur. Le jeton est un index dans le tableau local TypeDef. Vous ne pouvez pas construire une signature en temps d’exécution en `FindMember`dehors du contexte de la portée actuelle et utiliser cette signature comme entrée pour entrer à .  
  
 `FindMember`ne trouve que les membres qui ont été définis directement dans la classe ou l’interface; il ne trouve pas de membres hérités.  
  
> [!NOTE]
> `FindMember`est une méthode d’aide. Il appelle [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); si cet appel ne trouve `FindMember` pas de correspondance, appelle [alors IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
