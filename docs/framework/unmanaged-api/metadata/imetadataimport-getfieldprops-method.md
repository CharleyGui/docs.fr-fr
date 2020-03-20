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
ms.openlocfilehash: 8c3f98a124dbbcae3b0500932a2357ed1757951f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177246"
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
 [dans] Un jeton FieldDef qui représente le champ pour obtenir des métadonnées associées pour.  
  
 `pClass`  
 [out] Un pointeur à un jeton TypeDef qui représente le type de la classe que le champ appartient à.  
  
 `szField`  
 [out] Le nom du champ.  
  
 `cchField`  
 [dans] La taille en caractères larges de la mémoire tampon pour *szField*.  
  
 `pchField`  
 [out] La taille réelle du tampon retourné.  
  
 `pdwAttr`  
 [out] Drapeaux associés aux métadonnées du terrain.  
  
 `ppvSigBlob`  
 [dans] Un pointeur à la valeur des métadonnées binaires qui décrit le champ.  
  
 `pcbSigBlob`  
 [out] La taille dans `ppvSigBlob`les octets de .  
  
 `pdwCPlusTypeFlag`  
 [out] Un drapeau qui spécifie le type de valeur du champ.  
  
 `ppValue`  
 [out] Une valeur constante pour le terrain.  
  
 `pcchValue`  
 [out] La taille en `ppValue`chars de , ou zéro si aucune chaîne n’existe.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
