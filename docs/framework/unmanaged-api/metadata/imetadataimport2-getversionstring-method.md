---
title: IMetaDataImport2::GetVersionString, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type:
- apiref
ms.openlocfilehash: 84cf5ac9eab5749d3bdc63670fe5c31bfb62abcd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490403"
---
# <a name="imetadataimport2getversionstring-method"></a>IMetaDataImport2::GetVersionString, méthode
Obtient le numéro de version du runtime qui a été utilisé pour générer l’assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pwzBuf`  
 à Tableau pour stocker la chaîne qui spécifie la version.  
  
 `ccBufSize`  
 dans Taille, en caractères larges, du `pwzBuf` tableau.  
  
 `pccBufSize`  
 à Nombre de caractères larges, y compris un terminateur null, retournés dans le `pwzBuf` tableau.  
  
## <a name="remarks"></a>Remarques  
 La `GetVersionString` méthode obtient la version intégrée de la portée de métadonnées actuelle. Si l’étendue n’a jamais été enregistrée, elle n’a pas de version intégrée et une chaîne vide est retournée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport2, interface](imetadataimport2-interface.md)
- [IMetaDataImport, interface](imetadataimport-interface.md)
