---
title: IMetaDataAssemblyImport::EnumFiles, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumFiles
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumFiles
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumFiles method [.NET Framework metadata]
- EnumFiles method [.NET Framework metadata]
ms.assetid: f0d721e2-b946-426d-8e20-9124bd04e4cb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b32c402b20f9d7f0d370cfa6ec8376603efa8c3f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777990"
---
# <a name="imetadataassemblyimportenumfiles-method"></a>IMetaDataAssemblyImport::EnumFiles, méthode
Énumère les fichiers référencés dans le manifeste d’assembly actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,   
    [out] mdFile          rFiles[],   
    [in]  ULONG           cMax,   
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `phEnum`  
 [in, out] Pointeur vers l’énumérateur. Cela doit être une valeur null pour le premier appel de cette méthode.  
  
 `rFiles`  
 [out] Tableau utilisé pour stocker le `mdFile` des jetons de métadonnées.  
  
 `cMax`  
 [in] Le nombre maximal de `mdFile` jetons qui peuvent être placés dans `rFiles`.  
  
 `pcTokens`  
 [out] Le nombre de `mdFile` jetons placés dans `rFiles`.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumFiles` retourné avec succès.|  
|`S_FALSE`|Il n’existe pas de jetons à énumérer. Dans ce cas, `pcTokens` est défini à zéro.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
