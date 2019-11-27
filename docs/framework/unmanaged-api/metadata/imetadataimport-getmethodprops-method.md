---
title: IMetaDataImport::GetMethodProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type:
- apiref
ms.openlocfilehash: 4a258ce9121a287929ca5bc39c480f1ca2596e78
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437462"
---
# <a name="imetadataimportgetmethodprops-method"></a>IMetaDataImport::GetMethodProps, méthode
Obtient les métadonnées associées à la méthode référencée par le jeton MethodDef spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMethodProps (  
    [in]  mdMethodDef         mb,  
    [out] mdTypeDef           *pClass,  
    [out] LPWSTR              szMethod,  
    [in]  ULONG               cchMethod,  
    [out] ULONG               *pchMethod,  
    [out] DWORD               *pdwAttr,  
    [out] PCCOR_SIGNATURE     *ppvSigBlob,  
    [out] ULONG               *pcbSigBlob,  
    [out] ULONG               *pulCodeRVA,  
    [out] DWORD               *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `mb`  
 dans Jeton MethodDef qui représente la méthode pour laquelle retourner des métadonnées.  
  
 `pClass`  
 à Pointeur vers un jeton TypeDef qui représente le type qui implémente la méthode.  
  
 `szMethod`  
 à Pointeur vers une mémoire tampon qui a le nom de la méthode.  
  
 `cchMethod`  
 dans Taille de `szMethod`demandée.  
  
 `pchMethod`  
 à Pointeur vers la taille en caractères larges de `szMethod`, ou dans le cas d’une troncation, le nombre réel de caractères larges dans le nom de la méthode.  
  
 `pdwAttr`  
 à Pointeur vers tous les indicateurs associés à la méthode.  
  
 `ppvSigBlob`  
 à Pointeur vers la signature de métadonnées binaires de la méthode.  
  
 `pcbSigBlob`  
 à Pointeur vers la taille en octets de `ppvSigBlob`.  
  
 `pulCodeRVA`  
 à Pointeur vers l’adresse virtuelle relative de la méthode.  
  
 `pdwImplFlags`  
 à Pointeur vers tous les indicateurs d’implémentation de la méthode.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
