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
ms.openlocfilehash: fce4f3875fbdb110134d6b7f684eff40821f6bdd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503677"
---
# <a name="imetadataimportfindmember-method"></a>IMetaDataImport::FindMember, méthode
Obtient un pointeur vers le jeton MemberDef pour le champ ou la méthode qui est inclus dans le spécifié <xref:System.Type> et qui a le nom et la signature de métadonnées spécifiés.  
  
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
 dans Jeton TypeDef pour la classe ou l’interface qui englobe le membre à rechercher. Si cette valeur est `mdTokenNil` , la recherche est effectuée pour une variable globale ou une fonction globale.  
  
 `szName`  
 dans Nom du membre à rechercher.  
  
 `pvSigBlob`  
 dans Pointeur vers la signature de métadonnées binaires du membre.  
  
 `cbSigBlob`  
 dans Taille en octets de `pvSigBlob` .  
  
 `pmb`  
 à Pointeur vers le jeton MemberDef correspondant.  
  
## <a name="remarks"></a>Remarques  
 Vous spécifiez le membre à l’aide de sa classe englobante ou de son interface ( `td` ), son nom ( `szName` ) et éventuellement sa signature ( `pvSigBlob` ). Il peut y avoir plusieurs membres portant le même nom dans une classe ou une interface. Dans ce cas, transmettez la signature du membre pour trouver la correspondance unique.  
  
 La signature transmise à `FindMember` doit avoir été générée dans l’étendue actuelle, car les signatures sont liées à une portée particulière. Une signature peut incorporer un jeton qui identifie la classe englobante ou le type valeur. Le jeton est un index dans la table TypeDef locale. Vous ne pouvez pas générer de signature au moment de l’exécution en dehors du contexte de la portée actuelle et utiliser cette signature comme entrée pour l’entrée dans `FindMember` .  
  
 `FindMember`recherche uniquement les membres qui ont été définis directement dans la classe ou l’interface ; il ne trouve pas les membres hérités.  
  
> [!NOTE]
> `FindMember`est une méthode d’assistance. Il appelle [IMetaDataImport :: FindMethod,](imetadataimport-findmethod-method.md); Si cet appel ne trouve pas de correspondance, `FindMember` appelle [IMetaDataImport :: FindField,](imetadataimport-findfield-method.md).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](imetadataimport-interface.md)
- [IMetaDataImport2, interface](imetadataimport2-interface.md)
