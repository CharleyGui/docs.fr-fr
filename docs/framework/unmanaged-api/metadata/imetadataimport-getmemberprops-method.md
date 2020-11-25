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
ms.openlocfilehash: f01d65a339c77e6af3e768c620f17ef0190c1e58
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733216"
---
# <a name="imetadataimportgetmemberprops-method"></a>IMetaDataImport::GetMemberProps, méthode

Obtient les informations stockées dans les métadonnées pour une définition de membre spécifiée, y compris le nom, la signature binaire et l’adresse virtuelle relative, du <xref:System.Type> membre référencé par le jeton de métadonnées spécifié. Il s’agit d’une méthode d’assistance simple : si *Mo* est un MethodDef, **GetMethodProps,** est appelé ; Si *Mo* est un FieldDef, **GetFieldProps,** est appelé. Pour plus d’informations, consultez ces autres méthodes.
  
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
 dans Jeton qui référence le membre pour lequel obtenir les métadonnées associées.  
  
 `pClass`  
 à Pointeur vers le jeton de métadonnées qui représente la classe du membre.  
  
 `szMember`  
 à Nom du membre.  
  
 `cchMember`  
 dans Taille en caractères larges de la `szMember` mémoire tampon.  
  
 `pchMember`  
 à Taille en caractères larges du nom retourné.  
  
 `pdwAttr`  
 à Toutes les valeurs d’indicateur appliquées au membre.  
  
 `ppvSigBlob`  
 à Pointeur vers la signature de métadonnées binaires du membre.  
  
 `pcbSigBlob`  
 à Taille en octets de `ppvSigBlob` .  
  
 `pulCodeRVA`  
 à Pointeur vers l’adresse virtuelle relative du membre.  
  
 `pdwImplFlags`  
 à Indicateurs d’implémentation de méthode associés au membre.  
  
 `pdwCPlusTypeFlag`  
 à Indicateur qui marque un <xref:System.ValueType> . Il s’agit de l’une des `ELEMENT_TYPE_*` valeurs.
  
 `ppValue`  
 à Valeur de chaîne constante retournée par ce membre.  
  
 `pcchValue`  
 à Taille en caractères de `ppValue` , ou zéro si `ppValue` ne contient pas de chaîne.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](imetadataimport-interface.md)
- [IMetaDataImport2, interface](imetadataimport2-interface.md)
