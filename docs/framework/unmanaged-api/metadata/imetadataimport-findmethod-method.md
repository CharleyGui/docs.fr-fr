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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4225794740b7786c6f758c9a0953d323c31a1081
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782491"
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod, méthode
Obtient un pointeur vers le MethodDef jeton pour la méthode qui est comprise par le <xref:System.Type> et qui a la signature de nom et de métadonnées spécifiée.  
  
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
 [in] Le `mdTypeDef` jeton pour le type (classe ou interface) qui encadre le membre à rechercher. Si cette valeur est `mdTokenNil`, puis la recherche est effectuée pour une fonction globale.  
  
 `szName`  
 [in] Le nom de la méthode à rechercher.  
  
 `pvSigBlob`  
 [in] Pointeur vers la signature de métadonnées binaires de la méthode.  
  
 `cbSigBlob`  
 [in] La taille en octets de `pvSigBlob`.  
  
 `pmb`  
 [out] Pointeur vers le jeton MethodDef correspondant.  
  
## <a name="remarks"></a>Notes  
 Vous spécifiez la méthode à l’aide de son interface ou la classe englobante (`td`), son nom (`szName`) et éventuellement sa signature (`pvSigBlob`). Il existe peut-être plusieurs méthodes portant le même nom dans une classe ou interface. Dans ce cas, passez signature de la méthode pour rechercher la correspondance unique.  
  
 La signature est passé à `FindMethod` doit avoir été générée dans la portée actuelle, car les signatures sont liées à une étendue spécifique. Une signature peut incorporer un jeton qui identifie le type de valeur ou de la classe englobant. Le jeton est un index dans la table TypeDef local. Vous ne pouvez pas générer une signature d’exécution en dehors du contexte de la portée actuelle et utiliser cette signature comme entrée `FindMethod`.  
  
 `FindMethod` recherche uniquement les méthodes qui ont été définis directement dans la classe ou interface ; Il ne trouve pas de méthodes héritées.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Reflection.MethodInfo>
- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
