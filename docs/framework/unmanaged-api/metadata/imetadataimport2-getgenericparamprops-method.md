---
title: IMetaDataImport2::GetGenericParamProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
ms.openlocfilehash: 7e97b2d4ad1fec4675d1484959b115a4d4b87e90
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490612"
---
# <a name="imetadataimport2getgenericparamprops-method"></a>IMetaDataImport2::GetGenericParamProps, méthode
Obtient les métadonnées associées au paramètre générique représenté par le jeton spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `gp`  
 dans Jeton qui représente le paramètre générique pour lequel retourner des métadonnées.  
  
 `pulParamSeq`  
 à Position ordinale du `Type` paramètre dans le constructeur parent ou la méthode.  
  
 `pdwParamFlags`  
 à Valeur de l’énumération [CorGenericParamAttr,](corgenericparamattr-enumeration.md) qui décrit le `Type` pour le paramètre générique.  
  
 `ptOwner`  
 à Jeton TypeDef ou MethodDef qui représente le propriétaire du paramètre.  
  
 `reserved`  
 à Réservé pour une future extensibilité.  
  
 `wzName`  
 à Nom du paramètre générique.  
  
 `cchName`  
 dans Taille de la `wzName` mémoire tampon.  
  
 `pchName`  
 à Taille retournée du nom, en caractères larges.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport2, interface](imetadataimport2-interface.md)
- [IMetaDataImport, interface](imetadataimport-interface.md)
