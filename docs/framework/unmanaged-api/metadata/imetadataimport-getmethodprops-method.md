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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 27b2867019085bf5b44f2ee364c07af66144d4b5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782331"
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
 [in] Le jeton MethodDef qui représente la méthode pour retourner les métadonnées.  
  
 `pClass`  
 [out] Pointeur vers un jeton TypeDef qui représente le type qui implémente la méthode.  
  
 `szMethod`  
 [out] Pointeur vers une mémoire tampon qui a le nom de méthode.  
  
 `cchMethod`  
 [in] La taille demandée de `szMethod`.  
  
 `pchMethod`  
 [out] Un pointeur vers la taille en caractères larges de `szMethod`, ou dans le cas de troncation, le nombre réel de caractères étendus dans le nom de la méthode.  
  
 `pdwAttr`  
 [out] Pointeur vers les indicateurs associés à la méthode.  
  
 `ppvSigBlob`  
 [out] Pointeur vers la signature de métadonnées binaires de la méthode.  
  
 `pcbSigBlob`  
 [out] Un pointeur vers la taille en octets de `ppvSigBlob`.  
  
 `pulCodeRVA`  
 [out] Pointeur vers l’adresse virtuelle relative de la méthode.  
  
 `pdwImplFlags`  
 [out] Pointeur vers les indicateurs d’implémentation de la méthode.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
