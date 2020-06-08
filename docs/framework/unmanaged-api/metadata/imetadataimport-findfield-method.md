---
title: IMetaDataImport::FindField, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type:
- apiref
ms.openlocfilehash: 11ea6e468909ea42e38bdc7b76c60c460c98025e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503664"
---
# <a name="imetadataimportfindfield-method"></a>IMetaDataImport::FindField, méthode
Obtient un pointeur vers le jeton FieldDef pour le champ qui est entouré par le spécifié <xref:System.Type> et qui a le nom et la signature de métadonnées spécifiés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `td`  
 dans Jeton TypeDef pour la classe ou l’interface qui englobe le champ à rechercher. Si cette valeur est `mdTokenNil` , la recherche est effectuée pour une variable globale.  
  
 `szName`  
 dans Nom du champ à rechercher.  
  
 `pvSigBlob`  
 dans Pointeur vers la signature de métadonnées binaires du champ.  
  
 `cbSigBlob`  
 dans Taille en octets de `pvSigBlob` .  
  
 `pmb`  
 à Pointeur vers le jeton FieldDef correspondant.  
  
## <a name="remarks"></a>Remarques  
 Vous spécifiez le champ à l’aide de sa classe englobante ou de son interface ( `td` ), son nom ( `szName` ) et éventuellement sa signature ( `pvSigBlob` ).  
  
 La signature transmise à `FindField` doit avoir été générée dans l’étendue actuelle, car les signatures sont liées à une portée particulière. Une signature peut incorporer un jeton qui identifie la classe englobante ou le type valeur. (Le jeton est un index dans la table TypeDef locale). Vous ne pouvez pas générer une signature au moment de l’exécution en dehors du contexte de la portée actuelle et utiliser cette signature comme entrée pour `FindField` .  
  
 `FindField`recherche uniquement les champs qui ont été définis directement dans la classe ou l’interface ; il ne trouve pas les champs hérités.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](imetadataimport-interface.md)
- [IMetaDataImport2, interface](imetadataimport2-interface.md)
