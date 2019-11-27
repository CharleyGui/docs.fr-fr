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
ms.openlocfilehash: 247a2793bf3806f5ee38585d50b4535820dfcb69
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437060"
---
# <a name="imetadataimportgetpropertyprops-method"></a>IMetaDataImport::GetPropertyProps, méthode
Obtient les métadonnées de la propriété représentée par le jeton spécifié.  
  
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
 dans Jeton qui représente la propriété dont les métadonnées doivent être retournées.  
  
 `pClass`  
 à Pointeur vers le jeton TypeDef qui représente le type qui implémente la propriété.  
  
 `szProperty`  
 à Mémoire tampon destinée à contenir le nom de la propriété.  
  
 `cchProperty`  
 dans Taille en caractères larges de `szProperty`.  
  
 `pchProperty`  
 à Nombre de caractères larges retournés dans `szProperty`.  
  
 `pdwPropFlags`  
 à Pointeur vers tous les indicateurs d’attribut appliqués à la propriété. Cette valeur est un masque de masque de l’énumération [CorPropertyAttr,](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) .  
  
 `ppvSig`  
 à Pointeur vers la signature de métadonnées de la propriété.  
  
 `pbSig`  
 à Nombre d’octets retournés dans `ppvSig`.  
  
 `pdwCPlusTypeFlag`  
 à Indicateur spécifiant le type de la constante qui est la valeur par défaut de la propriété. Cette valeur provient de l’énumération CorElementType.  
  
 `ppDefaultValue`  
 à Pointeur vers les octets qui stockent la valeur par défaut de cette propriété.  
  
 `pcchDefaultValue`  
 à Taille en caractères larges de `ppDefaultValue`, si `pdwCPlusTypeFlag` est ELEMENT_TYPE_STRING ; dans le cas contraire, cette valeur n’est pas pertinente. Dans ce cas, la longueur de `ppDefaultValue` est déduite du type spécifié par `pdwCPlusTypeFlag`.  
  
 `pmdSetter`  
 à Pointeur vers le jeton MethodDef qui représente la méthode d’accesseur Set pour la propriété.  
  
 `pmdGetter`  
 à Pointeur vers le jeton MethodDef qui représente la méthode d’accesseur get pour la propriété.  
  
 `rmdOtherMethod`  
 à Tableau de jetons MethodDef qui représentent d’autres méthodes associées à la propriété.  
  
 `cMax`  
 [in] Taille maximale du tableau `rmdOtherMethod`. Si vous ne fournissez pas un tableau suffisamment grand pour contenir toutes les méthodes, elles sont ignorées sans avertissement.  
  
 `pcOtherMethod`  
 à Nombre de jetons MethodDef retournés dans `rmdOtherMethod`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
