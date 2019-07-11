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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e9d2c74adecdfb0201f9f0c08998feba674f9e0f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778923"
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
 [in] Jeton ParamDef qui représente le paramètre pour retourner les métadonnées.  
  
 `pmd`  
 [out] Pointeur vers un jeton MethodDef représentant la méthode qui prend le paramètre.  
  
 `pulSequence`  
 [out] La position ordinale du paramètre dans la liste d’arguments de méthode.  
  
 `szName`  
 [out] Une mémoire tampon pour contenir le nom du paramètre.  
  
 `cchName`  
 [in] La taille demandée en caractères larges de `szName`.  
  
 `pchName`  
 [out] La taille retournée en caractères larges de `szName`.  
  
 `pdwAttr`  
 [out] Pointeur vers les indicateurs d’attribut associé au paramètre. Il s’agit d’un masque de bits de `CorParamAttr` valeurs.  
  
 `pdwCPlusTypeFlag`  
 [out] Un pointeur vers un indicateur spécifiant que le paramètre est un <xref:System.ValueType>.  
  
 `ppValue`  
 [out] Pointeur vers une chaîne constante retournée par le paramètre.  
  
 `pcchValue`  
 [out] La taille de `ppValue` en caractères larges, ou zéro si `ppValue` ne contient pas de chaîne.  
  
## <a name="remarks"></a>Notes

Les valeurs de séquence dans `pulSequence` commencent par 1 pour les paramètres. Une valeur de retour a un numéro de séquence 0.

## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
