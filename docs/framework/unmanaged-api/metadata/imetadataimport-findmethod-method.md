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
ms.openlocfilehash: 53b3d94e8b1e273fcbc041d25a5bf586a12735c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177253"
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod, méthode
Obtient un pointeur vers le jeton MethodDef pour <xref:System.Type> la méthode qui est incluse par le spécifié et qui a le nom spécifié et la signature des métadonnées.  
  
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
 [dans] Le `mdTypeDef` jeton pour le type (une classe ou une interface) qui entoure le membre à rechercher. Si cette `mdTokenNil`valeur est, alors la recherche est faite pour une fonction globale.  
  
 `szName`  
 [dans] Le nom de la méthode à rechercher.  
  
 `pvSigBlob`  
 [dans] Un pointeur à la signature de métadonnées binaires de la méthode.  
  
 `cbSigBlob`  
 [dans] La taille dans `pvSigBlob`les octets de .  
  
 `pmb`  
 [out] Un pointeur pour le jeton MethodDef correspondant.  
  
## <a name="remarks"></a>Notes   
 Vous spécifiez la méthode`td`en utilisant`szName`sa classe ou son`pvSigBlob`interface d’enceinte ( ), son nom ( ), et en option sa signature (). Il peut y avoir plusieurs méthodes avec le même nom dans une classe ou une interface. Dans ce cas, passez la signature de la méthode pour trouver le match unique.  
  
 La signature `FindMethod` transmise doit avoir été générée dans la portée actuelle, parce que les signatures sont liées à une portée particulière. Une signature peut intégrer un jeton qui identifie la classe d’enceinte ou le type de valeur. Le jeton est un index dans le tableau local TypeDef. Vous ne pouvez pas construire une signature en temps d’exécution en `FindMethod`dehors du contexte de la portée actuelle et utiliser cette signature comme entrée pour entrer à .  
  
 `FindMethod`ne trouve que des méthodes qui ont été définies directement dans la classe ou l’interface; il ne trouve pas de méthodes héritées.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Reflection.MethodInfo>
- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
