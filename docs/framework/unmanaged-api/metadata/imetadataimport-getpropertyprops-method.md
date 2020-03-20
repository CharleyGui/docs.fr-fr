---
title: IMetaDataImport::GetPropertyProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type:
- apiref
ms.openlocfilehash: 5fc71bf240b89afadbf8f2ba10906322921bdda2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175328"
---
# <a name="imetadataimportgetpropertyprops-method"></a>IMetaDataImport::GetPropertyProps, méthode
Obtient les métadonnées pour la propriété représentée par le jeton spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,
   [out] LPCWSTR           szProperty,
   [in]  ULONG             cchProperty,
   [out] ULONG             *pchProperty,
   [out] DWORD             *pdwPropFlags,
   [out] PCCOR_SIGNATURE   *ppvSig,
   [out] ULONG             *pbSig,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,
   [out] mdMethodDef       *pmdGetter,
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,
   [out] ULONG             *pcOtherMethod
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `prop`  
 [dans] Un jeton qui représente la propriété pour retourner les métadonnées.  
  
 `pClass`  
 [out] Un pointeur sur le jeton TypeDef qui représente le type qui implémente la propriété.  
  
 `szProperty`  
 [out] Un tampon pour tenir le nom de la propriété.  
  
 `cchProperty`  
 [dans] La taille en `szProperty`caractères larges de .  
  
 `pchProperty`  
 [out] Le nombre de personnages `szProperty`larges retournés dans .  
  
 `pdwPropFlags`  
 [out] Un pointeur à tous les drapeaux d’attribut appliqués à la propriété. Cette valeur est un peumask de l’énumération [CorPropertyAttr.](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md)  
  
 `ppvSig`  
 [out] Un pointeur à la signature des métadonnées de la propriété.  
  
 `pbSig`  
 [out] Le nombre d’octets retournés dans `ppvSig`.  
  
 `pdwCPlusTypeFlag`  
 [out] Un drapeau spécifiant le type de la constante qui est la valeur par défaut de la propriété. Cette valeur provient de l’énumération De CorElementType.  
  
 `ppDefaultValue`  
 [out] Un pointeur aux octets qui stockent la valeur par défaut pour cette propriété.  
  
 `pcchDefaultValue`  
 [out] La taille en `ppDefaultValue`caractères `pdwCPlusTypeFlag` larges de , si est ELEMENT_TYPE_STRING; autrement, cette valeur n’est pas pertinente. Dans ce cas, `ppDefaultValue` la durée de la durée est `pdwCPlusTypeFlag`déduite du type spécifié par .  
  
 `pmdSetter`  
 [out] Un pointeur pour le jeton MethodDef qui représente la méthode d’accesseur défini pour la propriété.  
  
 `pmdGetter`  
 [out] Un pointeur pour le jeton MethodDef qui représente la méthode d’accès pour la propriété.  
  
 `rmdOtherMethod`  
 [out] Un tableau de jetons MethodDef qui représentent d’autres méthodes associées à la propriété.  
  
 `cMax`  
 [in] Taille maximale du tableau `rmdOtherMethod`. Si vous ne fournissez pas un tableau assez grand pour contenir toutes les méthodes, ils sont ignorés sans avertissement.  
  
 `pcOtherMethod`  
 [out] Le nombre de jetons MethodDef retournés dans `rmdOtherMethod`.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
