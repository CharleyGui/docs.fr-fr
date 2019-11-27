---
title: IMetaDataImport::GetParamProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
ms.openlocfilehash: bb73ccdd9eee4b5a655a56b5d6757e0c6003fbc9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437124"
---
# <a name="imetadataimportgetparamprops-method"></a>IMetaDataImport::GetParamProps, méthode
Obtient les valeurs de métadonnées pour le paramètre référencé par le jeton ParamDef spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `tk`  
 dans Jeton ParamDef qui représente le paramètre pour lequel retourner des métadonnées.  
  
 `pmd`  
 à Pointeur vers un jeton MethodDef représentant la méthode qui prend le paramètre.  
  
 `pulSequence`  
 à Position ordinale du paramètre dans la liste d’arguments de la méthode.  
  
 `szName`  
 à Mémoire tampon destinée à contenir le nom du paramètre.  
  
 `cchName`  
 dans Taille demandée en caractères larges de `szName`.  
  
 `pchName`  
 à Taille retournée en caractères larges de `szName`.  
  
 `pdwAttr`  
 à Pointeur vers tous les indicateurs d’attribut associés au paramètre. Il s’agit d’un masque de ré`CorParamAttr` valeurs.  
  
 `pdwCPlusTypeFlag`  
 à Pointeur vers un indicateur spécifiant que le paramètre est un <xref:System.ValueType>.  
  
 `ppValue`  
 à Pointeur vers une chaîne constante retournée par le paramètre.  
  
 `pcchValue`  
 à Taille de `ppValue` en caractères larges, ou zéro si `ppValue` ne contient pas de chaîne.  
  
## <a name="remarks"></a>Notes

Les valeurs de séquence dans `pulSequence` commencent par 1 pour les paramètres. Une valeur de retour a un numéro de séquence égal à 0.

## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
