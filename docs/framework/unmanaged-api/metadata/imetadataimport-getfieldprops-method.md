---
title: IMetaDataImport::GetFieldProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type:
- apiref
ms.openlocfilehash: 2bd05b49c3d51ac13865997910c99cc0cd5ca2d9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491242"
---
# <a name="imetadataimportgetfieldprops-method"></a>IMetaDataImport::GetFieldProps, méthode
Obtient les métadonnées associées au champ référencé par le jeton FieldDef spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pcbSigBlob,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `mb`  
 dans Jeton FieldDef qui représente le champ pour lequel obtenir les métadonnées associées.  
  
 `pClass`  
 à Pointeur vers un jeton TypeDef qui représente le type de la classe à laquelle le champ appartient.  
  
 `szField`  
 à Nom du champ.  
  
 `cchField`  
 dans Taille en caractères larges de la mémoire tampon pour *szField*.  
  
 `pchField`  
 à Taille réelle de la mémoire tampon retournée.  
  
 `pdwAttr`  
 à Indicateurs associés aux métadonnées du champ.  
  
 `ppvSigBlob`  
 dans Pointeur vers la valeur de métadonnées binaires qui décrit le champ.  
  
 `pcbSigBlob`  
 à Taille en octets de `ppvSigBlob` .  
  
 `pdwCPlusTypeFlag`  
 à Indicateur qui spécifie le type de valeur du champ.  
  
 `ppValue`  
 à Valeur constante pour le champ.  
  
 `pcchValue`  
 à Taille en caractères de `ppValue` , ou zéro si aucune chaîne n’existe.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](imetadataimport-interface.md)
- [IMetaDataImport2, interface](imetadataimport2-interface.md)
