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
ms.openlocfilehash: 0ba25c981cc389baf06ecca0db543d48ac60317b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711401"
---
# <a name="imetadataimportfindmemberref-method"></a>IMetaDataImport::FindMemberRef, méthode

Obtient un pointeur vers le jeton MemberRef pour la référence de membre qui est incluse dans le spécifié <xref:System.Type> et qui a le nom et la signature de métadonnées spécifiés.  
  
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
 dans Jeton TypeRef pour la classe ou l’interface qui englobe la référence de membre à rechercher. Si cette valeur est `mdTokenNil` , la recherche est effectuée pour une variable globale ou une référence de fonction globale.  
  
 `szName`  
 dans Nom de la référence de membre à rechercher.  
  
 `pvSigBlob`  
 dans Pointeur vers la signature de métadonnées binaires de la référence de membre.  
  
 `cbSigBlob`  
 dans Taille en octets de `pvSigBlob` .  
  
 `pmr`  
 à Pointeur vers le jeton MemberRef correspondant.  
  
## <a name="remarks"></a>Remarques  

 Vous spécifiez le membre à l’aide de sa classe englobante ou de son interface ( `td` ), son nom ( `szName` ) et éventuellement sa signature ( `pvSigBlob` ).  
  
 La signature transmise à `FindMemberRef` doit avoir été générée dans l’étendue actuelle, car les signatures sont liées à une portée particulière. Une signature peut incorporer un jeton qui identifie la classe englobante ou le type valeur. Le jeton est un index dans la table TypeDef locale. Vous ne pouvez pas générer une signature au moment de l’exécution en dehors du contexte de la portée actuelle et utiliser cette signature comme entrée pour `FindMemberRef` .  
  
 `FindMemberRef` recherche uniquement les références de membre qui ont été définies directement dans la classe ou l’interface ; il ne trouve pas les références de membre héritées.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](imetadataimport-interface.md)
- [IMetaDataImport2, interface](imetadataimport2-interface.md)
