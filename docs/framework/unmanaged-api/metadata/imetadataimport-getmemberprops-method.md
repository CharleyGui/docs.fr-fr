---
title: IMetaDataImport::GetMemberProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type:
- apiref
ms.openlocfilehash: 72e14ea0414ebdeb8f54a4bdef8ce5208fc8ef72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177231"
---
# <a name="imetadataimportgetmemberprops-method"></a>IMetaDataImport::GetMemberProps, méthode
Obtient les informations stockées dans les métadonnées pour une définition spécifiée du <xref:System.Type> membre, y compris le nom, la signature binaire et l’adresse virtuelle relative, du membre référencé par le jeton spécifié des métadonnées. Il s’agit d’une méthode d’aide simple: si *mb* est un MethodDef, puis **GetMethodProps** est appelé; si *mb* est un FieldDef, alors **GetFieldProps** est appelé. Voir ces autres méthodes pour plus de détails.
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMemberProps (  
   [in]  mdToken           mb,
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szMember,
   [in]  ULONG             cchMember,
   [out] ULONG             *pchMember,
   [out] DWORD             *pdwAttr,  
   [out] PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pcbSigBlob,
   [out] ULONG             *pulCodeRVA,
   [out] DWORD             *pdwImplFlags,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `mb`  
 [dans] Le jeton qui fait référence au membre pour obtenir les métadonnées associées pour.  
  
 `pClass`  
 [out] Un pointeur vers le jeton des métadonnées qui représente la classe du membre.  
  
 `szMember`  
 [out] Le nom du membre.  
  
 `cchMember`  
 [dans] La taille en caractères larges du `szMember` tampon.  
  
 `pchMember`  
 [out] La taille dans les caractères larges du nom retourné.  
  
 `pdwAttr`  
 [out] Toutes les valeurs du drapeau s’appliquaient au membre.  
  
 `ppvSigBlob`  
 [out] Un pointeur à la signature binaire métadonnées du membre.  
  
 `pcbSigBlob`  
 [out] La taille dans `ppvSigBlob`les octets de .  
  
 `pulCodeRVA`  
 [out] Un pointeur à l’adresse virtuelle relative du membre.  
  
 `pdwImplFlags`  
 [out] Tous les indicateurs de mise en œuvre de méthode associés au membre.  
  
 `pdwCPlusTypeFlag`  
 [out] Un drapeau qui <xref:System.ValueType>marque un . C’est l’une des `ELEMENT_TYPE_*` valeurs.
  
 `ppValue`  
 [out] Une valeur de chaîne constante retournée par ce membre.  
  
 `pcchValue`  
 [out] La taille dans `ppValue`les caractères de , ou zéro si `ppValue` ne tient pas une chaîne.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
