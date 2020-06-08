---
title: IMetaDataImport2::GetMethodSpecProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetMethodSpecProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetMethodSpecProps
helpviewer_keywords:
- GetMethodSpecProps method [.NET Framework metadata]
- IMetaDataImport2::GetMethodSpecProps method [.NET Framework metadata]
ms.assetid: 9544b711-e669-4eaf-8630-ee862e5e4489
topic_type:
- apiref
ms.openlocfilehash: 079d9245526ff7914d1cbd6a91f0f2d96a690af5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490443"
---
# <a name="imetadataimport2getmethodspecprops-method"></a>IMetaDataImport2::GetMethodSpecProps, méthode
Obtient la signature de métadonnées de la méthode référencée par le jeton MethodSpec spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,
   [out] ULONG            *pcbSigBlob  
);
```  
  
## <a name="parameters"></a>Paramètres  
 `mi`  
 dans Jeton MethodSpec qui représente l’instanciation de la méthode.  
  
 `tkParent`  
 à Pointeur vers le jeton MethodDef ou MethodRef qui représente la définition de méthode.  
  
 `ppvSigBlob`  
 à Pointeur vers la signature de métadonnées binaires de la méthode.  
  
 `pcbSigBlob`  
 à Taille, en octets, de `ppvSigBlob` .  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport2, interface](imetadataimport2-interface.md)
- [IMetaDataImport, interface](imetadataimport-interface.md)
