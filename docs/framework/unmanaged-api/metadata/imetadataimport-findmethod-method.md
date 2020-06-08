---
title: IMetaDataImport::FindMethod, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type:
- apiref
ms.openlocfilehash: c2ec907759a25048444ebcc81bf5bb0fd23ced58
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503651"
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod, méthode
Obtient un pointeur vers le jeton MethodDef pour la méthode qui est incluse dans le spécifié <xref:System.Type> et qui a le nom et la signature de métadonnées spécifiés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `td`  
 dans `mdTypeDef`Jeton pour le type (une classe ou une interface) qui englobe le membre à rechercher. Si cette valeur est `mdTokenNil` , la recherche est effectuée pour une fonction globale.  
  
 `szName`  
 dans Nom de la méthode à rechercher.  
  
 `pvSigBlob`  
 dans Pointeur vers la signature de métadonnées binaires de la méthode.  
  
 `cbSigBlob`  
 dans Taille en octets de `pvSigBlob` .  
  
 `pmb`  
 à Pointeur vers le jeton MethodDef correspondant.  
  
## <a name="remarks"></a>Remarques  
 Vous spécifiez la méthode à l’aide de sa classe englobante ou de son interface ( `td` ), son nom ( `szName` ) et éventuellement sa signature ( `pvSigBlob` ). Il peut y avoir plusieurs méthodes portant le même nom dans une classe ou une interface. Dans ce cas, transmettez la signature de la méthode pour rechercher la correspondance unique.  
  
 La signature transmise à `FindMethod` doit avoir été générée dans l’étendue actuelle, car les signatures sont liées à une portée particulière. Une signature peut incorporer un jeton qui identifie la classe englobante ou le type valeur. Le jeton est un index dans la table TypeDef locale. Vous ne pouvez pas générer de signature au moment de l’exécution en dehors du contexte de la portée actuelle et utiliser cette signature comme entrée pour l’entrée dans `FindMethod` .  
  
 `FindMethod`recherche uniquement les méthodes qui ont été définies directement dans la classe ou l’interface ; il ne trouve pas les méthodes héritées.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Reflection.MethodInfo>
- [IMetaDataImport, interface](imetadataimport-interface.md)
- [IMetaDataImport2, interface](imetadataimport2-interface.md)
