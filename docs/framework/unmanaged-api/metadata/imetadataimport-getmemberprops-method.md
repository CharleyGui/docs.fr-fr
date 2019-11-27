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
ms.openlocfilehash: bc5bbba2fa4a95955e52a2e083a2097178b5d96a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437522"
---
# <a name="imetadataimportgetmemberprops-method"></a>IMetaDataImport::GetMemberProps, méthode
Obtient les informations stockées dans les métadonnées pour une définition de membre spécifiée, y compris le nom, la signature binaire et l’adresse virtuelle relative, du membre <xref:System.Type> référencé par le jeton de métadonnées spécifié. Il s’agit d’une méthode d’assistance simple : si *Mo* est un MethodDef, **GetMethodProps,** est appelé ; Si *Mo* est un FieldDef, **GetFieldProps,** est appelé. Pour plus d’informations, consultez ces autres méthodes. 
  
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
 dans Taille en caractères larges de la mémoire tampon de `szMember`.  
  
 `pchMember`  
 à Taille en caractères larges du nom retourné.  
  
 `pdwAttr`  
 à Toutes les valeurs d’indicateur appliquées au membre.  
  
 `ppvSigBlob`  
 à Pointeur vers la signature de métadonnées binaires du membre.  
  
 `pcbSigBlob`  
 à Taille en octets de `ppvSigBlob`.  
  
 `pulCodeRVA`  
 à Pointeur vers l’adresse virtuelle relative du membre.  
  
 `pdwImplFlags`  
 à Indicateurs d’implémentation de méthode associés au membre.  
  
 `pdwCPlusTypeFlag`  
 à Indicateur qui marque un <xref:System.ValueType>. Il s’agit de l’une des valeurs `ELEMENT_TYPE_*`.
  
 `ppValue`  
 à Valeur de chaîne constante retournée par ce membre.  
  
 `pcchValue`  
 à Taille en caractères de `ppValue`, ou zéro si `ppValue` ne contient pas de chaîne.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
